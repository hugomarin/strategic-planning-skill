---
artifact: feature-governance-officialization
version: 0.1
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
technical_reference: Technical Artifacts/features/feature-governance-officialization.md
---

# Feature: Governance & Officialization

## What it does

Le permite al usuario definir qué componentes, variantes, y estilos son "oficiales" en su producto — es decir, los que deben seguir existiendo y los que el AI debe preservar en futuras sesiones. También le permite marcar elementos como drift, deprecados, o ignorados intencionalmente. Es el módulo donde el usuario recupera la autoría sobre su sistema visual.

## Why it exists

Schemaflow puede detectar drift, pero no puede decidir por el usuario qué es correcto. La governance requiere que el usuario tome decisiones. Sin officialization, el producto solo diagnostica — no governa. Este módulo es la diferencia entre un scanner y un governance layer.

## Where it lives

Panel de decisiones en `/scan/[id]/governance` — accesible desde cada item del UI kit y de la drift analysis.

---

## Sub-feature: Official / Unofficial Component Decisioning

### What it does

Por cada componente, variante, o estilo detectado, el usuario puede marcarlo como oficial (parte del sistema visual intencional del producto), no-oficial / drift (error o inconsistencia a corregir), o ignorado intencionalmente (diferencia válida que no debe tratarse como problema). Schemaflow usa estas decisiones como fuente de verdad para generar los outputs AI-actionables.

### Why it exists

La fuente de verdad para los prompts de corrección y el design context file debe venir del usuario, no de inferencias del sistema. Si Schemaflow decide solo, puede officializar el estado incorrecto o silenciar variantes intencionales. El usuario debe mantener la autoría.

### Where it lives

Panel lateral o inline en cada item del UI kit y de la drift analysis. También accesible desde `/scan/[id]/governance`.

### How it is composed

- Por cada componente / variante / estilo detectado:
  - Botón "Oficial" — este es el que debe existir, el AI debe preservarlo
  - Botón "Drift / No oficial" — este es un error, debe ser corregido
  - Botón "Ignorar" — esta diferencia es intencional, no es un problema
- Estado guardado por sesión de scan y persistido en el proyecto
- Vista consolidada de todas las decisiones tomadas ("Mis componentes oficiales")
- Indicador de progreso: cuántos items han sido decididos vs. pendientes
- Sugerencia de Schemaflow (marcada como inferencia) para facilitar la decisión

### Who can use it

Todos los usuarios. Las decisiones se guardan a nivel de proyecto.

### Rules

- El usuario siempre tiene la última palabra — Schemaflow sugiere, el usuario confirma
- Una decisión de officialization puede cambiarse en cualquier momento
- Si el usuario marca un elemento como "oficial" y existe un elemento idéntico en múltiples páginas, la decisión aplica a todas las instancias
- Si el usuario marca un elemento como "drift," Schemaflow lo incluye en los prompts de corrección con el valor del elemento oficial correspondiente
- Schemaflow puede pre-seleccionar una sugerencia (el elemento más frecuente como "oficial"), pero siempre debe ser visible que es una sugerencia, no una decisión tomada

### What happens when it fails or is empty

- Sin decisiones tomadas: el sistema puede generar outputs con sugerencias de Schemaflow, pero los marca como "sugeridos por Schemaflow, no confirmados por el usuario"
- Error al guardar: notificación + retry

### Known issues

- Ninguno adicional

### How it should evolve

- Approval workflow para equipos (otro miembro del equipo debe aprobar la decisión)
- Component status lifecycle: borrador → en revisión → oficial → deprecado
- Reglas adjuntas a componentes oficiales ("el botón primario nunca debe usarse sin ícono en mobile")
- Versionado de decisiones (cuándo cambió y quién lo cambió)
- Vista de library de componentes oficiales del proyecto

---

## Sub-feature: Governance Summary

### What it does

Muestra un resumen del estado de governance del proyecto — cuántos elementos están oficializados, cuántos son drift pendiente de corrección, cuántos están ignorados intencionalmente, y qué porcentaje del sistema visual está gobernado.

### Why it exists

El usuario necesita saber si avanzó. Un número claro ("60% de tu sistema visual está gobernado") es más motivador y orientador que una lista infinita de items sin progreso visible.

### Where it lives

Dashboard del proyecto o panel superior de `/scan/[id]/governance`.

### How it is composed

- Contador de elementos oficiales / drift / ignorados / pendientes
- Porcentaje de sistema gobernado (elementos con decisión / total elementos)
- Lista de items pendientes de decisión, ordenados por frecuencia o importancia
- CTA para continuar con los items pendientes

### Who can use it

Todos los usuarios.

### Rules

- El porcentaje de "sistema gobernado" debe ser interpretable — explicar brevemente qué significa
- No presionar al usuario para oficializar todo — algunos elementos puede no requerir decisión

### What happens when it fails or is empty

- Sin decisiones: 0% con CTA para empezar a tomar decisiones

### Known issues

- Ninguno

### How it should evolve

- Governance score histórico entre scans
- Drift recurrence rate: qué elementos previamente corregidos volvieron a aparecer
