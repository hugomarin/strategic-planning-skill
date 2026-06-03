---
artifact: objectives-architecture
version: 0.1
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
---

# Objectives Architecture

## Purpose

Definir los objetivos medibles que validan la estrategia etapa por etapa. Este artefacto precede al strategic-roadmap — el roadmap no puede generarse sin que los objetivos de validación estén definidos.

**Premisa fundamental:** Schemaflow está en estado de validación de value proposition, no de optimización de monetización. Los objetivos de este artefacto reflejan esa realidad. No se asume un roadmap validado ni un modelo de pricing definido.

---

## Strategic Objectives

El objetivo principal en esta etapa no es monetizar — es probar que el governance loop funciona.

**Objetivo central:** Validar el minimum governance loop: usuarios ingresan URLs de su producto, reciben un UI kit real y diagnóstico de drift confiable, entienden qué acciones tomar, usan los outputs de Schemaflow para corregir o guiar la corrección, y regresan para un segundo scan que muestra mejora observable.

**Definición de activación:** El usuario completó el loop mínimo:
primer scan → identifica drift / UI kit → elige qué es oficial → aplica o exporta correcciones → corre segundo scan → ve que la consistencia mejoró.

**Sentimiento objetivo del usuario:** *"Encontré el desorden, lo entendí, lo limpié, implementé los cambios, y el producto mejoró de forma medible."*

---

## North Star Metric

**Completed Governance Loop Rate**

**Definición:** usuarios que completan primer scan → acción de governance → segundo scan con mejora visible, dividido sobre usuarios que completan el primer scan.

**Fórmula:** `Completed Governance Loop Rate = usuarios(scan → acción → re-scan con mejora) / usuarios(primer scan completo)`

**Por qué este metric y no otro:** captura las tres cosas que la tesis predice: (1) el diagnóstico fue útil — el usuario vio drift real, (2) el usuario actuó — marcó componentes, exportó instrucciones, implementó correcciones, (3) el usuario volvió — corrió un segundo scan para verificar. Un usuario que solo escanea prueba curiosidad. Un usuario que completa el loop prueba valor.

**Métricas de soporte:**
- Activation rate: % de usuarios que completan el primer scan y reconocen problemas válidos
- Action rate: % de usuarios que marcan oficial/no-oficial, exportan instrucciones, o implementan correcciones
- Re-scan rate: % de usuarios activados que corren segundo y tercer scan
- Quality metric: reducción de drift entre scans (variantes accidentales, componentes inconsistentes)
- Economic metric: costo por governance loop completado

**Anti-métricas — ver sección al final.**

---

## Validation Stages

Schemaflow usa etapas de validación en lugar de fases de roadmap porque el roadmap no puede definirse responsablemente antes de que la value proposition esté validada.

---

### Stage 0 — Design Partner Recruitment

**Lo más importante que debe ser verdad al final de esta etapa:**
Schemaflow puede encontrar 5–10 personas relevantes dispuestas a testear el producto y dar feedback significativo con un producto real.

**Señales de que está funcionando:**
- Builders AI-nativos, freelancers, agencias pequeñas, o founders aceptan participar
- Al menos 60% de los candidatos cualificados contactados aceptan una conversación o demo
- Los participantes tienen productos reales con URL, beta, o superficie de cliente real

**Señales de que algo está mal:**
- No se pueden reclutar 5 personas en X semanas después de contactar a candidatos cualificados
- Todos los que aceptan son demasiado tempranos (sin producto real) o no tienen el problema

**Thesis link:** [Needs Human Review] Esta etapa valida parcialmente la **Suposición 3** de PT-03 — que el costo de tiempo de corrección eventualmente supera el umbral donde el builder busca una solución dedicada. Si no se puede reclutar a nadie que sienta urgencia, la suposición puede ser prematura. También valida la **Suposición 1** — que el problema existe de forma recurrente en builders reales. → OQ-005

**Milestone de validación (observable):**
Al menos 5 design partners relevantes someten o comparten una URL, repo, conjunto de screenshots, o superficie de producto real para testear. Una conversación amigable no cuenta. Una superficie de producto real cuenta.

---

### Stage 1 — Value Proposition / Activation

**Lo más importante que debe ser verdad al final de esta etapa:**
Los usuarios experimentan que Schemaflow los ayuda a recuperar control sobre su diseño.

**Señales de que está funcionando:**
- Al menos 70% de design partners completan un primer scan de un producto real
- Al menos 50% identifican problemas de UI reales que reconocen como válidos (componentes duplicados, variantes accidentales, drift, inconsistencias)
- Al menos 40% completan una acción de governance: marcan algo como oficial/no-oficial, exportan instrucciones, implementan una corrección, aceptan una recomendación, o preparan un prompt de agente

[Needs Human Review] Estos targets son **hipótesis iniciales, no commitments.** Sin baselines previos ni benchmarks comparables. A validar con los primeros design partners. → OQ-006

**Señales de que algo está mal:**
- Los usuarios completan el scan pero no identifican problemas que reconocen como suyos — el diagnóstico no refleja su producto real
- Los usuarios ven el diagnóstico pero no toman ninguna acción — el path de acción no es claro o los prompts de corrección no son lo suficientemente precisos
- Ningún usuario completa el re-scan espontáneamente

**Thesis link:** [Needs Human Review] Esta etapa valida directamente las **Suposiciones 1, 2, 4, y 9** de PT-03: (1) el drift es real y recurrente en builders reales, (2) los builders tienen estándares visuales aunque no sepan diseño formal, (4) confiarán en el diagnóstico de AI si es específico y trazable, (9) Schemaflow puede extraer un real UI kit confiable. Si ninguna de estas se cumple, la tesis central está en riesgo. → OQ-005

**Milestone de validación (observable):**
Un usuario completa el primer governance loop: escanea un producto real → ve el UI kit generado o el diagnóstico de drift → identifica problemas válidos → toma al menos una acción de governance → corre un segundo scan que muestra mejora observable.

---

### Stage 2 — Retention / Governance Behavior

**Lo más importante que debe ser verdad al final de esta etapa:**
Algunos usuarios convierten Schemaflow en parte de su workflow de producto — no solo como diagnóstico puntual.

**Señales de que está funcionando:**
- Al menos 30–40% de usuarios activados corren un segundo scan dentro de 7–14 días o después de implementar cambios
- Al menos 50% de usuarios que corren el segundo scan ven mejora observable (menos variantes, menos drift, mayor consistencia)
- Al menos 25% de usuarios activados corren un tercer scan o agregan nuevas URLs/páginas

[Needs Human Review] Hipótesis iniciales — validar con comportamiento real de design partners. → OQ-006

**Señales de que algo está mal:**
- Los usuarios usan Schemaflow como diagnóstico puntual pero no regresan después de corregir
- El segundo scan no muestra mejora observable — los prompts de corrección no fueron lo suficientemente precisos, o el design context file no fue adoptado
- Ningún usuario corre espontáneamente un tercer scan

**Thesis link:** [Needs Human Review] Esta etapa valida las **Suposiciones 5, 6, y 10** de PT-03: (5) mantener buen diseño a través de iteraciones AI seguirá siendo difícil sin una capa de control dedicada, (6) el design context file generado reducirá el drift en sesiones futuras de forma observable, (10) la re-escaneabilidad es un comportamiento natural para este usuario. Si el re-scan no ocurre espontáneamente, la Suposición 10 falla — y la retención del producto no puede depender de recordatorios. → OQ-005

**Milestone de validación (observable):**
El usuario vuelve sin ser guiado manualmente y corre otro scan porque hizo cambios en el producto o quiere verificar que la consistencia se está preservando. El evento importante no es solo volver a visitar — es volver a escanear por una razón de governance.

---

### Stage 3 — Usage Economics / Cost Understanding

**Lo más importante que debe ser verdad al final de esta etapa:**
Schemaflow entiende el costo de servir el producto antes de definir pricing.

**Señales de que está funcionando:**
- Costo por scan medido (crawling, extracción HTML/CSS, screenshots, análisis AI, storage, procesamiento)
- Costo por usuario activado calculado (primer scan + acción de governance + re-scan)
- Costo del governance loop básico conocido (primer scan + export/acción + re-scan)

[Needs Human Review] KR-3 del documento fuente incluye un placeholder: "≤ 20–30% de un precio mensual hipotético" — el precio hipotético no está definido y no puede serlo hasta que Stage 3 genere datos reales. Dejar como [TO BE DEFINED] → OQ-006

**Señales de que algo está mal:**
- El costo por governance loop es tan alto que ningún modelo de pricing factible generaría margen positivo
- Los scans de páginas autenticadas o complejas tienen costos de procesamiento desproporcionados que no escalan

**Thesis link:** Esta etapa no valida directamente la tesis de producto — valida la viabilidad económica del negocio. Es prerequisito de Stage 4 (monetización), no de la tesis central. Si Stage 3 revela que el costo es insostenible, el desafío es de unit economics, no de product-market fit.

**Milestone de validación (observable):**
Schemaflow puede calcular el costo de entrega de: (a) un scan completo con análisis de AI, (b) un re-scan, (c) un export AI-actionable, (d) un usuario activado completo. Los datos son medibles, no estimados.

---

### Stage 4 — Monetization Hypothesis

**Lo más importante que debe ser verdad al final de esta etapa:**
Al menos un segmento ve suficiente ROI como para pagar.

**Señales de que está funcionando:**
- Al menos 20–30% de usuarios activados expresan intención de pago clara cuando se exponen a un paywall, upgrade simulado, o conversación de pricing
- Al menos 10–15% de usuarios activados intentan acceder a un feature de valor limitado (más páginas, más scans, historial, scan autenticado, múltiples proyectos, reglas persistentes, exports AI-actionables)
- Al menos un segmento con señales de ROI repetidas identificado (ej. freelancers/agencias que conectan Schemaflow a entrega de cliente, o founders con productos maduros que conectan Schemaflow a horas de corrección ahorradas)

[Needs Human Review] Targets son hipótesis iniciales — sin datos de conversión previos. El ICP monetizable aún no está validado (OQ-002). → OQ-002, OQ-006

**Señales de que algo está mal:**
- Los usuarios valoran el producto pero ninguno expresa intención de pago
- El segmento que paga es demasiado estrecho para construir un negocio sostenible
- Los límites del free tier que generan upgrade intent también cortan el aha moment antes de que ocurra

**Thesis link:** Esta etapa valida las **Suposiciones 7 y 8** de PT-03: (7) los builders que experimentan el benefit del governance loop lo suficientemente claro pagarán por él, (8) el segmento que paga será más estrecho que el segmento que usa. Si ningún segmento muestra WTP después de experimentar el valor, la Suposición 7 falla y la tesis de negocio — no la tesis de producto — necesita revisión. → OQ-005

**Milestone de validación (observable):**
Al menos un segmento intenta cruzar un límite de valor — intenta acceder a más scans, más páginas, historial, scan autenticado, múltiples proyectos, o exports AI-actionables. El evento observable no es que el usuario diga que pagaría — es que intenta usar algo que está detrás de un límite.

---

## KPI Architecture

[Needs Human Review] Los siguientes KPIs son señales de seguimiento. Los targets marcados son hipótesis iniciales — no commitments. Los métodos de medición exactos se definen en Stage 3 cuando la instrumentación esté activa. → OQ-006

| KPI | Definición | Stage | Target hipotético | Tipo de señal | Thesis link |
|---|---|---|---|---|---|
| Design partner recruitment rate | % de candidatos cualificados contactados que aceptan participar | 0 | ≥ 60% | Señal de problema y promesa | Suposición 1, 3 |
| First scan completion rate | % de design partners que completan un primer scan de un producto real | 1 | ≥ 70% | Señal de adquisición y onboarding | Suposición 9 |
| Problem recognition rate | % de usuarios que identifican problemas válidos tras el primer scan | 1 | ≥ 50% | Señal de diagnóstico confiable | Suposición 1, 4, 9 |
| Governance action rate | % de usuarios que toman al menos una acción de governance (officialize, export, correct) | 1 | ≥ 40% | Señal de valor accionable | Suposición 2, 4 |
| **Completed Governance Loop Rate** (North Star) | % de usuarios activados que completan scan → acción → re-scan con mejora observable | 1–2 | [TO BE DEFINED] → OQ-006 | Señal de valor completo | Suposiciones 1–10 |
| Re-scan rate | % de usuarios activados que corren un segundo scan | 2 | ≥ 30–40% | Señal de retención | Suposición 10 |
| Second-scan improvement rate | % de usuarios que corren el segundo scan y ven mejora observable | 2 | ≥ 50% | Señal de valor real del loop | Suposición 6, 9 |
| Third scan / workflow adoption | % de usuarios activados que corren un tercer scan o agregan páginas | 2 | ≥ 25% | Señal de hábito incipiente | Suposición 5, 10 |
| Cost per governance loop | Costo total de entregar primer scan + export + re-scan | 3 | [TO BE DEFINED] → OQ-006 | Señal de viabilidad económica | No aplica |
| Upgrade intent rate | % de usuarios activados que expresan intención de pago o intentan cruzar un límite | 4 | ≥ 20–30% | Señal de WTP | Suposición 7, 8 |

---

## Validation Sequence

La secuencia de validación sigue el orden de incertidumbre — lo más incierto primero, al menor costo posible.

**Más incierto primero:**

1. **¿Podemos encontrar 5–10 personas que sientan el problema con urgencia suficiente?** (Stage 0) — sin esto, nada de lo que sigue importa
2. **¿El governance loop entrega valor observable en un solo ciclo?** (Stage 1) — sin esto, no hay retention que medir
3. **¿Los usuarios vuelven espontáneamente?** (Stage 2) — sin esto, no hay negocio recurrente que monetizar
4. **¿El costo de entrega es viable?** (Stage 3) — sin esto, el pricing no tiene base
5. **¿Algún segmento paga?** (Stage 4) — solo tiene sentido validar esto después de los cuatro anteriores

**No saltar etapas.** Intentar monetizar antes de validar la retención es el error más común — y el más caro.

---

## Anti-metrics

Las siguientes métricas pueden parecer señales de éxito pero son engañosas para Schemaflow en esta etapa. Optimizar para ellas sin las métricas correctas produce falsa sensación de tracción.

| Anti-métrica | Por qué es engañosa | Qué trackear en su lugar |
|---|---|---|
| Total de scans | Un scan sin acción de governance solo prueba curiosidad | Completed Governance Loop Rate |
| Signups / usuarios registrados | Registro ≠ activación ≠ valor experimentado | Governance action rate |
| GitHub stars del repositorio | Stars sin uso activo del producto son vanidad | Re-scan rate |
| Primer scan completado | El primer scan sin re-scan prueba awareness, no valor | Second-scan rate |
| Files generated (DESIGN.md, ui-kit.md) | Un archivo generado y no usado no prueba que el loop funciona | Files que el usuario reporta haber injertado en su AI session |
| Tiempo en la app / pageviews | Engagement sin acción puede significar confusión, no valor | Actions taken / governance decisions made |
| NPS después del primer scan | El usuario puede calificar bien una herramienta que no vuelve a usar | Repeat scan behavior en las dos semanas siguientes |

---

## Open Questions

- OQ-002: ¿Quién es el primer ICP monetizable — qué sub-segmento muestra WTP antes que los demás? Hipótesis: builders con productos serios y monetizables donde la consistencia visual importa. Determina los targets de Stage 4.
- OQ-005: Mapeo explícito de cada stage de validación a cada suposición específica de PT-03. Los links incluidos en este artefacto son una propuesta del Orchestrator — requieren revisión humana para confirmar que el mapeo es correcto.
- OQ-006: Métodos de medición por KPI — cómo se trackea cada métrica en la práctica. Los targets hipotéticos requieren instrumentación activa para volverse targets reales.
- OQ-011: Anti-métricas formalizadas — incluidas en este artefacto; confirmar si la lista está completa o requiere ajustes.
