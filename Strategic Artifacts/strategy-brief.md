---
artifact: strategy-brief
version: 0.2
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
---

# Strategy Brief

## Purpose

Define la dirección estratégica que debe preservarse durante el planning, la ejecución y el review. Este artefacto es la referencia única de qué es Schemaflow, para quién, y por qué.

## Current Understanding

Schemaflow es una capa de governance visual progresiva para builders AI-nativos. El builder usa AI coding tools (Cursor, Lovable, v0, Claude Code) para iterar rápido, pero cada sesión de AI corre sin memoria de las decisiones de diseño anteriores — produciendo drift visual acumulado. Schemaflow escanea el producto real del usuario, extrae su UI kit actual, revela la inconsistencia, le permite definir sus componentes y reglas oficiales, y genera dos tipos de output: prompts de corrección precisos para arreglar el drift de hoy, y un design context file que previene el drift de mañana. El usuario puede re-escanear para verificar que las correcciones funcionaron. El producto es el loop, no el archivo.

## Problem

Los AI coding tools aceleran el desarrollo pero destruyen la consistencia visual de forma acumulativa. Cada sesión de AI genera sin memoria del contexto de diseño anterior: un botón aquí, un card allá, colores que fueron "parecidos" pero no iguales. Después de meses de iteración rápida, el producto del builder parece tres productos distintos. El problema no tiene nombre en las comunidades de builders — los afectados lo describen como "arreglé el hero pero el pricing page sigue raro" o "le di al AI las instrucciones pero lo hizo a su manera." Las soluciones actuales son manuales y frágiles: Notion con los hex codes, screenshots pegados al inicio de cada sesión, preambles largos que el AI ignora o interpreta distinto cada vez.

El problema es urgente *ahora* porque la proliferación de AI coding tools en 2025-2026 convierte algo que antes era un problema ocasional en un problema estructural para cualquier builder que itere con AI.

**Por qué no se resuelve solo:** las herramientas de design system existentes (Tokens Studio, Figma) son para diseñadores y requieren workflow de DesignOps. Los AI coding tools gatan consistencia detrás de Enterprise. Nadie cierra el loop scan → correct → prevent → re-scan para el builder individual.

## Target User / ICP

[Needs Human Review] ICP en estado pre-validado — definición conductual establecida, no validada como persona de compra. → OQ-002

**ICP de entrada (learning ICP):** builders AI-nativos con un producto real en movimiento. Usan Cursor, Lovable, v0, Claude Code, o similares regularmente. Tienen más de una página o componente con inconsistencias observables. Están comenzando a experimentar la governance visual como un costo de tiempo recurrente.

**Señales observables de fit:**
- Usa AI coding tools para iterar el frontend
- Tiene un producto con múltiples páginas o componentes existentes
- Ha corregido manualmente inconsistencias visuales al menos una vez
- Ha usado prompts como "hazlo consistente" o "usa el mismo estilo que el hero"
- No tiene un design system formal ni un equipo de diseño

**Hipótesis de ICP monetizable:** builders con productos serios y monetizables donde la consistencia visual tiene impacto directo en la percepción del producto — freelancers con trabajo de cliente, indie builders con 2+ productos activos, founders preparando lanzamiento o fundraise. → OQ-002

**Trigger de compra:** el usuario alcanza un umbral de costo de tiempo visible — se da cuenta de que está gastando demasiado tiempo arreglando problemas visuales sin poder resolverlos de forma duradera. No es un evento discreto único; es el momento en que el dolor crónico se vuelve lo suficientemente costoso como para buscar una solución. → OQ-001

## Value Proposition

Schemaflow le devuelve al builder el control visual de su producto sin requerir que aprenda diseño ni que abandone su workflow de AI.

El mecanismo: escanea el producto real del usuario → extrae el UI kit existente (colores, tipografías, espaciados, componentes) → detecta drift entre lo que el usuario construyó en distintas sesiones → permite al usuario definir qué es "oficial" en su producto → genera dos outputs:

**(1) Corrección:** prompts precisos con valores exactos ("reemplaza `background: #3B2F8A` con `background: #4F3EAD` en el botón primario de estas páginas") para arreglar el drift detectado hoy. El usuario los ejecuta directamente o los pasa a su AI coding tool.

**(2) Prevención:** un design context file (DESIGN.md / rules file) que el AI del usuario lee en cada sesión futura — preservando las decisiones de diseño sin que el usuario tenga que repetirlas.

El usuario puede re-escanear el producto después de las correcciones para verificar que el loop funcionó. La re-escaneabilidad es la retención.

## Strategic Direction

[Needs Human Review — decision confirmada por founder 2026-06-01] Governance-layer seleccionado como posicionamiento primario (C-02 resuelto). Format-first diferido como estrategia de mercado a largo plazo. Si esta decisión cambia, revisar también: Differentiation, Priorities, North Star en objectives-architecture.

Governance-layer. El producto es el workflow de governance: scan → diagnose → correct → officialize → prevent → re-scan. El design context file es un output del proceso, no el producto en sí. El loop completo — especialmente el re-scan que verifica las correcciones — es el mecanismo de retención.

La estrategia de distribución es PLG: el valor es suficientemente claro en la primera sesión como para generar word-of-mouth, y el design context file embebido crea switching cost natural.

La estandarización del formato (DESIGN.md como estándar open-source) es una estrategia de mercado a largo plazo, no la primera acción comercial. El usuario inicial no compra un estándar — compra el arreglo inmediato de su problema de consistencia.

## Differentiation

[Needs Human Review] Diferenciación actual basada en posición y features — no en moat estructural aún. → OQ-008

**Nota sobre posicionamiento estratégico (D-010, D-002):** La sección de Strategic Direction y esta sección están escritas desde el frame de governance-layer. Este frame fue confirmado por el founder (C-02, resuelto 2026-06-01). Format-first (DESIGN.md como estándar open-source, CLI independiente) queda diferido como estrategia de mercado a largo plazo. Si esta resolución cambia, las secciones de Differentiation, Strategic Direction, Priorities, y objectives-architecture / North Star requieren revisión.

**Nota sobre Backlight (D-008, D-017):** Backlight fue removido de la lista de competidores activos. Cerró el 1 de junio de 2025 (fuente: SchemaFlow Strategy.pdf). Su cierre es una señal de fragilidad del mercado para plays full-platform — no del mercado en sí.

**Posición única:** el cuadrante superior-izquierdo del mapa competitivo (builders AI-nativos + capa de governance) está desocupado. Ningún competidor cierra el loop scan → correct → prevent → re-scan para el builder individual.

**Ventaja específica frente a alternativas:**
- Tokens Studio: 264K usuarios en Figma, pero Figma-locked, requiere DesignOps, no integra con AI coding tools
- getdesign.md: extrae design system de un sitio existente, mismo target user — **el competidor más directo**. No cierra el loop de governance (no detecta drift, no corrige, no re-escanea)
- AI coding tools (Lovable, v0, Bolt): gatan consistencia detrás de Enterprise. El builder individual no tiene acceso
- Superdesign: extrae design system vía screenshots — no persiste, no corrige, no re-escanea
- Workarounds manuales (Notion, screenshots, preambles): sin persistencia, sin detección, sin corrección sistemática

**Diferenciador principal:** Schemaflow es el único tool que cierra el loop completo — y el único cuyo output AI-actionable entrega instrucciones de corrección con valores exactos, no recomendaciones genéricas.

**Riesgo de diferenciación:** los features que diferencian hoy (officialization, output con valores exactos, re-scan loop) son replicables. El moat aspiracional es el switching cost del historial de governance y la ontología de componentes embebida en el workflow del usuario.

## Strategic Principles

Los siguientes principios resuelven trade-offs reales que surgirán durante el desarrollo. Cada uno tiene dientes — puede rechazar una decisión de producto o roadmap.

1. **Lifecycle-aware:** Las decisiones de producto deben corresponder al lifecycle stage del usuario. Un builder en Stage 0 (design partners) y uno en Stage 4 (monetización) tienen necesidades distintas. No optimizar para el segmento equivocado en el momento equivocado.

2. **Exponer complejidad, hacer la acción más rápida:** El producto puede mostrar que el problema es complejo, pero nunca puede hacer que la corrección sea más difícil que hacerlo manualmente. Si arreglar un drift con Schemaflow tarda más que editarlo a mano, el loop falla.

3. **AI-actionability sobre interpretación manual:** Los outputs deben ser ejecutables por un AI coding tool, no solo legibles por humanos. Una recomendación que el usuario tiene que interpretar y luego traducir no es un output válido — es documentación.

4. **Governance sin recrear la pesadez del design system tradicional:** Schemaflow nunca puede requerir que el usuario aprenda terminología de diseño, instale un sistema de tokens, o mantenga una fuente de verdad externa separada. Si el setup requiere más de 15 minutos o conocimiento previo de diseño, el producto falla su propósito.

5. **Observado / inferido / recomendado — siempre distinguibles:** El producto nunca presenta una inferencia como un hecho observado. El usuario debe saber qué vio Schemaflow directamente, qué infirió, y qué está recomendando. La confianza en el diagnóstico es la condición de retención.

6. **Corrección antes que prevención — prevención antes que enforcement:** El orden de valor para el usuario es: (1) arreglar lo que está roto hoy, (2) prevenir que se rompa en el futuro, (3) imponer que el equipo siga las reglas. El producto debe entregar (1) y (2) antes de intentar (3).

7. **El loop de re-scan es la métrica de producto más importante:** Un usuario que completa el loop completo (scan → acción → re-scan) ha validado el valor del producto. Un usuario que escanea una vez no ha validado nada. Las decisiones de producto que aumentan el loop rate son prioritarias sobre las que aumentan los scans iniciales.

## Priorities

Secuencia derivada de la incertidumbre — se valida lo más incierto primero, al menor costo posible.

**Stage 0 (inmediato, pre-roadmap):** Reclutar 5–10 design partners con productos reales, AI-nativos, dispuestos a trabajar iterativamente. Sin design partners no hay roadmap responsable. Esta acción precede a cualquier otra decisión.

**Stage 1 — Validar el governance loop mínimo:** Que un usuario pueda entrar una URL, recibir un UI kit real y un diagnóstico de drift confiable, entender qué acciones tomar, y completar una corrección. El objetivo no es shippe features — es validar que el loop básico funciona y que el usuario *regresa* para un segundo scan.

**Stage 2 — Validar retención:** Que los usuarios que completaron el Stage 1 vuelvan por su propia motivación, no porque se los recordemos.

**Stage 3 — Validar usage economics:** Entender el costo real por scan, la distribución de features usados, y qué comportamientos son precursores del re-scan. Esta información es prerequisito para cualquier decisión de pricing.

**Stage 4 — Monetización:** Solo cuando Stage 3 haya definido el ICP monetizable y el pricing model con datos reales.

## Anti-priorities

Los siguientes items son opciones genuinamente atractivas que se difieren intencionalmente:

- **CLI independiente:** relevante bajo format-first positioning; diferido bajo governance-layer hasta que el loop de producto esté validado
- **GitHub Actions / CI integration:** feature de Enterprise; no construir antes de validar el loop individual
- **Herramienta de colaboración de equipo:** el ICP actual es individual; la colaboración es una expansión posterior
- **Design recommendations / redesign automático:** el producto governa lo que el usuario decidió, no decide por él
- **Marketplaces de componentes o templates:** scope posterior; no construir antes de validar el loop básico
- **Integraciones profundas** (Figma, Storybook, Zeplin): el ICP no usa estas herramientas en su workflow principal
- **Visual testing / screenshot regression:** diferente problema, diferente producto
- **Open-sourcing del formato como primera acción comercial:** diferido; el usuario compra el arreglo, no el estándar

## Success Criteria

**North Star:** Completed Governance Loop Rate — porcentaje de usuarios que completan el loop completo: primer scan → acción de governance → segundo scan que muestra mejora observable.

[Needs Human Review] KR targets por stage son hipótesis iniciales del Objectives Architecture, no commitments. Sin baselines previos. → OQ-006

**Señales de que la estrategia funciona:**
- Usuarios vuelven para un segundo scan después de corregir (sin que se los pidamos)
- Usuarios reportan que sus AI sessions generan menos drift después de usar el design context file
- Design partners referencian Schemaflow cuando hablan del problema con otros builders

**Señales de que algo está mal:**
- Usuarios completan el primer scan pero no toman ninguna acción de corrección
- Usuarios usan el scan como diagnóstico pero prefieren corregir sin los prompts de Schemaflow
- El segundo scan no muestra mejora observable — el output de corrección no fue lo suficientemente preciso

## Open Questions

- OQ-001: ¿Cuál es el trigger específico de compra — qué evento concreto convierte awareness en purchase intent?
- OQ-002: ¿Quién es el primer ICP monetizable — qué sub-segmento muestra WTP antes que los demás?
- OQ-007: ¿Cuál es el TAM/SAM del ICP primario?
- OQ-008: ¿Cómo se defiende el posicionamiento si AI coding tools agregan visual consistency nativamente?
