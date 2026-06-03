---
artifact: feature-design-context
version: 0.1
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
technical_reference: Technical Artifacts/features/feature-design-context.md
---

# Feature: Design Context

## What it does

Organiza y persiste las decisiones de diseño del usuario — componentes oficiales, reglas de uso, restricciones, y contexto visual — en un espacio estructurado y reusable. Este contexto es la fuente de verdad del producto del usuario: lo que Schemaflow genera como design context file para el AI, lo que el re-scan valida contra, y lo que persiste entre sesiones de trabajo. Es el módulo que da memoria al sistema visual del usuario.

## Why it exists

Sin persistencia, cada scan parte de cero y el usuario tiene que re-tomar las mismas decisiones. El design context es lo que convierte decisiones puntuales en un sistema gobernado — acumula las elecciones del usuario en algo duradero que el AI puede leer, que Schemaflow puede validar en re-scans, y que crece con el producto.

## Where it lives

`/project/[id]/design-context` — vista del design context acumulado del proyecto.

---

## Sub-feature: Project Workspace

### What it does

Agrupa todos los scans, decisiones de governance, exports, e historial de un producto/proyecto en un único espacio persistente. El usuario puede volver al proyecto días después y encontrar su sistema visual en el estado exacto en que lo dejó.

### Why it exists

La governance no puede existir sin persistencia. Si cada scan es aislado, el usuario no puede construir un sistema visual progresivamente. El project workspace es el contenedor que hace posible la governance a lo largo del tiempo.

### Where it lives

`/project/[id]` — dashboard del proyecto.

### How it is composed

- Nombre y URL del proyecto
- Lista de scans realizados con fecha, número de issues detectados, y estado de corrección
- Resumen del estado actual de governance (% de sistema gobernado, issues pendientes)
- Acceso al design context acumulado
- CTA principal: "Re-scan" o "Ver último scan"
- Acceso al historial de exports

### Who can use it

Todos los usuarios. El número de proyectos puede estar limitado en el free tier (ej. 1 proyecto en free, múltiples en paid).

### Rules

- El proyecto se crea automáticamente cuando el usuario hace el primer scan de un URL
- Las decisiones de officialization persisten en el proyecto y se aplican a todos los scans futuros
- El proyecto nunca elimina scans anteriores — se acumula el historial
- El usuario puede archivar un proyecto si ya no es relevante

### What happens when it fails or is empty

- Sin proyectos: estado vacío con CTA para crear el primer scan
- Sin scans en el proyecto: pantalla de onboarding del primer scan

### Known issues

- Ninguno adicional

### How it should evolve

- Multi-project dashboard (para usuarios con múltiples productos)
- Credenciales de acceso por proyecto (para authenticated scan)
- Project-level design rules (reglas que aplican a todos los scans del proyecto)
- Acceso de equipo al proyecto (colaboradores)
- Workspace compartido para agencias

---

## Sub-feature: Design Context Library

### What it does

Almacena las decisiones oficiales del usuario — componentes, variantes, valores, reglas de uso, restricciones — de forma estructurada y accesible. Es la librería del sistema visual gobernado del proyecto. El AI-actionable export (output tipo 2) se genera desde aquí.

### Why it exists

Schemaflow se vuelve defensible cuando tiene algo más que un scan — cuando tiene el contexto de diseño estructurado y persistente del producto del usuario. La design context library es ese repositorio: donde viven las decisiones confirmadas, los valores exactos, y las reglas que el AI debe respetar en cada sesión futura.

### Where it lives

`/project/[id]/design-context` — tab dentro del proyecto.

### How it is composed

- Secciones organizadas por tipo: Colors, Typography, Buttons, Inputs, Cards, Components, Spacing, Rules
- Por cada elemento oficial: valor exacto, nombre de referencia, regla de uso, contexto de por qué es el oficial
- Estado de cada elemento: activo / pendiente de revisión / deprecado
- Vista de "reglas generales": restricciones que aplican al sistema completo ("nunca usar texto blanco sobre fondos claros")
- Timestamp de última actualización por elemento
- Botón "Generar design context file" para exportar el estado actual como DESIGN.md o rules file

### Who can use it

Todos los usuarios con al menos una decisión de officialization. La versión completa puede requerir plan paid.

### Rules

- Solo contiene elementos confirmados por el usuario — nunca sugerencias no confirmadas de Schemaflow
- Los valores son exactos y copiables
- El usuario puede editar manualmente los valores o reglas si quiere ajustar algo fuera del flujo de scan
- Los cambios manuales se registran con un timestamp diferente para distinguirlos de los generados por scan
- La library es la fuente de verdad para el re-scan: Schemaflow valida el estado del producto contra lo que está en la library

### What happens when it fails or is empty

- Vacío: CTA para hacer el primer scan y tomar decisiones de governance
- Sin confirmaciones del usuario: la library muestra las sugerencias de Schemaflow como "pendientes de confirmar"

### Known issues

- Ninguno adicional

### How it should evolve

- Component ontology: relaciones entre componentes (el botón primario vive dentro de este card)
- Versioning: ver el historial de decisiones y cuándo cambiaron
- Design rules engine: reglas complejas ("el texto siempre es oscuro cuando el fondo tiene lightness > 50%")
- Reusable agent skills basadas en el design context
- Exportar como npm package o design token file (W3C format)
