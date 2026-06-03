---
artifact: product-thesis
version: 0.1
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
---

# Product Thesis

## Purpose

Capturar la apuesta central del producto y sus implicaciones. Este artefacto es la fuente de verdad para qué debe ser verdad para que Schemaflow funcione — y qué señales lo falsificarían.

## Central Thesis

Schemaflow apuesta a que, a medida que el AI acelera el desarrollo de interfaces, los builders perderán suficiente control visual a lo largo de las iteraciones como para adoptar una capa de governance dedicada que detecte drift, restaure coherencia, y mantenga el producto alineado con su intención de diseño.

**Counter-thesis explícita:** el drift visual es real pero tolerable — los builders prefieren velocidad sobre consistencia, o encuentran que corregir el AI con prompts ad hoc es suficientemente bueno. Si esto es verdad, no hay suficiente demanda para una capa de governance dedicada.

## Why This Thesis Matters

Los AI coding tools crearon una nueva clase de builder: alguien que puede shippe un producto completo sin saber diseño, pero que aun así tiene estándares visuales — "sabe lo que le gusta cuando lo ve." Este builder tiene un problema que no existía antes: la velocidad del AI supera su capacidad de mantener coherencia visual entre sesiones. No es un problema de skill de diseño; es un problema de memoria de diseño. Ninguna herramienta existente está construida para este builder en este momento del ciclo de desarrollo.

## Non-obvious Belief

El mercado está confundiendo generación de AI con governance de AI. Generar no es gobernar.

Las herramientas actuales optimizan para generar UI más rápido. Schemaflow apuesta a que la siguiente capa necesaria no es más velocidad de generación — es control sobre lo que el AI ya generó. El incumbente que más se acerca (Tokens Studio) está construido para diseñadores que trabajan en Figma. Los AI coding tools gatan consistency features detrás de Enterprise. Nadie está construyendo la capa de governance para el builder individual que construye con AI.

La creencia no-obvia: el problema no es que los builders tengan poco skill de diseño. Es que el AI no tiene memoria de diseño entre sesiones — y eso es un problema de tooling, no de educación.

## Assumptions

Las siguientes suposiciones deben ser verdaderas para que la tesis funcione. Cada una puede fallar.

1. Los builders AI-nativos con productos reales experimentan drift visual de forma recurrente y acumulativa — no como un problema puntual que se resuelve una vez.
2. Los builders tienen estándares visuales propios aunque no sepan diseño formal — "saben lo que quieren" aunque no puedan articularlo en términos de tokens o design systems.
3. El costo de tiempo de corregir drift manualmente eventualmente supera el umbral donde un builder busca una solución dedicada.
4. Los builders confiarán en un diagnóstico generado por AI si está expresado con suficiente especificidad y trazabilidad (observado vs. inferido vs. recomendado).
5. Mantener buen diseño a través de iteraciones AI-assisted seguirá siendo difícil sin una capa de control dedicada — el problema no se resuelve solo con mejores prompts.
6. El design context file generado por Schemaflow reducirá el drift en sesiones futuras de forma observable — el AI leerá el contexto y lo respetará.
7. Los builders que experimentan el beneficio del governance loop lo suficientemente claro pagarán por él.
8. El segmento que paga será más estrecho que el segmento que usa: usuarios con productos maduros, múltiples proyectos, trabajo de clientes, o suficiente sensibilidad visual para que la consistencia tenga impacto económico directo.
9. Schemaflow puede extraer un UI kit real y confiable del producto existente del usuario — suficientemente preciso como para que el diagnóstico sea accionable.
10. La re-escaneabilidad (volver después de corregir para verificar mejora) es un comportamiento natural para este usuario, no algo que haya que enseñar.

## Evidence

[Needs Human Review] La evidencia actual es temprana y cualitativa. El dolor existe pero aparece más como incomodidad recurrente que como categoría de mercado plenamente validada. Se necesita evidencia externa (entrevistas, datos de comportamiento de no-founders) para elevar la certeza. → OQ-004

**Señales con trazabilidad:**
- Workarounds documentados y prevalentes: Notion con hex codes, screenshots pegados al inicio de sesiones, preambles largos que el AI ignora o reinterpreta. Fuente: `ai-design-consistency-new-creative.md`, `JTBD-new-creative-segment.md`
- MindStudio research: "Silence in your design system = Claude defaults." Evidencia directa de que el AI sin contexto produce resultados inconsistentes. Fuente: `ai-design-consistency-new-creative.md`
- Lovable, v0, Bolt gatan design system consistency detrás de Enterprise — validación indirecta de que el problema es real y percibido como valioso. Fuente: `ai-design-consistency-new-creative.md`
- No existe producto que cierre el loop scan → correct → prevent → re-scan para el builder individual. El cuadrante competitivo está vacío. Fuente: `strategy-and-competitive-analysis.md`
- Evidencia founder: alinear un botón, switch, o fuente puede tomar más tiempo que construir un feature de backend completo — el costo de tiempo es real y desproporcionado. Fuente: `Schemaflow Product Thesis.md`
- Señales de colaboradores informales y contexto de comunidades de builders (Indie Hackers, HN, foros de Cursor). No estructuradas. Fuente: `ai-design-consistency-new-creative.md`, `Strategic Analysis Document.md`

**Lo que falta:** entrevistas con usuarios no-founders, datos de comportamiento observados externamente, alguna señal de WTP de usuarios reales.

## Challenge / Counterargument

El contraargumento más fuerte no es que el problema no exista — es que puede no ser urgente ni monetizable en escala:

*"El drift visual es real, pero 70-80% bueno es suficientemente bueno para la mayoría de builders en etapa temprana. El costo de tolerarlo es menor que el costo de gestionarlo. Los builders que realmente tienen estándares altos contratan un diseñador o aprender a usar Figma. El segmento que pagaría por una herramienta de governance visual es demasiado estrecho para construir un negocio sostenible."*

Este contraargumento se fortalece si: (a) los design partners no exhiben comportamiento de re-scan espontáneo, (b) los usuarios encuentran suficiente con los prompts de corrección sin el design context file, o (c) el ICP monetizable resulta ser más estrecho de lo anticipado.

## Falsification Risks

Las siguientes señales indicarían que la tesis es débil o falsa:

1. **Los usuarios reconocen el drift pero no lo corrigen:** completan el primer scan, ven el diagnóstico, y no toman ninguna acción. Interpretan el problema como "interesante" pero no como urgente.
2. **Los usuarios completan el scan pero no regresan:** usan Schemaflow como diagnóstico puntual, no como workflow recurrente. El re-scan no ocurre espontáneamente.
3. **Los usuarios prefieren corregir directamente al AI:** en lugar de usar los prompts de Schemaflow, prefieren pedir al AI "hazlo consistente" y aceptar el resultado aproximado. La precisión de Schemaflow no justifica el esfuerzo de correr el scan.
4. **El design context file no reduce el drift observable:** el AI lee el contexto pero lo interpreta de formas distintas en cada sesión — el problema persiste. La prevención no funciona.
5. **Los AI coding tools absorben el workflow nativamente:** Cursor, Claude Code, o Lovable integran governance de diseño para todos los tiers — el espacio de mercado desaparece antes de que Schemaflow alcance masa crítica.

## Product Implications

La tesis impone las siguientes restricciones al producto:

**El loop completo es la unidad mínima de valor:** scan → diagnose → correct → officialize → prevent → re-scan. Un producto que solo hace scan y diagnóstico entrega valor informativo, no governance. Sin el output de corrección y sin el re-scan, la tesis no está siendo validada.

**Dos outputs AI-actionables del mismo loop:**
- *Corrección:* prompts precisos con valores exactos para arreglar el drift detectado — "reemplaza `color: #3B82F6` con `color: #4F3EAD` en los botones de estas páginas." Ejecutable directamente o pasable al AI coding tool del usuario.
- *Prevención:* design context file (DESIGN.md / rules file) generado durante la officialization — le dice al AI del usuario cómo construir en futuras sesiones, preservando las decisiones de diseño sin repetición.

**Velocidad de governance < velocidad de corrección manual:** si arreglar drift con Schemaflow tarda más que editarlo a mano, el usuario abandona. La velocidad del loop es una restricción de producto, no una aspiración.

**Especificidad observable:** el diagnóstico debe distinguir siempre entre lo que Schemaflow observó directamente, lo que infirió, y lo que recomienda. Nunca presentar una inferencia como un hecho observado.

**Sin terminología de design system:** el usuario nunca debe necesitar saber qué es un "token", una "variable de Figma", o un "design system". Si el producto requiere este vocabulario, rompe el principio de zero-craft entry.

## Roadmap Implications

La tesis impone la siguiente secuencia de build — cada step es prerequisito del siguiente:

1. **Extraer UI kit real del producto existente** — sin esto, no hay diagnóstico confiable y no hay nada que gobernar
2. **Detectar drift y mostrarlo de forma comprensible** — sin esto, el usuario no puede tomar acción
3. **Permitir que el usuario defina qué es oficial** — sin esto, los outputs de corrección no tienen una fuente de verdad
4. **Generar prompts de corrección con valores exactos** — el output que convierte el diagnóstico en acción
5. **Generar design context file** — el output que convierte la governance en prevención futura
6. **Cerrar el loop con re-scan** — la señal de que el producto funciona y la mecánica de retención
7. **Persistencia y diseño entre scans** — valor adicional una vez que el loop básico está validado
8. **Design intelligence** — capa adicional de valor una vez que el producto tiene suficiente datos

**No construir paso N+1 antes de que paso N esté validado con usuarios reales.** El riesgo de construir rápido sin validación es que el loop completo falle en un punto que no es obvio desde el product design.

## Validation Needs

Lo que elevaría o debilitaría la certeza en la tesis:

**Elevaría la certeza:**
- Design partners que completan el re-scan espontáneamente después de corregir
- Usuarios que reportan que sus AI sessions generan menos drift después de usar el design context file
- Builders que pagan sin ser empujados explícitamente (pull, no push)
- Evidencia de que el trigger de compra es predecible y targeteable

**Debilitaría la certeza:**
- Design partners que usan el diagnóstico pero no los prompts de corrección
- Re-scan no ocurre espontáneamente en los primeros 5–10 design partners
- Usuarios que reportan que el AI no respeta el design context file de forma consistente
- Ningún design partner está dispuesto a pagar, aunque el producto funcione
