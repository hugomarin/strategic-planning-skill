---
artifact: feature-ai-actionable-output
version: 0.1
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
technical_reference: Technical Artifacts/features/feature-ai-actionable-output.md
---

# Feature: AI-Actionable Output

## What it does

Genera los dos tipos de outputs AI-actionables del governance loop — uno para corregir el drift detectado hoy, otro para prevenir el drift en sesiones futuras. El usuario no necesita traducir manualmente el diagnóstico en instrucciones para su AI coding tool: Schemaflow lo hace por él, con valores exactos y acciones específicas.

## Why it exists

Es el diferenciador más fuerte del producto. Cualquier scanner puede decirle al usuario qué está mal. Schemaflow va más lejos: le dice exactamente qué cambiar, con qué valores, y le da el contexto para que su AI no lo vuelva a romper. Sin este módulo, el usuario tiene un diagnóstico pero no tiene la solución — y vuelve a hacer el trabajo manualmente.

## Where it lives

`/scan/[id]/export` — accesible después de que el usuario haya tomado decisiones de officialization.

---

## Sub-feature: Correction Prompts (Output Tipo 1 — Reparar)

### What it does

Genera prompts de corrección muy precisos con los valores exactos necesarios para arreglar el drift detectado. Cada prompt instruye al AI coding tool del usuario a hacer un cambio específico: qué componente, en qué archivo o página, qué valor debe reemplazar a qué otro valor. El usuario puede copiar el prompt y pegarlo directamente en Cursor, Claude, o su herramienta preferida.

### Why it exists

El trigger de compra hipotético es que el usuario está gastando demasiado tiempo arreglando problemas visuales sin poder resolverlos de forma duradera. Este output es la resolución directa de ese problema — convierte horas de corrección manual en instrucciones precisas que el AI puede ejecutar en segundos.

### Where it lives

`/scan/[id]/export/correction` — tab o sección dentro del export.

### How it is composed

- Por cada elemento marcado como "drift" por el usuario:
  - Prompt de corrección copiable con el valor exacto a cambiar y el valor oficial al que debe cambiar
  - Contexto de la corrección: qué tipo de elemento, en qué páginas aparece, cuántas instancias
  - Acción esperada clara: "Reemplaza `background: #3B2F8A` con `background: #4F3EAD` en el componente botón primario de estas páginas"
- Lista consolidada de todos los prompts de corrección del scan (uno por tipo de problema o por componente)
- Opción de "Copiar todo" para pasar todos los prompts de una vez al AI
- Opción de copiar prompt individual por item

### Who can use it

Todos los usuarios con al menos un elemento marcado como drift. El número de prompts exportables puede estar limitado en el free tier.

### Rules

- Los valores deben ser exactos y verificables — no "un azul más oscuro" sino "`#4F3EAD`"
- Cada prompt debe incluir suficiente contexto para que el AI entienda qué cambiar sin ambigüedad
- Los prompts son instrucciones, no sugerencias — deben estar formulados en imperativo
- Solo se generan prompts para elementos que el usuario marcó como drift (no para sugerencias de Schemaflow sin confirmar)
- Si el usuario no ha tomado decisiones de officialization, se puede generar una versión con las sugerencias de Schemaflow marcadas como tales

### What happens when it fails or is empty

- Sin elementos marcados como drift: CTA para ir a la drift analysis y marcar elementos
- Sin official element para comparar: advertencia de que se necesita marcar el elemento oficial antes de generar el prompt de corrección

### Known issues

- Ninguno adicional

### How it should evolve

- Cursor rules export (archivo `.cursorrules` con las correcciones estructuradas)
- Claude Code instructions (archivo de instrucciones compatible con Claude Code)
- Agrupación de prompts por tipo de corrección (todos los botones, toda la tipografía, etc.)
- Exportar como issue list de Linear o GitHub

---

## Sub-feature: Design Context File (Output Tipo 2 — Prevenir)

### What it does

Genera un design context file (DESIGN.md o rules file) que el usuario puede agregar a su proyecto para que su AI coding tool lo lea en cada sesión futura. El archivo contiene los componentes oficiales, los valores exactos, las reglas de uso, y las restricciones de diseño que el usuario definió durante la officialization — de forma que el AI no genere drift en nuevas iteraciones.

### Why it exists

Los prompts de corrección arreglan el pasado. El design context file protege el futuro. Sin este output, el usuario tiene que seguir re-escaneando y corrigiendo indefinidamente cada vez que el AI genera nueva UI. Con él, el AI tiene memoria persistente de las decisiones de diseño del usuario — previniendo el drift antes de que ocurra.

### Where it lives

`/scan/[id]/export/design-context` — tab o sección dentro del export, disponible después de officialization.

### How it is composed

- Archivo DESIGN.md o rules file generado automáticamente a partir de las decisiones de officialization del usuario
- Contiene: paleta de colores oficial con valores exactos, fuentes y tamaños tipográficos oficiales, componentes oficiales con sus variantes válidas, reglas de uso ("el botón primario siempre usa estos valores"), restricciones ("nunca usar estos colores para texto principal")
- Preview del archivo antes de descargarlo
- Instrucciones de uso: "Agrega este archivo a la raíz de tu proyecto y referéncialo en tu CLAUDE.md o `.cursorrules`"
- Opción de descarga directa + opción de copiar contenido
- Compatibilidad explícita indicada: Cursor, Claude Code, Lovable (según el formato generado)

### Who can use it

Todos los usuarios que hayan completado al menos una decisión de officialization. Puede requerir plan paid para el archivo completo (el free tier puede ofrecer una versión reducida o con watermark).

### Rules

- El archivo solo incluye elementos que el usuario confirmó como oficiales — nunca sugerencias de Schemaflow sin confirmar
- Los valores deben ser exactos y en el formato correcto para el tipo de archivo generado
- El archivo debe ser legible por humanos y por AI — no solo estructurado en JSON o YAML, sino con lenguaje natural que explique el propósito de cada regla
- El usuario debe poder editarlo después de descargarlo — no es un archivo generado one-time, es un punto de partida

### What happens when it fails or is empty

- Sin decisiones de officialization: CTA para completar el proceso de governance antes de generar el archivo
- Error de generación: retry + opción de contactar soporte

### Known issues

- Ninguno adicional

### How it should evolve

- Versiones de formato por herramienta: `.cursorrules` (Cursor), `CLAUDE.md` additions (Claude Code), Lovable-compatible format
- MCP-compatible context para integración directa con AI tools que soporten MCP
- Actualización incremental del design context file después de cada re-scan y officialization (no regenerar desde cero)
- Agent skills estructuradas para herramientas que las soporten
- Integración directa con el repositorio (crear PR con el archivo)
