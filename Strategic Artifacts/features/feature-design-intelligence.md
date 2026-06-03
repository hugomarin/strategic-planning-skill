---
artifact: feature-design-intelligence
version: 0.1
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
technical_reference: Technical Artifacts/features/feature-design-intelligence.md
---

# Feature: Design Intelligence

## What it does

Analiza el historial de scans, las decisiones de governance, y los patrones de componentes acumulados en el design context para generar recomendaciones de mejora — no solo correcciones de drift, sino sugerencias sobre cómo fortalecer el sistema visual del producto en el tiempo. Es la capa de valor que aparece después de que el usuario ha completado múltiples governance loops.

## Why it exists

La corrección arregla problemas del pasado. La prevención protege el futuro. La intelligence mejora el sistema activamente. Sin este módulo, Schemaflow puede mantener la consistencia pero no puede ayudar al usuario a construir un sistema visual más robusto. Este módulo es la capa de defensibilidad a largo plazo — el moat que crece con el uso.

## Where it lives

`/project/[id]/intelligence` — disponible después de múltiples scans y con suficiente contexto acumulado.

---

## Sub-feature: Pattern & Variant Consolidation Recommendations

### What it does

Analiza el historial de decisiones de governance y el design context acumulado para detectar oportunidades de consolidación — componentes que podrían unificarse, variantes que persisten sin justificación, o patrones que se están volviendo inconsistentes de forma gradual.

### Why it exists

Con el tiempo, incluso un producto gobernado acumula variaciones sutiles. La intelligence detecta estos patrones antes de que se conviertan en drift significativo — y sugiere consolidaciones que simplificarían el sistema visual.

### Where it lives

`/project/[id]/intelligence/recommendations`

### How it is composed

- Lista de oportunidades de consolidación con evidencia visual
- Por cada recomendación: qué elementos podrían consolidarse, por qué, y cuál sería el beneficio esperado
- Acción recomendada: consolidar, revisar, o ignorar
- Impacto estimado: cuántos componentes o páginas afectaría la consolidación

### Who can use it

Usuarios con 3+ scans y decisiones de governance acumuladas. P2 en el roadmap.

### Rules

- Las recomendaciones son sugerencias, no instrucciones — el usuario siempre decide
- Una recomendación de consolidación debe tener evidencia concreta (no solo similitud visual)
- No mostrar recomendaciones hasta tener suficiente historial para que sean relevantes (mínimo 2–3 scans)

### What happens when it fails or is empty

- Sin suficiente historial: "Haz más scans para activar Design Intelligence"
- Sin oportunidades detectadas: "Tu sistema está bien consolidado"

### Known issues

- Ninguno — feature P2, no requerida para MVP ni para Phases 1-3

### How it should evolve

- Component ontology completa: relaciones entre componentes y su contexto de uso
- Weak pattern detection: detectar patrones que se usan de forma inconsistente con su propia intención
- Design architecture suggestions: recomendar reorganizaciones del sistema visual
- Layout consistency recommendations
- Product-specific design quality insights basados en el tipo de producto

---

## Sub-feature: Design System Health Score

### What it does

Genera un score de salud del sistema visual del producto basado en la consistencia detectada, el porcentaje de elementos gobernados, el drift trend entre scans, y la completitud del design context. Le da al usuario un número simple que resume el estado de su governance.

### Why it exists

Un número claro y progresivo ("tu sistema de diseño pasó de 45 a 72 de salud") crea engagement, justifica el uso continuado del producto, y da un objetivo concreto al usuario. Es también una señal interna de si el producto está funcionando.

### Where it lives

Dashboard del proyecto y en la vista de comparison post-rescan.

### How it is composed

- Score numérico (0–100) con categorías: crítico / mejorable / bueno / excelente
- Componentes del score: % sistema gobernado, drift reducido entre scans, completitud del design context, consistencia general
- Tendencia histórica del score entre scans
- Explicación simple de qué está impactando el score negativamente

### Who can use it

Todos los usuarios con al menos 2 scans. P2 para el score completo; una versión básica (% gobernado) puede estar disponible antes.

### Rules

- El score debe ser explicable — no un número mágico. El usuario debe entender por qué bajó o subió.
- El score no debe gamificar en exceso — el objetivo es la salud del sistema, no el número en sí
- Un score de 100 solo se puede alcanzar con 0 drift y 100% del sistema gobernado en múltiples scans consecutivos

### What happens when it fails or is empty

- Sin suficiente historial: mostrar solo el % de sistema gobernado como proxy

### Known issues

- Ninguno — feature P2

### How it should evolve

- Benchmarking anónimo: cómo se compara tu score con productos similares
- Score por módulo / área del producto
- Alertas cuando el score baja significativamente entre scans
