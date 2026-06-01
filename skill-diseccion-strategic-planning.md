# Disección del Strategic Planning Skill
## De intención a estrategia verificable

---

## El problema que resuelve este skill

La planificación estratégica falla de dos maneras: el agente inventa lo que el input no cubre, o el humano corrige tarde porque nadie validó los supuestos a tiempo.

El Strategic Planning Skill no es un generador de documentos. Es un sistema de orquestación con mecanismos explícitos de diagnóstico, validación y revisión que operan **antes**, **durante** y **después** de cada artefacto. Cada archivo del skill tiene un rol funcional en ese proceso.

La tesis central del skill lo declara así:

> *"The output should not be what AI happened to generate. It should be the product that was actually decided."*

---

## Estructura del sistema

```
SKILL.md                          ← El Orchestrator
│
├── references/
│   ├── artifact-questions.yaml   ← Motor de validación: criterios por artefacto
│   ├── templates.md              ← Estructura con disciplina
│   ├── sp-questions-format.md    ← Protocolo del registro de preguntas abiertas
│   └── feature-child-template.md ← Plantilla para features hijas
│
└── .claude/
    ├── agents/
    │   ├── diagnostic-analyst.md     ← Sub-agente: analiza input, detecta gaps
    │   └── adversarial-reviewer.md   ← Sub-agente: desafía cada artefacto
    └── references/
        └── review-report-format.md   ← Esquema del reporte de revisión
```

**Regla de arquitectura fundamental** (declarada en el SKILL.md):

> *"Subagents analyze and challenge. The Orchestrator decides, writes, versions, and publishes."*
> *"Subagents do not write files. Subagents do not publish artifacts. Subagents do not make strategic decisions."*

---

## El flujo completo

El skill declara el flujo en su sección Core Thesis:

```text
Input/ (source documents)
  → Phase 0: Diagnostic (_analysis.md)        ← Diagnostic Analyst subagent
  → Phase 1: strategy-brief.md + product-thesis.md
  → Phase 2: user-architecture.md + product-architecture.md
  → Phase 3: objectives-architecture.md
  → Phase 4: features/ children (if applicable)
  → Phase 5: strategic-roadmap.md
  → Review Checkpoint (KAs)                   ← Adversarial Reviewer subagent
  → Review Checkpoint (Roadmap)               ← Adversarial Reviewer subagent
  → Phase 6: Handoff to Task Planning
  → _analysis.md deleted
```

Una regla de prerrequisito gobierna todo el flujo:

> *"`strategic-roadmap.md` cannot be generated until all 5 Strategic Artifacts are complete. The roadmap is the output of the KA process, not a shortcut to it."*

---

## Arquitectura de agentes

| Rol | Archivo | Responsabilidad |
|---|---|---|
| Orchestrator | `SKILL.md` (este skill) | Coordina, genera, versiona, publica, decide |
| Diagnostic Analyst | `.claude/agents/diagnostic-analyst.md` | Lee `Input/`, produce reporte diagnóstico estructurado |
| Adversarial Reviewer | `.claude/agents/adversarial-reviewer.md` | Revisa KAs y roadmap, produce reporte de dos bloques |

### Invocando al Diagnostic Analyst

Invocar al inicio de `/sp-start` o `/sp-diagnose`, antes de componer `_analysis.md`.

```
Parameters to pass:
- project_path: absolute path to the project folder
- input_path: absolute path to Input/
- artifact_questions_path: absolute path to references/artifact-questions.yaml
```

> *"Do not read `Input/` yourself before the agent has run — the agent does the heavy reading."*

### Invocando al Adversarial Reviewer

Se invoca **dos veces** por sesión de planificación.

**Invocación 1 — después de todos los KAs, antes del roadmap:**
```
- review_scope: "kas"
- artifacts_path: absolute path to Strategic Artifacts/
- input_path: absolute path to Input/
- diagnostic_report_path: absolute path to Strategic Artifacts/_analysis.md
- artifact_questions_path: absolute path to .claude/references/artifact-questions.yaml
- review_format_path: absolute path to .claude/references/review-report-format.md
```

**Invocación 2 — después de generar el roadmap:**
```
- review_scope: "roadmap"
- (mismos paths)
```

---

## Los comandos — la API pública del harness

Los comandos controlan cómo el Orchestrator ejecuta el skill:

| Comando | Acción |
|---|---|
| `/sp-diagnose` | Ejecuta solo Fase 0. Invoca Diagnostic Analyst, produce diagnóstico completo. No genera ningún artefacto. |
| `/sp-start` | Ejecuta Fase 0 + presenta Input Analysis Summary. Espera confirmación humana antes de generar. |
| `/sp-next` | Ejecuta la siguiente fase pendiente. Una fase a la vez. Produce output, presenta resumen, espera confirmación. |
| `/sp-run [artifact]` | Ejecuta o recalibra un KA específico. Crea nueva versión si el artefacto ya existe. |
| `/sp-status` | Muestra estado de todos los KA: completo, en progreso, faltante, o con marcadores NHR. |
| `/sp-roadmap` | Intenta generar `strategic-roadmap.md`. Si algún KA falta o está incompleto, falla con mensaje explícito. |
| `/sp-questions [filter]` | Muestra preguntas abiertas de `open-questions.md` con sus supuestos actuales. |

**Comportamiento por defecto:** si el usuario provee input sin comando, el agente ejecuta `/sp-start` automáticamente.

---

## Fase 0 — Diagnóstico y `_analysis.md`

La Fase 0 es la más crítica del proceso. Antes de generar cualquier cosa, el sistema necesita saber qué cubre el input y qué no.

**Paso 1:** el Orchestrator invoca al Diagnostic Analyst con los paths del proyecto.

**Paso 2:** el Orchestrator compone `_analysis.md` usando el reporte del sub-agente como fuente primaria.

El esquema de `_analysis.md` es scaffolding interno — no es un entregable. Se elimina en Fase 6. Su estructura:

```md
# Input Analysis (internal scaffolding — delete after session)

## Sources available
## Ontological map
## Coverage map          ← aquí entra artifact-questions.yaml
## Claims with evidence
## Assumed claims
## Source conflicts
## Tactical inputs found
## Candidates for open-questions.md
## Non-omittable questions
## Proposed generation order
```

La sección `Coverage map` es donde `artifact-questions.yaml` entra por primera vez: el Diagnostic Analyst evalúa cada pregunta del yaml contra el input disponible.

**Checkpoint obligatorio:** antes de generar cualquier artefacto, el Orchestrator presenta un Input Analysis Summary al humano. Esta es la **única pausa obligatoria** antes de la generación:

```md
## Input Analysis Summary

### What the Input covers well
### What the Input covers partially
### What the Input does not cover
### Source conflicts found
### Tactical items found
### Non-omittable questions
### Proposed plan
Phase 1: [artifacts] — reason
...

Confirm to proceed, or adjust before I begin.
```

---

## `artifact-questions.yaml` — El motor de validación

Este archivo es el componente más crítico del sistema de calidad. No es documentación: es el criterio operativo que gobierna qué se puede generar, cuándo hay que detenerse, y qué necesita revisión humana.

### Estructura de cada pregunta

```yaml
- id: SB-01
  question: "¿Cuál es el problema central que este producto resuelve?"
  section: Problem
  type: required
  failure_signal: "El artefacto define features o soluciones sin haber articulado el problema."
  needs_human_review_if: "El problema está formulado en términos de solución, no de necesidad real."
```

Cinco campos por pregunta:

- **`id`** — identificador único por artefacto (`SB-` = strategy-brief, `PT-` = product-thesis, `UA-` = user-architecture, `PA-` = product-architecture, `OA-` = objectives-architecture)
- **`question`** — lo que el artefacto debe poder responder con honestidad
- **`type`** — `required` o `quality`
- **`failure_signal`** — patrón que indica que la pregunta no fue respondida, aunque parezca que sí
- **`needs_human_review_if`** — condición específica que dispara un marcador NHR en el artefacto

### Dos tipos de preguntas, dos consecuencias distintas

**`required`:** El artefacto está incompleto sin responder esta pregunta. Si el input no la cubre, el Orchestrator no puede generar esa sección. La marca como `[TO BE DEFINED] → OQ-XXX` y la registra en `open-questions.md` con `Blocks: roadmap`.

**`quality`:** El artefacto puede existir sin responderla, pero queda débil. El Orchestrator puede proceder haciendo un supuesto explícito. Ese supuesto va en el artefacto con marcador `⚠️ NHR` y en `open-questions.md` con la columna `Current assumption` completada.

### Cobertura del yaml

El archivo cubre los 5 artefactos principales:

| Artefacto | IDs | Preguntas |
|---|---|---|
| strategy-brief | SB-01 a SB-08 | 8 |
| product-thesis | PT-01 a PT-08 | 8 |
| user-architecture | UA-01 a UA-08 | 8 |
| product-architecture | PA-01 a PA-09 | 9 |
| objectives-architecture | OA-01 a OA-08 | 8 |

### Dos momentos de uso

**Momento 1 — Fase 0 (construcción del coverage map):**
El Diagnostic Analyst recorre todas las preguntas del yaml y las evalúa contra el input. El resultado en `_analysis.md` muestra, para cada KA, qué está respondido, parcialmente respondido, o ausente. Este mapa determina qué artefactos se pueden generar en qué profundidad.

**Momento 2 — Cierre de cada artefacto (closing gate):**
Antes de marcar un artefacto como completo, el Orchestrator verifica que las preguntas `required` están respondidas y que ninguna condición `needs_human_review_if` se cumple sin estar marcada. Si algo escapa, el Adversarial Reviewer lo detecta en el Review Checkpoint.

---

## Los marcadores NHR

Los marcadores NHR (Needs Human Review) son el mecanismo de transparencia del sistema. Cuando el Orchestrator genera contenido basado en un supuesto, marca esa sección:

```markdown
⚠️ NHR: Este segmento asume [X] porque el input no define explícitamente [Y]. → OQ-012
```

El SKILL.md hace una distinción importante entre los dos tipos de respuesta a campos faltantes:

```
- [Needs Human Review] — el agente generó algo y el humano lo revisa.
- Empty field + explicit question — el humano decide antes de que el agente genere.
```

Para targets, métricas y decisiones de roadmap, el segundo es el correcto. Los marcadores NHR persisten en el artefacto hasta que el humano resuelve la pregunta referenciada.

---

## `templates.md` — Estructura con disciplina

Las plantillas no son formularios a llenar. Cada sección lleva un contrato implícito. El SKILL.md lo enuncia como dos principios de generación que **anulan la ambición estructural**:

**Principio 1 — No generar lo que no está en el Input:**

| Situación | Comportamiento correcto |
|---|---|
| Campo faltante pero no bloqueante | Dejar vacío con pregunta explícita → OQ-XXX |
| Campo afecta targets, métricas, o decisiones de roadmap | Preguntar al humano antes de generar |
| Humano no puede responder y el agente debe continuar | Proponer opciones con razonamiento · o `[TO BE DEFINED]` · o referencia externa marcada `[external reference — not a product decision]` |

**Principio 2 — Complejidad proporcional al Input:**

> *"If the Input covers a topic in 2 paragraphs, the KA should not produce 5 sections on that topic. A sparse but honest KA is more useful than a dense KA built on agent inference."*

### El caso más delicado: `objectives-architecture.md`

La plantilla de este artefacto tiene restricciones escritas directamente en el template:

```md
## KPI Architecture
[Only populated when the human defines targets or accepts an explicit agent proposal.
Leave as [TO BE DEFINED] → OQ-XXX until then.
External benchmarks allowed only when marked [external reference — not a product decision].]
```

Y el skill lo refuerza con una regla de prerrequisito:

> *"Before generating any OKR, KPI, or target, the agent must identify non-omittable questions — inputs that cannot be inferred from the strategy alone (GTM segment, pricing model, runway, conversion assumptions). Present these to the human and wait for answers or explicit deferrals before proceeding."*

### Feature children

`feature-child-template.md` define un segundo nivel de artefactos: los archivos en `features/`. No duplican razonamiento estratégico de `product-architecture.md` — el padre posee los principios y el razonamiento arquitectónico. Los children describen comportamiento concreto, reglas de negocio, estados, y referencias a OQ-IDs para bugs y decisiones pendientes.

La activación de la Fase 4 (features children) es una decisión explícita que el skill registra en `strategic-change-log.md`:

```
Phase 4 is required if the artifact defines 5 or more modules with distinct behavior.
Phase 4 is optional if modules are fewer or behavior is not sufficiently differentiated.
Phase 4 is skipped if product-architecture.md is primarily principles and flows.
```

---

## `sp-questions-format.md` — El protocolo del registro abierto

`open-questions.md` es la memoria viva del proceso. No es una lista de tareas: es el registro completo de todo lo que el sistema no pudo resolver con el input disponible.

### Estructura de una pregunta abierta

```md
| ID | Question | Artifact | Section | Current assumption | Blocks | Priority |
| OQ-007 | ¿Cuál es el segmento de entrada? | objectives-architecture | Phase 1 | Seg A + C como co-entrada | roadmap | Alta |
```

La columna `Current assumption` es el corazón del sistema. El SKILL.md la describe así:

> *"If the agent proceeded with an assumption, state it explicitly. This is what `/sp-questions` shows so the human can confirm or replace it without opening the file."*

Con esta columna visible, el humano tiene tres opciones al revisar con `/sp-questions`:
- **Confirmar** el supuesto → se mueve a "Resolved Decisions"
- **Reemplazarlo** con una respuesta real → el Orchestrator actualiza artefacto + registro + change-log
- **Diferirlo explícitamente** → el supuesto permanece, marcado como diferido intencionalmente

### El protocolo de cross-referencia (GAP-01)

Toda pregunta abierta o marcador NHR dentro de un KA debe llevar su OQ-ID:

```
[Needs Human Review] ICP lacks observable criteria → OQ-002
¿Cuál es la estrategia de GTM? → OQ-001
```

Al generar o revisar un KA: verificar si la pregunta existe en `open-questions.md` → si no, crear con el siguiente ID disponible → escribir `→ OQ-XXX` en el KA. Nunca duplicar.

### La regla de resolución atómica

Una pregunta no está resuelta hasta completar los tres pasos en la misma operación:

1. `open-questions.md` — mover la fila a "Resolved Decisions" con decisión y fecha
2. Artefacto de origen — reemplazar el marcador NHR y `→ OQ-XXX` con la decisión; incrementar versión del KA
3. `strategic-change-log.md` — registrar el cambio

---

## Review Checkpoints — El Adversarial Reviewer en acción

Los Review Checkpoints son los dos momentos donde el sistema se desafía a sí mismo. El Adversarial Reviewer usa `artifact-questions.yaml` para detectar artefactos que parecen completos pero no lo son.

Después de cada invocación, el reporte se presenta al humano **completo y sin comprimir**:

> *"Do not summarize or compress it. The human needs both blocks fully visible."*

El reporte tiene dos bloques estructurados según `review-report-format.md`. El Orchestrator maneja cada ítem según su tipo:

| Tipo de ítem | Qué hace el Orchestrator |
|---|---|
| `orchestrator_revise` | Maneja solo. Revisa y versiona los artefactos afectados. Registra en change-log. |
| `human_input_needed` / `human_decision_needed` | Presenta como lista consolidada. Espera respuesta. |
| `open_question` | Confirma con humano antes de registrar en `open-questions.md`. |
| `accept_as_assumption` | Marca explícitamente en el artefacto. Registra en change-log. |
| `flag_for_skill_review` | Anota en el documento de handoff para iteración futura del skill. |

### Patrones que el Adversarial Reviewer detecta

Los `failure_signal` del yaml guían la revisión. Algunos de los más frecuentes:

- Una sección de "Problema" formulada en términos de solución (SB-01)
- Un ICP tan amplio que no puede guiar decisiones de producto (UA-02)
- KPIs con targets numéricos que el input no justifica (OA-05)
- Una tesis sin supuestos explícitos ni evidencia (PT-03)
- Principios de producto que no derivan de la tesis (PA-01)

---

## Versionado de artefactos

Cada Knowledge Artifact incluye frontmatter con estado explícito:

```md
---
artifact: strategy-brief
version: 0.1
status: draft
current: false
last_updated: YYYY-MM-DD
needs_human_review: true
---
```

| Versión | Significado |
|---|---|
| `v0.x` | Draft, puede tener NHR y gaps |
| `v1.0` | Aceptado por el humano como fuente de verdad |
| `v1.x` | Actualización menor (nueva información, NHR resuelto) |
| `v2.0+` | Revisión mayor (cambio de tesis, ICP, arquitectura o secuencia de roadmap) |

**Regla de cascada:**

> *"When a KA is revised, the agent evaluates whether downstream artifacts are affected. If they are, it marks them as `needs_human_review` and proposes what to update. It does not silently update downstream artifacts without presenting the impact."*

---

## Fase 6 — Handoff a Task Planning

`_analysis.md` se elimina. El Orchestrator produce un documento de handoff estructurado:

```md
# Strategic Planning Handoff

## Current Roadmap Version
## Strategic Direction to Preserve
## Initiatives Ready for Task Planning
## Context Required by Task Planning
## Decisions That Must Not Be Reinterpreted
## Constraints and Trade-offs to Preserve
## Validation Objectives and KPIs
## Open Questions Requiring Human Review
## Risks to Watch During Task Planning
## Skill Review Flags
```

La pregunta de salida que valida el handoff:

> *"Can `strategic-roadmap.md` feed Task Planning without the next agent having to invent, reinterpret, or weaken the original strategic intention?"*

---

## Construir tu propio harness

Los patrones transferibles del Strategic Planning Skill:

**El yaml de criterios como motor de validación** — cualquier proceso que produzca artefactos puede tener un archivo de criterios que el sistema consulta antes de generar y el revisor usa para desafiar. La clave es separar `required` (bloqueante) de `quality` (NHR pero puede continuar).

**La dualidad analista / revisor adversarial** — el analista diagnostica cobertura antes de generar; el revisor adversarial desafía lo generado. Esta oposición evita que el sistema confirme lo que el humano ya pensaba.

**El registro de preguntas abiertas con supuestos explícitos** — `open-questions.md` hace que los supuestos sean visibles y trazables. En cualquier proceso donde el input es incompleto, este patrón evita que los supuestos queden enterrados en el texto de los artefactos.

**Templates con restricciones en la propia plantilla** — la disciplina de "no llenes lo que el input no soporta" está escrita en el template, no solo en las instrucciones del skill.

**La regla de resolución atómica** — actualizar simultáneamente el registro, el artefacto de origen y el change-log evita estados inconsistentes. Es un patrón de integridad de datos aplicado a documentos estratégicos.

**Handoff estructurado** — el último artefacto no es el roadmap. Es el documento que le dice al siguiente momento qué debe preservar y qué no puede reinventar.

---

## Loop Dimensions Check

El skill incluye 10 dimensiones de validación que el Orchestrator verifica antes del handoff:

| Dimensión | Pregunta |
|---|---|
| D1 Intent | ¿Preserva el roadmap la tesis, prioridades y anti-prioridades del producto? |
| D2 Context | ¿Está el roadmap fundamentado en fuentes identificables? |
| D3 Schema | ¿Organiza el roadmap fases, iniciativas, dependencias, riesgos, validación? |
| D4 Skills | ¿Puede el proceso repetirse usando este skill? |
| D5 Tools | ¿Se consideraron todas las fuentes, incluyendo conflictos e items tácticos? |
| D6 Execution | ¿Puede el roadmap convertirse en iniciativas e issues en Task Planning? |
| D7 Memory | ¿Se registraron los cambios y versiones de roadmap? |
| D8 Objectives | ¿Cada fase del roadmap está vinculada a al menos un KR o milestone de validación? |
| D9 Scaffolding | ¿Se eliminó `_analysis.md` antes del handoff final? |
| D10 Review | ¿Se completaron ambos Review Checkpoints y se resolvieron sus outputs? |

---

*Este documento es una disección del skill tal como está construido. Si quieres construir tu propio harness, los patrones que más vale replicar son: el yaml de criterios, la dualidad analista/revisor, y el registro atómico de preguntas abiertas.*
