---
artifact: feature-ui-kit-extraction
version: 0.1
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
technical_reference: Technical Artifacts/features/feature-ui-kit-extraction.md
---

# Feature: Real UI Kit Extraction & Visualization

## What it does

Extrae el UI kit que realmente existe en el producto del usuario a partir del scan — colores, tipografía, espaciados, botones, inputs, cards, y demás patrones visuales — y lo presenta de forma visual e inspectable. El usuario ve el sistema visual real de su producto, organizado, aunque nunca lo haya documentado. Este es el primer aha moment del producto.

## Why it exists

Los builders AI-nativos no tienen un registro organizado de lo que su producto realmente usa. Lo que existe es el resultado acumulado de múltiples sesiones de AI, cada una con sus propias interpretaciones. La extracción le muestra al usuario la realidad de su UI — sin filtros aspiracionales. Sin este módulo, no hay nada que gobernar.

## Where it lives

Pantalla principal del scan completado: `/scan/[id]/ui-kit`.

---

## Sub-feature: Real UI Kit Extraction

### What it does

Analiza el DOM, CSS computado, y evidencia visual capturada durante el scan para identificar y organizar los elementos del sistema visual del producto: paleta de colores real, fuentes y tamaños tipográficos, espaciados comunes, variantes de botones, tipos de inputs, cards, y otros patrones de componentes repetidos.

### Why it exists

El aha moment del producto depende de mostrarle al usuario algo verdadero y no obvio: "esto es lo que tu producto realmente está usando." Sin extracción precisa, la visualización no tiene credibilidad y el diagnóstico posterior no tiene base.

### Where it lives

Proceso de backend que corre después del scan. Los resultados se muestran en `/scan/[id]/ui-kit`.

### How it is composed

- Extractor de colores: paleta real de valores hex/rgb usados en el producto (backgrounds, textos, borders, shadows)
- Extractor de tipografía: familias tipográficas, tamaños, pesos, y line-heights usados
- Extractor de espaciados: patrones de padding, margin, y gap comunes
- Detector de componentes: botones (variantes, estados, tamaños), inputs, cards, badges, switches, navigation elements
- Identificador de variantes: agrupa elementos visualmente similares bajo el mismo componente
- Clasificador de patrones: detecta elementos que se repiten en múltiples páginas vs. elementos únicos

### Who can use it

Todos los usuarios. La profundidad de la extracción puede estar limitada en el free tier (ej. solo primera página, o análisis superficial).

### Rules

- Nunca inventar colores, fuentes, o componentes que no aparecen en la UI escaneada
- Siempre distinguir: observado directamente vs. inferido por agrupación
- Si un elemento aparece en solo una página, marcarlo con menor confianza que uno que aparece en múltiples páginas
- Los valores deben ser exactos (no "azul" sino `#4F3EAD`), ya que se usarán en los prompts de corrección
- No asumir que el design system declarado (si existe) es equivalente al real — usar solo la evidencia del scan

### What happens when it fails or is empty

- Scan con muy poco contenido CSS: advertencia de cobertura baja + explicación de limitaciones del scan
- Página con CSS puramente inline o shadow DOM: fallback a extracción visual
- Ningún patrón repetido detectado: mostrar lo encontrado sin agrupar + advertencia de que el producto puede tener muy pocas páginas escaneadas

### Known issues

- OQ-009: El nivel de completitud de extracción que preserva la confianza del usuario no está definido aún — se validará con design partners

### How it should evolve

- Extracción de design tokens (variables CSS, Tailwind config)
- Component ontology: entender la relación entre componentes (ej. este botón vive dentro de este card)
- Análisis de frecuencia de uso por componente
- Comparación contra brand manual o Figma (referencia externa)
- Extracción de componentes de librerías específicas (shadcn, Radix, MUI)

---

## Sub-feature: UI Kit Visualization

### What it does

Presenta el UI kit extraído en una interfaz visual que el usuario puede inspeccionar, navegar, y evaluar. Organiza el sistema visual por categorías (colores, tipografía, componentes, etc.) y muestra evidencia de dónde fue encontrado cada elemento.

### Why it exists

La extracción sin visualización no es accionable. El usuario debe poder ver lo que Schemaflow encontró, navegar por los elementos, juzgar si refleja su producto real, y tomar decisiones basadas en eso. La visualización es también la capa de confianza — si el usuario puede trazar cada elemento a una página concreta de su producto, confía en el diagnóstico.

### Where it lives

`/scan/[id]/ui-kit` — vista principal del scan.

### How it is composed

- Secciones organizadas: Colors, Typography, Buttons, Inputs, Cards, Components, Spacing, Other
- Inventory visual de cada elemento con su valor exacto (hex, px, rem, etc.)
- Badge de "observado" vs. "inferido" por elemento
- Link de evidencia: "detectado en [página]" con thumbnail o screenshot
- Contador de apariciones: cuántas páginas o instancias tiene este elemento
- Variantes agrupadas visualmente cuando corresponde

### Who can use it

Todos los usuarios.

### Rules

- Cada elemento visible debe tener al menos una referencia a su fuente (URL o página donde se detectó)
- Los valores deben ser exactos y copiables (el usuario puede necesitar el valor para correcciones manuales o para entender los prompts de corrección)
- La distinción observado/inferido debe ser visible pero no dominante — no puede distraer del contenido principal
- No ocultar variantes porque "son similares" — mostrarlas y dejar que el usuario decida si son intencionales o drift

### What happens when it fails or is empty

- Extracción pobre: mostrar lo que se encontró con banner de cobertura baja y CTA para "reportar un problema de detección"
- Sin datos: estado vacío con instrucción para volver a escanear con más URLs

### Known issues

- OQ-009: Sin definir el umbral mínimo de cobertura que preserva la confianza

### How it should evolve

- Interactive component explorer (click para ver todas las instancias en el producto)
- Filtros y búsqueda en el UI kit
- Vista "official vs. unofficial" después de que el usuario haya tomado decisiones de officialization
- Modo comparación: UI kit del scan anterior vs. actual
