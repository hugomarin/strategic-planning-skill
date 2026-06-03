---
artifact: product-architecture
version: 0.2
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
---

# Product Architecture

## Purpose

Traducir la estrategia y el entendimiento del usuario en la estructura del producto. Este artefacto define los principios, módulos, flujos críticos, features indispensables, restricciones, dependencias, riesgos, e implicaciones de roadmap que deben guiar el build de Schemaflow.

**Premisa arquitectónica:** Schemaflow no es un UI scanner. Es una capa de governance visual progresiva para el desarrollo asistido por AI — ayuda a los builders a extraer el real UI kit de su producto, entender el drift, definir qué es oficial, generar contexto AI-actionable, y volver a escanear para mantener el control visual en el tiempo.

## Product Principles

Los siguientes principios resuelven trade-offs reales. Cada uno puede rechazar una decisión de producto o roadmap.

1. **Decisiones lifecycle-aware:** Las features de adquisición y las de retención deben juzgarse de forma diferente. Adquisición debe crear claridad rápida y un aha moment fuerte. Retención debe crear governance, corrección, mantenimiento, y scans repetidos. No optimizar para lo mismo en ambas etapas.

2. **Claridad inmediata en adquisición:** La primera experiencia debe mostrar rápidamente algo verdadero y útil sobre el producto del usuario — el real UI kit, drift visible, inconsistencias, y variación inesperada. Si el primer scan no entrega un aha moment en menos de 15 minutos, el loop de adquisición falla.

3. **Governance en retención:** Una vez que el usuario entiende el problema, el producto debe pasar del diagnóstico al control — componentes oficiales, variantes válidas, reglas de corrección, contexto reusable, y loops de governance repetibles.

4. **Exponer complejidad, hacer la acción más rápida:** Schemaflow no debe ocultar drift, estilos duplicados, componentes inconsistentes, o deuda visual para parecer simple. Debe organizar la complejidad de forma que el usuario pueda gobernarla más rápido. La promesa no es hacer que el desorden parezca ordenado — es hacer que el desorden sea gobernable.

5. **AI-actionability sobre interpretación manual:** El usuario no debe tener que traducir manualmente los hallazgos a prompts, instrucciones, o reglas. Schemaflow debe generar contexto accionable para agentes. Dos tipos de output AI-actionable del mismo loop: (a) prompts de corrección con valores exactos para arreglar drift actual, (b) design context file para prevenir drift futuro.

6. **Autoría del usuario sobre enforcement automático:** Schemaflow puede sugerir qué parece oficial o inconsistente, pero el usuario debe preservar la autoría sobre las decisiones de diseño. El producto restaura control, no lo toma.

7. **UI real sobre documentación aspiracional:** El producto comienza desde lo que realmente existe en screens, código, UI renderizada, HTML, y CSS. Brand manuals o design systems declarados pueden ser referencias útiles, pero la UI real es la fuente de verdad para el diagnóstico.

## Core Modules

Ocho módulos que juntos convierten una UI existente en un design system gobernado y AI-actionable.

**1. UI Ingestion Module**
Captura el estado real del producto desde URLs, screens, código, screenshots, repos, páginas renderizadas, o evidencia equivalente del producto.
Responsabilidad: *¿Qué producto estamos analizando, y de dónde viene la evidencia visual?*
No asume que el brand manual o el design system declarado son la verdad. Parte de la UI real.

**2. Real UI Kit Extraction Module**
Extrae los componentes, estilos, tokens, patrones, variantes, y decisiones visuales que realmente existen en el producto.
Responsabilidad: *¿Qué UI kit existe realmente en este producto, aunque nadie lo haya documentado explícitamente?*
Produce el primer valor de adquisición — muestra al usuario algo que probablemente no tiene organizado.

**3. Drift & Consistency Analysis Module**
Detecta inconsistencias, variantes accidentales, duplicación visual, desviaciones entre componentes, y gaps entre el diseño intendido y la implementación real.
Responsabilidad: *¿Dónde se está perdiendo coherencia visual, y qué tan importante es cada desviación?*
No solo dice que existen diferencias — empieza a organizar cuáles importan para la governance del producto.

**4. Governance & Officialization Module**
Permite al usuario definir qué componentes, variantes, estilos, o patrones son oficiales y cuáles deben corregirse, removerse, deprecarse, o consolidarse.
Responsabilidad: *¿Qué partes del sistema visual deben convertirse en fuente de verdad?*
Esencial porque Schemaflow no impone el diseño correcto automáticamente — sugiere, pero preserva la autoría del usuario.

**5. Design Context Module**
Convierte las decisiones visuales en contexto estructurado — reglas de uso, intención de componentes, restricciones, tokens, variantes válidas, patrones permitidos, y criterios de implementación.
Responsabilidad: *¿Cómo organizar el contexto de diseño para que los humanos puedan gestionarlo y los agentes AI puedan entenderlo?*
Aquí Schemaflow se vuelve más que un scanner — no solo detecta, estructura el conocimiento visual del producto.

**6. AI-Actionable Output Module**
Genera los dos tipos de outputs AI-actionables del governance loop:
- *Corrección:* prompts precisos con valores exactos para arreglar el drift detectado — ejecutables directamente o pasables al AI coding tool del usuario.
- *Prevención:* design context file (DESIGN.md / rules file) generado durante la officialization, para prevenir drift en sesiones futuras.
Responsabilidad: *¿Cómo convertir la governance visual en instrucciones que el AI puede ejecutar?*

**7. Correction & Re-scan Loop Module**
Cierra el loop soportando la corrección, el re-scan, la comparación, y la verificación de que la coherencia mejoró.
Responsabilidad: *¿Recuperó el producto el control visual después de que se tomaron acciones?*
Crítico para la retención — convierte a Schemaflow en un workflow recurrente, no en un reporte puntual.

**8. Design Intelligence Module**
Con el tiempo, analiza la lógica de componentes y patrones de uso para sugerir mejoras, consolidar variantes, detectar decisiones de componentes débiles, y construir una ontología de componentes reusable.
Responsabilidad: *¿Cómo puede el design system mejorar, no solo corregirse?*
No parte del MVP más temprano — representa una dirección estratégica más defensible una vez que Schemaflow tiene contexto de componentes y uso estructurado.

**Activación de Phase 3 (features/ children):** con 8 módulos definidos, cada uno con dominio de responsabilidad diferenciado, **Phase 3 se declara requerida.** Los 8 módulos tienen comportamiento suficientemente diferenciado como para justificar feature children individuales. Se ejecutará después de que este artefacto sea confirmado.

## Critical Flows

El flujo crítico de Schemaflow es el loop end-to-end que convierte el primer scan en governance recurrente.

El reto central del producto no es solo producir un scan útil — es convertir ese primer scan en un segundo, tercer, cuarto, y quinto scan. El comportamiento de re-scan es la señal más clara de que Schemaflow se está convirtiendo en un workflow de governance, no en una herramienta de diagnóstico puntual.

**El loop completo:**

1. **URL Intake / Product Entry** — El usuario ingresa las URLs del producto a analizar. Primer momento de adquisición. Si hay demasiada fricción aquí, el usuario no llega al valor.

2. **Scan / Real UI Detection** — Schemaflow escanea las páginas y detecta componentes reales, estilos, patrones, variantes, tokens, y señales visuales. El objetivo es mostrar lo que existe, no lo que el usuario asume que existe.

3. **Real UI Kit Generation** — El producto genera una representación del real UI kit. Primer aha moment: *"Ahora puedo ver el sistema visual que mi producto tiene realmente."*

4. **Problem Understanding / Action Clarity** — El usuario debe entender qué está mal, qué está duplicado, qué drifteó, qué es inconsistente, y qué acción se recomienda. Schemaflow debe evitar ser un reporte abrumador — debe convertir complejidad en acciones claras.

5. **Correction Support** — Schemaflow genera los **prompts de corrección precisos con valores exactos** para arreglar el drift detectado. El usuario no debe tener que traducir el diagnóstico en acción manualmente. Ejemplo: "Reemplaza `background: #3B2F8A` con `background: #4F3EAD` en el botón primario de estas páginas."

6. **Officialization / Maintenance** — Después de la corrección, el producto ayuda a mantener el sistema: componentes oficiales, variantes válidas, reglas de uso. Genera el **design context file** (DESIGN.md / rules file) que el AI del usuario leerá en sesiones futuras.

7. **Re-scan / Governance Loop** — El usuario vuelve para verificar que las correcciones funcionaron y detectar nuevo drift. El segundo scan muestra progreso, reducción de drift, nuevos issues, regresiones, o cambios comparados con el scan anterior.

## Core Features

Features indispensables — sin ellas el producto no puede expresar la tesis central.

1. **URL-based product scan** — Sin esto no hay path de adquisición simple. P0.
2. **Real UI kit extraction** — Sin esto no hay aha moment. P0.
3. **Drift and inconsistency detection** — Sin esto el usuario no ve el problema de governance. P0.
4. **UI kit visualization** — El usuario debe poder ver y confiar en lo que se detectó. P0.
5. **Actionable recommendations** — Sin acción, el producto es solo diagnóstico. P0.
6. **Official / unofficial component decisioning** — Governance requiere autoría humana, no solo inferencia automática. P0.
7. **AI-actionable output — corrección:** prompts de corrección precisos con valores exactos. En la primera versión puede empezar como copyable prompts con los valores exactos de corrección. P0.
8. **Re-scan / comparison** — Sin esto, Schemaflow permanece como herramienta de diagnóstico puntual en lugar de loop de governance. P0.

**AI-actionable output — prevención:** design context file (DESIGN.md / rules file) generado durante officialization. P1 inmediato — no blocking para el primer scan, pero requerido para completar el loop de retención.

**Features no-core para el primer loop:** colaboración avanzada, team workflows, historial sofisticado, gestión multi-proyecto, integraciones profundas (GitHub, Figma, Linear), component marketplaces, recomendaciones avanzadas de diseño, monitoring continuo automático, design intelligence.

## Dependencies

**La cadena de dependencias es estricta:** no se puede gobernar lo que no se puede ver con precisión. No se pueden generar acciones útiles desde un diagnóstico débil. No se puede crear retención sin un re-scan loop.

**La dependencia más importante es el modelo de acceso al sitio.**

| Dependencia | Bloquea |
|---|---|
| Site access model → | calidad de scan y cobertura |
| Acceso autenticado → | casos de uso de productos maduros (dashboards, logged-in states) |
| Extracción HTML/CSS/rendered-state → | generación del real UI kit |
| Calidad de scan → | confianza del usuario en el diagnóstico |
| Extracción del real UI kit → | diagnóstico de drift |
| Análisis de drift → | recomendaciones accionables |
| Officialization → | governance real (fuente de verdad) |
| Design context → | AI-actionable export (prevención) |
| AI-actionable export corrección → | comportamiento de corrección del usuario |
| Comportamiento de corrección → | valor del re-scan |
| Historial de re-scan → | governance en el tiempo |

**Modelo de acceso al sitio — decisión del founder:**

[Needs Human Review] Dirección confirmada: solución web con server-side. En el servidor, posiblemente un MCP montado. El detalle de implementación se define durante Stage 0 con design partners — en particular según si sus productos relevantes viven detrás de login o son suficientemente escaneables desde páginas públicas. → OQ-003

Análisis de opciones:

| Opción | Ventajas | Desventajas |
|---|---|---|
| Server-side | Experiencia simple, buena para adquisición, fácil de escalar | Credenciales más sensibles, dificultad con sitios protegidos, bot detection |
| Browser-visible | Más transparente, mejor para confianza, maneja login con usuario presente | Más fricción, menos "mágico," puede sentirse más técnico |
| Local/desktop | Mejor privacidad, localhost, credenciales menos expuestas | Alta fricción de instalación, peor para adquisición simple |
| Hybrid | Adquisición rápida + cobertura profunda para casos maduros | Múltiples paths, mayor complejidad de arquitectura y UX |

**Recomendación arquitectónica:** modelo hybrid — server-side para adquisición (URLs públicas), con soporte de MCP en el servidor o modo de acceso autenticado para productos con dashboard. Confirmar con design partners cuál es el blocker real.

## Product Constraints

Restricciones duras — romperlas compromete la integridad o la confianza del producto.

1. **Mapear el UI real con cobertura suficiente para preservar la confianza:** Si el producto tiene 7 estilos de botón y Schemaflow solo mapea 2, la confianza se rompe. El producto puede organizar y priorizar hallazgos, pero no puede ocultar omisiones importantes.

2. **Nunca alucinar componentes, estilos, o patrones de uso:** El producto no debe inventar componentes que no existen, variantes no usadas, o patrones no presentes en la UI real. La distinción es siempre obligatoria: **observado / inferido / recomendado.**

3. **Separar hechos observados de interpretación del producto:** La UX debe mostrar claramente qué fue directamente observado y qué está siendo interpretado. Ejemplo: "7 estilos de botón detectados" = hecho observado. "Este parece ser el botón primario oficial" = inferencia. "Recomendamos consolidar estas 3 variantes" = recomendación.

4. **No simplificar ocultando complejidad real:** Schemaflow puede resumir, agrupar, y priorizar, pero no debe distorsionar la realidad para que el producto parezca más simple de lo que es.

5. **Proteger el acceso y las credenciales como capa de confianza de primera clase:** Si el producto necesita acceder a páginas privadas o flujos autenticados, el manejo de credenciales debe tratarse como una preocupación central del producto, no un detalle técnico. El usuario debe poder crear una cuenta de prueba para Schemaflow, proveer credenciales a través de un mecanismo seguro, o confiar en un flujo local/desktop.

6. **Minimizar el acceso sensible siempre que sea posible:** Solicitar el mínimo acceso necesario para realizar el scan. Si una página pública es suficiente, no requerir credenciales.

7. **Nunca producir diagnóstico sin un path accionable:** Mostrar problemas sin decir qué hacer aumenta la ansiedad y el trabajo. Todo hallazgo importante debe ofrecer un siguiente paso — oficializar, consolidar, ignorar, exportar al agente, generar una regla, generar un fix, o marcar para revisión.

8. **Nunca hacer la governance más lenta que la corrección manual:** Si usar Schemaflow tarda más que corregir manualmente en Cursor, Claude, Figma, o código, el producto pierde su razón de existir. Puede exponer complejidad, pero debe reducir el tiempo necesario para decidir y actuar.

## Risks

Los 10 riesgos principales, ordenados por impacto potencial en la tesis:

1. **Scan trust risk:** Schemaflow no mapea la UI real con suficiente cobertura. Mecanismo de falla: detección incompleta → usuario nota estilos/componentes faltantes → diagnóstico pierde credibilidad → usuario no actúa ni vuelve.

2. **Hallucination risk:** Schemaflow inventa componentes, variantes, estilos, o patrones que no existen. Especialmente peligroso porque la autoridad del producto depende de mostrar el estado real de la UI.

3. **Site access and credential risk:** El producto no puede acceder a las partes correctas del producto del usuario de forma segura y cómoda. Si solo escanea URLs públicas, puede perderse la superficie real del producto.

4. **First scan dead-end risk:** El primer scan es interesante pero no lleva a acción. Mecanismo de falla: scan produce reporte → usuario ve problemas → no hay path de acción claro → no hay corrección → no hay segundo scan.

5. **Re-scan failure risk:** El producto no crea una razón fuerte para volver. El segundo scan es la señal crítica de retención. Si los usuarios no vuelven después de corregir, Schemaflow falla como governance layer.

6. **Actionability risk:** El producto detecta drift pero los prompts de corrección no son lo suficientemente precisos como para ser ejecutados directamente. Si el usuario debe interpretar y reescribir las instrucciones, Schemaflow agrega trabajo en lugar de quitarlo.

7. **Overwhelm risk:** El producto muestra la complejidad completa de la UI pero falla en organizarla. Demasiados hallazgos sin jerarquía = el usuario se siente peor, no más en control.

8. **ICP dilution risk:** Posicionamiento demasiado amplio. Los builders muy en etapa temprana usan el free tier pero no pagan. El segmento pagante es más estrecho.

9. **Commodity scanner risk:** El producto es percibido como un UI scanner, no como una governance layer. Si los users lo entienden como "tool que encuentra inconsistencias de UI," puede ser copiado o absorbido por incumbentes. La posición defensible está en el design context, officialization, AI-actionable governance, y re-scan loops.

10. **Native tool absorption risk:** AI coding/design tools resuelven el problema nativamente. Si Cursor, Claude, Lovable, v0, o Figma integran governance de diseño para todos los tiers, el espacio de mercado desaparece.

## Roadmap Implications

Secuencia de build derivada de la cadena de dependencias — cada step es prerequisito del siguiente:

**Trade-off explícito — D-013:** La separación entre corrección (P0) y prevención (P1) es una decisión de scope que debe confirmarse. Product-thesis.md dice que "ambos outputs del mismo loop" son requeridos para validar la tesis completa. Si se shipea P0 sin el design context file, el loop que se valida en Stage 1 es parcial — solo corrige el pasado, no previene el futuro. El equipo debe decidir si esto es aceptable para Stage 1 o si el design context file debe escalarse a P0. Registrado como trade-off, no como decisión silenciosa. → OQ-010

**P0 — MVP mínimo para validar el loop:**
1. URL-based product scan (public pages, server-side)
2. Real UI kit extraction
3. Drift and inconsistency detection
4. UI kit visualization + actionable recommendations
5. Official / unofficial component decisioning
6. AI-actionable output — corrección (prompts con valores exactos)
7. Re-scan / comparison

**P1 — Completar el loop de retención:**
8. AI-actionable output — prevención (design context file: DESIGN.md / rules file)
9. Authenticated scan (si design partners lo requieren — puede escalar a P0)
10. MCP en servidor para integración más profunda con AI coding tools

**P2 — Expansión y defensibilidad:**
11. Design Intelligence module
12. Historial de scans y comparación longitudinal
13. Multi-project management
14. GitHub integration
15. Team workflows y colaboración

**Regla:** no construir P1 antes de que P0 esté validado con usuarios reales. El riesgo de construir rápido sin validación es que el loop completo falle en un punto que no es obvio desde el product design.

## Feature Children Index

| Feature | File | Status | Last updated | Technical spec |
|---|---|---|---|---|
| UI Ingestion | Strategic Artifacts/features/feature-ui-ingestion.md | draft | 2026-06-01 | Technical Artifacts/features/feature-ui-ingestion.md |
| Real UI Kit Extraction & Visualization | Strategic Artifacts/features/feature-ui-kit-extraction.md | draft | 2026-06-01 | Technical Artifacts/features/feature-ui-kit-extraction.md |
| Drift & Consistency Analysis | Strategic Artifacts/features/feature-drift-analysis.md | draft | 2026-06-01 | Technical Artifacts/features/feature-drift-analysis.md |
| Governance & Officialization | Strategic Artifacts/features/feature-governance-officialization.md | draft | 2026-06-01 | Technical Artifacts/features/feature-governance-officialization.md |
| AI-Actionable Output | Strategic Artifacts/features/feature-ai-actionable-output.md | draft | 2026-06-01 | Technical Artifacts/features/feature-ai-actionable-output.md |
| Correction & Re-scan Loop | Strategic Artifacts/features/feature-correction-rescan-loop.md | draft | 2026-06-01 | Technical Artifacts/features/feature-correction-rescan-loop.md |
| Design Context | Strategic Artifacts/features/feature-design-context.md | draft | 2026-06-01 | Technical Artifacts/features/feature-design-context.md |
| Design Intelligence | Strategic Artifacts/features/feature-design-intelligence.md | draft | 2026-06-01 | Technical Artifacts/features/feature-design-intelligence.md |
| Cross-cutting | Strategic Artifacts/features/cross-cutting.md | draft | 2026-06-01 | — |

## Open Questions

- OQ-003: ¿Qué modelo de acceso a sitio usará el MVP — server-side, browser-visible, local/desktop o hybrid? Dirección: solución web server-side + MCP en servidor. Detalle a definir con design partners.
- OQ-009: ¿Qué nivel de completitud de scan es suficiente para preservar la confianza en el primer uso?
- OQ-010: ¿Cuál es el minimum viable governance loop que puede validarse con design partners — qué subset de features P0 es verdaderamente irreducible?
