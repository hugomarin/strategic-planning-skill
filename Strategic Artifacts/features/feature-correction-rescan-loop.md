---
artifact: feature-correction-rescan-loop
version: 0.1
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
technical_reference: Technical Artifacts/features/feature-correction-rescan-loop.md
---

# Feature: Correction & Re-scan Loop

## What it does

Guía al usuario a través del proceso de corrección — desde entender qué corregir hasta ejecutarlo — y le permite volver a escanear el producto después para verificar que las correcciones funcionaron. El re-scan compara el estado actual contra el anterior, muestra el progreso, y detecta si apareció nuevo drift. Es el módulo que convierte a Schemaflow de una herramienta de diagnóstico en un workflow de governance recurrente.

## Why it exists

El primer scan crea awareness. El re-scan crea retention. Si el usuario escanea, ve los problemas, corrige, y puede verificar que mejoró, vuelve. Si no puede cerrar el loop — si no sabe si sus correcciones funcionaron — no tiene razón para volver. Este módulo es la mecánica de retención del producto.

## Where it lives

`/scan/[id]/correction` para el workflow de corrección. `/project/[id]/rescan` o botón "Re-scan" en el dashboard del proyecto.

---

## Sub-feature: Action Clarity / Recommended Fixes

### What it does

Organiza los hallazgos de drift en una lista de acciones priorizadas — qué corregir primero, por qué, y cómo. Cada item tiene una acción clara: oficializar, consolidar, corregir con el prompt generado, o ignorar intencionalmente. El usuario no necesita interpretar el diagnóstico — recibe instrucciones directas.

### Why it exists

Un diagnóstico sin path de acción claro aumenta la ansiedad y el trabajo. El usuario ya sabe que tiene drift — lo que necesita saber es qué hacer primero. Sin este sub-feature, el scan es una lista de problemas sin prioridad.

### Where it lives

`/scan/[id]/correction` — vista de acciones recomendadas.

### How it is composed

- Lista de issues ordenados por tipo e importancia aproximada
- Por cada issue:
  - Descripción en lenguaje claro: "Tienes 5 variantes del botón primario"
  - Acción recomendada: "Officializa el más frecuente y corrige los demás con este prompt"
  - El prompt de corrección copiable con valores exactos
  - Estado: pendiente / en progreso / resuelto / ignorado
- Vista de progreso: X issues resueltos de Y totales
- Filtros: por tipo, por estado, por prioridad

### Who can use it

Todos los usuarios.

### Rules

- Cada issue debe tener exactamente una acción recomendada por defecto — el usuario puede cambiarla
- Los prompts de corrección en esta vista son los mismos que en el export — consistencia obligatoria
- El usuario puede marcar un issue como "resuelto" manualmente (sin re-scan) o puede dejarlo para que el re-scan lo confirme automáticamente
- La vista no debe abrumar — si hay más de 10 issues, agrupar por tipo y mostrar un resumen colapsable

### What happens when it fails or is empty

- Sin drift: "Tu producto está bien. Consideramos agregarle más páginas al scan para una cobertura mayor."
- Sin decisiones de officialization: CTA para completar governance antes de ver las correcciones

### Known issues

- Ninguno adicional

### How it should evolve

- Priority / impact scoring automático por issue
- Estimated effort por corrección
- Batch actions: "corregir todos los issues de este tipo a la vez"
- "Fix with agent" flow: integración directa con Cursor o Claude

---

## Sub-feature: Re-scan

### What it does

Permite al usuario ejecutar un nuevo scan del mismo producto/proyecto después de haber hecho correcciones. El re-scan captura el estado actual del producto y lo compara automáticamente con el scan anterior.

### Why it exists

El re-scan es la señal de retención más importante del producto. Un usuario que vuelve a escanear después de corregir ha validado que el governance loop funciona para él. Sin el re-scan, Schemaflow es una herramienta de diagnóstico puntual — con él, es un workflow de governance.

### Where it lives

Botón "Re-scan" prominente en el dashboard del proyecto y en la vista de scan completado.

### How it is composed

- Botón "Re-scan" o "Run new scan" en el dashboard del proyecto
- Las URLs del proyecto se recuerdan automáticamente — el usuario no tiene que re-ingresarlas
- Configuración heredada del scan anterior (modo de acceso, páginas, etc.)
- Feedback de progreso durante el scan
- Al completar: redirige automáticamente a la vista de comparación

### Who can use it

Todos los usuarios. El número de re-scans puede estar limitado en el free tier.

### Rules

- El re-scan usa las mismas URLs que el scan anterior por defecto — el usuario puede agregar o quitar URLs
- El re-scan preserva todas las decisiones de officialization del usuario (no las borra)
- Si el usuario agrega nuevas páginas al re-scan, los nuevos elementos se analizan contra el sistema ya oficializado
- El re-scan genera una nueva versión del scan, no sobreescribe el anterior

### What happens when it fails or is empty

- Error durante el re-scan: notificación + opción de reintentar, el scan anterior permanece disponible
- Sin scans previos: no disponible — CTA para hacer el primer scan

### Known issues

- Ninguno adicional

### How it should evolve

- Scans programados (post-deploy, diarios, semanales)
- Scan automático después de detectar cambios en el repositorio (integración con GitHub)
- Regression alerts: notificar si el re-scan detecta nuevo drift en elementos previamente corregidos

---

## Sub-feature: Improvement Comparison

### What it does

Compara el estado del re-scan con el scan anterior y muestra el progreso de forma clara — qué drift fue corregido, qué sigue pendiente, y si apareció drift nuevo. Le da al usuario evidencia visible de que Schemaflow lo ayudó a mejorar.

### Why it exists

El usuario necesita ver que su trabajo de corrección funcionó. "El número de inconsistencias bajó de 18 a 7" es un dato concreto que justifica haber usado Schemaflow — y que motiva el siguiente re-scan. Sin comparación visible, el re-scan es solo otro reporte sin contexto.

### Where it lives

`/scan/[id]/comparison` — vista automática después de completar el re-scan.

### How it is composed

- Resumen de comparación: inconsistencias resueltas / pendientes / nuevas
- Lista de issues resueltos (marcados visualmente como "corregido")
- Lista de issues que permanecen (con su estado actual)
- Lista de nuevos issues detectados (si el AI generó drift nuevo)
- Métrica de progreso simple: "Resolviste 11 de 18 inconsistencias"
- CTA para continuar con los issues pendientes

### Who can use it

Todos los usuarios que hayan completado al menos un re-scan.

### Rules

- La comparación es siempre con el scan inmediatamente anterior (no con el primero)
- Un issue se considera "resuelto" cuando ya no aparece en el re-scan con la misma clasificación
- Los nuevos issues se muestran con énfasis diferente para que el usuario entienda que son regresiones, no items que Schemaflow "no había encontrado antes"
- El progreso nunca debe mostrarse como 100% a menos que realmente no haya drift detectado

### What happens when it fails or is empty

- Sin scan anterior para comparar: mostrar el scan solo como vista normal
- Sin mejoras detectadas: mostrar igual — "el drift no cambió significativamente"

### Known issues

- Ninguno adicional

### How it should evolve

- Visual diffs: ver exactamente qué cambió en el componente entre scans
- Governance score histórico (línea de tiempo de la salud visual del producto)
- Component-level improvement history
- "Streak" o tracking de cuántos scans consecutivos mejoraron
