---
artifact: feature-drift-analysis
version: 0.1
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
technical_reference: Technical Artifacts/features/feature-drift-analysis.md
---

# Feature: Drift & Consistency Analysis

## What it does

Analiza el UI kit extraído para detectar inconsistencias, variantes accidentales, duplicación de estilos, y desviaciones entre elementos que deberían ser iguales. Le muestra al usuario dónde está perdiendo control visual — con evidencia trazable y distinción clara entre lo que se observó y lo que se infirió. Es el módulo que convierte a Schemaflow de un inventario en una herramienta de governance.

## Why it exists

El usuario no puede gobernar lo que no puede ver. La extracción le muestra qué existe. La drift analysis le muestra qué está mal. Sin este módulo, Schemaflow es un catalogador — útil, pero no un governance layer.

## Where it lives

`/scan/[id]/drift` — tab o sección dentro del scan completado, después de la UI kit view.

---

## Sub-feature: Drift Detection

### What it does

Detecta inconsistencias entre elementos que deberían ser iguales o compartir un patrón visual. Agrupa las variantes accidentales, identifica las duplicaciones de estilos, y organiza los hallazgos por tipo y severidad aproximada.

### Why it exists

Los builders no siempre pueden ver el drift porque lo generaron de forma incremental. Schemaflow lo hace visible de golpe — "tienes 7 variantes de botón primario en tu producto."

### Where it lives

`/scan/[id]/drift` — lista de problemas detectados.

### How it is composed

- Lista de inconsistencias agrupadas por tipo: botones, tipografía, colores, spacing, inputs, cards, otros
- Por cada inconsistencia: las variantes detectadas con sus valores exactos, la página donde aparece cada una, y la acción recomendada
- Indicador de frecuencia: cuántas instancias de cada variante existen
- Badge de evidencia: "observado directamente" vs. "inferido por agrupación"
- Recomendación por item: consolidar, oficializar, ignorar, o revisar

### Who can use it

Todos los usuarios. El nivel de detalle puede limitarse en el free tier.

### Rules

- Nunca marcar una diferencia como "drift" si podría ser intencional y no hay evidencia de inconsistencia (ej. un dark mode genuino)
- Siempre mostrar los valores exactos de cada variante — no "botones inconsistentes" sino "3 variantes: `#4F3EAD`, `#3B2F8A`, `#5C4AE8`"
- No abrumar con todos los hallazgos al mismo tiempo — priorizar y organizar por categoría
- El usuario debe poder ignorar intencionalmente un hallazgo (ej. "esta diferencia es intencional")
- La distinción observado/inferido debe estar presente en cada item

### What happens when it fails or is empty

- Sin drift detectado: mensaje positivo ("Tu producto tiene buena consistencia visual en las páginas escaneadas") + recomendación de agregar más URLs
- Análisis incompleto: mostrar lo que se pudo analizar + advertencia de cobertura

### Known issues

- OQ-009: Sin definir umbral de cobertura mínima — si el scan cubre pocas páginas, el drift detectado puede ser incompleto y dar falsa sensación de consistencia

### How it should evolve

- Severity scoring (crítico / importante / cosmético)
- Visual debt score por página o por proyecto
- Drift trends entre scans (este problema empeoró vs. mejoró)
- Comparación contra el sistema oficial (después de que el usuario lo haya definido)
- Page-level drift heatmap

---

## Sub-feature: Scan Evidence and Trust Layer

### What it does

Muestra la evidencia concreta de cada hallazgo — de qué página viene, qué elemento del DOM o CSS fue detectado, y si fue observado directamente o inferido. Le permite al usuario verificar que Schemaflow no está inventando o exagerando los problemas.

### Why it exists

La confianza en el diagnóstico es prerequisito de la acción. Si el usuario no puede trazar un hallazgo a una fuente concreta, va a dudar del diagnóstico. Y si duda del diagnóstico, no va a actuar — ni va a volver para un segundo scan.

### Where it lives

Panel de evidencia expandible en cada item de drift y en cada componente del UI kit.

### How it is composed

- Por cada componente o inconsistencia detectada: URL de la página fuente, screenshot o referencia visual, elemento DOM o CSS de origen
- Badge claro: "Observado directamente" / "Inferido por agrupación" / "Recomendado"
- Opción de "Ver en contexto" — ver el elemento en la página original
- Indicador de confianza cuando corresponda

### Who can use it

Todos los usuarios.

### Rules

- Nunca mostrar un hallazgo sin su evidencia mínima (al menos la URL de origen)
- La distinción observado/inferido/recomendado es obligatoria — nunca mezclar las tres categorías sin marcarlas
- No esconder hallazgos de baja confianza — mostrarlos con su nivel de confianza para que el usuario decida

### What happens when it fails or is empty

- Sin evidencia disponible para un hallazgo específico: marcarlo con advertencia y dar opción de "reportar problema de detección"

### Known issues

- Ninguno adicional a los del scan

### How it should evolve

- Click-to-inspect: abrir el elemento fuente en DevTools o en el código del repositorio
- Cross-page evidence: mostrar todas las páginas donde aparece el mismo elemento
- Explainability panel: por qué Schemaflow decidió agrupar estos elementos como la misma variante

---

## Sub-feature: Scan Quality Feedback

### What it does

Permite al usuario reportar detecciones incorrectas o faltantes — "esto es incorrecto," "falta este componente," "esta variante es intencional." Captura feedback del usuario para mejorar la calidad del scan en el tiempo.

### Why it exists

La detección no será perfecta en las primeras versiones. Sin un mecanismo de feedback, el usuario pierde confianza silenciosamente. Con él, el producto puede aprender y mejorar, y el usuario siente que tiene control sobre la calidad del diagnóstico.

### Where it lives

Botón o link "Reportar problema" en cada item del UI kit y de la drift analysis.

### How it is composed

- Botón "Esto es incorrecto" por cada item
- Opciones rápidas: "No detectaste este componente," "Esta variante es intencional," "Este agrupamiento es incorrecto," "Este valor es inexacto"
- Campo opcional de texto libre
- Confirmación de recibo del feedback

### Who can use it

Todos los usuarios. P1 en el roadmap.

### Rules

- El feedback no debe interrumpir el flujo principal — debe ser accesible pero no prominente
- Nunca auto-corregir el diagnóstico en base al feedback sin que el usuario lo confirme — el feedback es una señal, no una instrucción directa

### What happens when it fails or is empty

- Sin feedback enviado: neutral — el flujo continúa normalmente

### Known issues

- Ninguno adicional

### How it should evolve

- Human review queue interna para procesar el feedback
- Active learning: usar correcciones del usuario para mejorar la detección a nivel de proyecto
- Project-specific detection rules: "en este proyecto, este estilo es intencional"
