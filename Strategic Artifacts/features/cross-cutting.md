---
artifact: feature-cross-cutting
version: 0.1
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
technical_reference: Technical Artifacts/features/cross-cutting.md
---

# Feature: Cross-cutting

## What it does

Agrupa los features que aplican de forma transversal a todos los módulos de Schemaflow — autenticación y acceso seguro al sitio, instrumentación de costos de uso, y límites del free tier. Estos no son features de un módulo específico sino restricciones y capacidades que toda la experiencia del producto debe respetar.

## Why it exists

Estas capacidades no pueden vivir dentro de un módulo específico porque afectan a todos. El site access model determina qué pueden ver todos los módulos downstream. La instrumentación de costos informa cualquier decisión de pricing. Los límites del free tier definen la frontera entre exploración y governance real para todos los features.

---

## Sub-feature: Site Access & Credential Handling

### What it does

Gestiona cómo Schemaflow accede al producto del usuario — qué modo de acceso se usa (público, autenticado, local), cómo se manejan las credenciales si son necesarias, y cómo se comunica la transparencia de ese acceso al usuario.

### Why it exists

El site access model es la dependencia más crítica del stack entero. Sin un modelo claro y seguro, Schemaflow no puede escanear productos reales — solo páginas de marketing públicas. Y si el manejo de credenciales no inspira confianza, los usuarios no dan acceso a sus productos reales.

### Where it lives

Configuración del proyecto (`/project/[id]/settings/access`) y flujo de onboarding de nuevo scan.

### How it is composed

**MVP (server-side público):**
- Solo URLs públicas en el MVP
- Comunicación clara al usuario de qué puede y no puede escanear ("El scan funciona en páginas públicas. Para dashboards y áreas privadas, espera el modo autenticado.")
- Sin manejo de credenciales en MVP

**P1 — Authenticated scan:**
- Opción de proveer credenciales de cuenta de prueba para que Schemaflow pueda acceder a áreas privadas
- Mecanismo seguro: instrucciones claras de qué crear (cuenta de prueba, permisos mínimos)
- Comunicación de qué accede Schemaflow, qué no toca, cómo maneja la sesión

**P1 — MCP en servidor:**
- Modo de integración vía MCP para herramientas que lo soporten
- Menor fricción de setup que las credenciales tradicionales

### Who can use it

Todos los usuarios para el scan público. El scan autenticado puede ser feature paid.

### Rules

- Schemaflow siempre solicita el mínimo acceso necesario para el scan — nunca más
- Si solo se necesita escanear páginas públicas, nunca pedir credenciales
- Cada vez que Schemaflow requiere acceso a algo sensible, debe explicar por qué, qué accede, y qué no toca
- Las credenciales del usuario nunca se almacenan más tiempo del necesario para el scan
- El usuario debe poder revocar el acceso en cualquier momento

### What happens when it fails or is empty

- URL requiere login y no hay modo autenticado disponible: error explicativo con CTA para el modo futuro
- Credenciales inválidas: error claro + instrucciones para crear cuenta de prueba correctamente

### Known issues

- OQ-003: Modelo de acceso definitivo no resuelto — dirección confirmada (server-side web + MCP en servidor) pero detalle a definir con design partners

### How it should evolve

- OQ-003: Autenticado vía browser-visible session para users sin acceso a crear cuenta de prueba
- Local/desktop scanner para entornos privados o desarrollo local
- Secure credential vault por proyecto
- Integración OAuth para plataformas que lo soporten

---

## Sub-feature: Usage Cost Instrumentation

### What it does

Trackea internamente el costo de entrega de cada scan, re-scan, export, análisis de AI, y storage — de forma que el equipo de Schemaflow pueda entender el costo por governance loop antes de definir pricing.

### Why it exists

Pricing sin datos de costo es una decisión ciega. El equipo necesita saber cuánto cuesta un scan de 5 páginas vs. 50, cuánto cuesta el análisis de AI por componente, cuánto storage consume el historial de scans. Sin esta información, cualquier modelo de pricing es una apuesta.

### Where it lives

Dashboard interno de Schemaflow (no visible para el usuario en el MVP).

### How it is composed

- Tracking por evento: costo de scan por página, costo de procesamiento de AI por componente, costo de storage por proyecto/scan, costo de generación de export
- Agregación: costo total por governance loop completado (scan → export → re-scan)
- Dashboard interno: costo por usuario, por proyecto, por tipo de scan
- Alertas: si el costo de un scan supera un threshold definido

### Who can use it

Solo el equipo interno de Schemaflow. No visible para el usuario.

### Rules

- La instrumentación debe existir desde el primer scan en producción — no es opcional post-launch
- Los datos de costo deben ser suficientemente granulares para simular diferentes modelos de pricing (por scan, por página, por proyecto, por feature)
- Nunca exponer datos de costo interno a usuarios sin intención explícita

### What happens when it fails or is empty

- Si la instrumentación falla en un scan: el scan continúa, se loguea el error, se recupera manualmente si es posible

### Known issues

- Ninguno

### How it should evolve

- Pricing simulation tool: "si cobramos X por scan, con este costo, el margen es Y"
- Customer-level cost profile: costo acumulado por usuario para identificar outliers
- Usage-based pricing support: facturación basada en scans, páginas, o governance loops

---

## Sub-feature: Free Tier Limits

### What it does

Define qué puede hacer el usuario de forma gratuita y qué requiere upgrade. Los límites deben ser lo suficientemente generosos para que el usuario experimente el governance loop completo, pero lo suficientemente ajustados para que los usuarios con governance real (múltiples proyectos, scans frecuentes, exports persistentes) encuentren un motivo para pagar.

### Why it exists

El free tier es el canal de adquisición y validación del producto. Sin él, el costo de entrada es demasiado alto para el learning ICP. Con él, Schemaflow puede observar cuándo los usuarios llegan a sus límites y qué comportamientos predicen upgrade.

### Where it lives

Aplicado de forma transversal en todos los módulos. La UI de límite aparece en el punto de restricción (ej. "Has alcanzado el límite de 3 scans en el free tier").

### How it is composed

**Posibles dimensiones de límite (a definir según datos de usage economics):**
- Número de URLs por proyecto
- Número de páginas escaneadas por scan
- Número de scans por mes
- Número de re-scans
- Número de exports AI-actionables
- Historial de scans (solo el más reciente en free)
- Scan autenticado (solo paid)
- Número de proyectos (1 en free)
- Acceso a design context library persistente

### Who can use it

Todos los usuarios. Los límites exactos se definen en Stage 3 (usage economics).

### Rules

- El free tier debe permitir experimentar el governance loop al menos una vez completo — scan → governance → export → re-scan
- Los límites no deben cortarse antes del aha moment — el primer scan completo siempre debe ser posible en free
- Los mensajes de límite deben ser claros sobre qué se desbloquea con el upgrade y por qué vale la pena
- Nunca cortar funcionalidad en medio de un flujo crítico — los límites deben activarse antes de iniciar la acción, no a mitad

### What happens when it fails or is empty

- Usuario llega al límite: mensaje claro, explicación de qué desbloquea el upgrade, CTA no agresivo
- Error al verificar límite: dejar pasar con logging del error (no bloquear por un error de sistema)

### Known issues

- OQ-011: Las anti-métricas formales no están definidas — los límites del free tier deben diseñarse para que el usuario que llega a ellos sea un usuario con governance real, no un explorador puntual
- Los límites exactos dependen de OQ-006 (métodos de medición de KRs) y de los datos de Stage 3

### How it should evolve

- Pricing tiers formales con características específicas por tier
- Usage-based pricing como opción
- Team plans (múltiples proyectos, acceso colaborativo)
- Paywalls progresivos basados en engagement (no solo en volumen)
