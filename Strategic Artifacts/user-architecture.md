---
artifact: user-architecture
version: 0.1
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
---

# User Architecture

## Purpose

Definir para quién está construido Schemaflow y qué señales deben guiar las decisiones de producto. Este artefacto es la fuente de verdad sobre el usuario — quién es, qué experimenta, cómo trabaja hoy, y por qué adoptaría una capa de governance.

## Primary User / ICP

[Needs Human Review] Schemaflow está en estado **pre-ICP**. El producto no sabe con certeza aún qué segmento comprará. El target actual debe tratarse como un **learning ICP**, no como una persona de compra validada. → OQ-002

**ICP de aprendizaje:** AI-native builders que ya tienen un producto real en movimiento, usan AI tools para generar o modificar UI, y están comenzando a experimentar la governance visual como un costo de tiempo recurrente.

Este segmento puede incluir: founder-builders, indie hackers avanzados, freelancers técnicos, builders de agencias pequeñas, product engineers, design engineers, y early startups con suficiente madurez de producto o presupuesto como para que la consistencia visual les importe.

**Tres sub-segmentos a distinguir:**

1. **Segmento de adquisición / aprendizaje:** builders AI-nativos lo suficientemente curiosos como para escanear su producto y ver su real UI kit. Alta adquisición; conversión a pago incierta.
2. **Segmento monetizable hipotético:** usuarios para quienes el drift visual tiene costo operacional — múltiples productos, trabajo de clientes, productos monetizados, interfaces brand-sensitive. Hipótesis del founder: "builders con productos serios y monetizables donde la consistencia visual importa." No validado. → OQ-002
3. **Segmento no-prioritario para pago:** personas experimentando con un MVP muy temprano, sin usuarios, sin monetización, sin costo real adjunto a la inconsistencia. Generan scans gratuitos; no deben guiar el roadmap.

**Objetivo estratégico:** comenzar con el segmento de aprendizaje amplio pero relevante, observar qué usuarios experimentan el dolor más fuerte y mayor WTP, y progresar hacia el ICP con mayor probabilidad de compra.

## Observable Signals

Las siguientes señales indican que un usuario es fit fuerte *ahora* — no solo que "le importa el diseño," sino que ya tiene el problema y está intentando resolverlo.

1. Usa AI coding tools regularmente (Cursor, Claude Code, Lovable, v0, Bolt, Replit, Figma AI, o similares) para crear o modificar UI/código
2. Tiene una superficie de producto real para escanear — URL pública, beta, dashboard, app interna, proyecto de cliente, o producto en producción
3. Hace cambios de UI repetidamente — genera screens, componentes, landing pages, flows, o cambios visuales de forma recurrente
4. Corrige manualmente inconsistencias visuales — pasa tiempo ajustando botones, fuentes, espaciados, colores, cards, inputs o variantes que el AI dejó "parecidos pero no iguales"
5. Usa prompts como workaround de control de diseño — instruye agentes con "hazlo consistente," "usa el mismo estilo," "sigue el design system," "arregla la UI"
6. Tiene más de un producto, cliente, o superficie que mantener — el pago es más probable cuando la inconsistencia es un costo operacional multi-proyecto
7. Ya paga por infraestructura de producto — Vercel, Supabase, AI tools, Figma, Linear, Cursor, Claude — señal de WTP si Schemaflow ahorra tiempo real
8. Tiene inconsistencia visible en el UI — múltiples estilos de botón, tipografía irregular, espaciados inconsistentes, componentes duplicados, CSS disperso
9. Expresa frustración alrededor del control, no solo la estética — "el AI lo hace rápido pero no puedo mantenerlo consistente," "ya no siento que sea mío," "cada chat cambia cosas"
10. Quiere outputs reusables por agentes — pide `design.md`, `ui-kit.md`, reglas, prompts, tokens, o instrucciones para que el agente no siga rompiendo el diseño

**La señal de fit más fuerte no es el gusto por el diseño — es el comportamiento repetido que revela que la governance visual se ha convertido en un costo de tiempo operacional.**

## Jobs / Needs / Frictions

**Tensión central:** el usuario quiere la velocidad del AI sin perder la autoría del producto.

Quiere generar, iterar y shippe más rápido, pero su workflow AI-nativo actual hace difícil preservar la consistencia visual, la intención de diseño, y el control entre screens, componentes, chats, e iteraciones.

El usuario no está bloqueado de producir UI. Está bloqueado de *confiar* en que la UI que produce permanecerá coherente.

**Tensión funcional:** el AI permite crear UI rápido, pero no preserva de forma confiable la consistencia entre cambios.

**Tensión emocional:** el producto puede funcionar, pero el usuario siente que ya no controla del todo cómo se ve. El producto empieza a sentirse menos "suyo."

**Tensión económica:** corregir inconsistencias visuales puede llevar más tiempo que construir funcionalidad — especialmente cuando el problema se repite cada semana o en múltiples productos.

**Línea de posicionamiento:** *AI los ayuda a construir más rápido, pero hace más difícil mantener el producto visualmente bajo control.*

## Workarounds

Los builders AI-nativos resuelven el drift visual hoy mediante corrección manual, prompting repetido, documentación ad hoc, copia de componentes, y comparación visual. Estos workarounds confirman que el problema existe porque los usuarios ya invierten tiempo intentando recuperar control — sin una herramienta de governance dedicada.

1. **Prompting repetido dentro del AI coding agent** — "hazlo consistente," "usa el mismo estilo de botón," "sigue el design system." El agente puede arreglar una pantalla mientras rompe otra o reinterpretar la instrucción de forma distinta en cada chat.
2. **Corrección visual manual en el código** — editar CSS, clases de Tailwind, archivos de componentes, o stylesheets para ajustar botones, inputs, espaciados, fuentes, cards, variantes. Convierte el problema en pérdida de tiempo medible.
3. **Copy-paste del "mejor" componente existente** — encontrar el componente que se ve mejor y copiarlo en otros lugares. Arregla inconsistencias locales pero no crea fuente de verdad ni previene drift futuro.
4. **Notas de diseño ad hoc** — Notion con los hex codes, README files, prompts, markdown files, comentarios en código. Desconectados del AI y del código real.
5. **Referencia de Figma / documentación de marca** — útil como fuente de intención pero requiere traducción manual a código AI-generado.
6. **Comparación de screenshots / eyeballing** — abrir pantallas side by side y comparar botones, fuentes, espaciados. No escala.
7. **Sesiones de cleanup one-off** — "ahora necesito arreglar la UI." Limpia la deuda acumulada pero no previene drift futuro.
8. **Refactor de componentes después del hecho** — cuando el drift se vuelve obvio, consolidar componentes o crear shared components. Mejora la calidad del código pero captura tarde la intención de diseño.

**La debilidad de todos estos workarounds:** son locales, manuales, y frágiles. Pueden arreglar una pantalla o componente pero no crean un contexto de diseño gobernado que el AI pueda reusar de forma confiable en iteraciones futuras.

## Adoption Logic

La adopción de Schemaflow no sigue la misma lógica para todos los usuarios. El producto puede atraer un amplio set de builders AI-nativos a través de un free scan, pero el uso regular y el pago probablemente vendrán de segmentos más estrechos donde el drift visual crea un costo operacional recurrente.

**Marco: Try → Return → Pay**

**Founder-builder AI-nativo**
- *Try:* quiere ver el estado real de su UI. El primer scan funciona como curiosity hook: "¿qué UI kit está produciendo realmente mi producto?"
- *Return:* vuelve si el scan revela problemas que reconoce y el segundo scan muestra progreso después de las correcciones.
- *Pay:* paga si ahorrar tiempo de corrección visual es más barato que arreglarlo manualmente — especialmente antes de lanzar, demos, fundraise, o crecimiento.

**Freelancer / solo builder con trabajo de cliente**
- *Try:* necesita entregar trabajo que se vea consistente sin pasar horas puliendo UI manualmente.
- *Return:* cada nuevo cliente/proyecto crea otra oportunidad de scan. Schemaflow puede volverse parte del delivery checklist.
- *Pay:* paga si Schemaflow reduce el retrabajo, mejora la calidad de entrega, y ayuda a presentar un producto más profesional.

**Agencia pequeña / studio**
- *Try:* administra varios productos o clientes y necesita detectar inconsistencias visuales rápidamente.
- *Return:* cada proyecto, sprint, o entrega puede requerir revisión visual.
- *Pay:* paga si Schemaflow estandariza el QA visual, reduce horas de revisión, y genera artefactos reusables para equipos o agentes AI.

**Early startup / equipo de producto con algo de presupuesto**
- *Try:* tiene suficiente superficie de producto para acumular deuda visual y quiere entender dónde existe la inconsistencia.
- *Return:* vuelve si Schemaflow se vuelve parte del ciclo de release o iteración — antes de releases, después de trabajo AI-assisted, o durante revisiones de consistencia.
- *Pay:* paga si Schemaflow reduce riesgo de calidad, acelera el desarrollo, y aumenta la confianza mientras el producto crece.

**Usuario exploratorio / free**
- *Try:* curiosidad y acceso de bajo costo de fricción.
- *Return:* solo si descubren un problema real y tienen un próximo cambio que validar.
- *Pay:* probablemente no pagan aún — a menos que su producto madure o lleguen a límites de valor.

**Resumen de lógica de adopción:**
- *Try:* "Quiero ver mi real UI kit."
- *Return:* "Quiero saber si mejoró o si se volvió a romper."
- *Pay:* "Me cuesta menos pagar que arreglar esto manualmente o arriesgar la calidad."

## Purchase Trigger

[Needs Human Review] El trigger de compra es actualmente una **hipótesis del founder, no un hecho validado externamente.** → OQ-001

**Hipótesis de compra:** el usuario alcanza un umbral de costo de tiempo visible — se da cuenta de que está gastando demasiado tiempo arreglando problemas visuales sin poder resolverlos de forma duradera. No es un evento discreto único; es el momento en que el dolor crónico se vuelve lo suficientemente costoso como para buscar una solución pagada.

**Triggers hipotéticos por segmento:**
- *Freelancers:* antes de una entrega de cliente donde la calidad visual afecta la aprobación o renovación
- *Startups:* antes de un lanzamiento, demo, o fundraise donde el producto necesita verse profesional
- *Builders maduros:* cuando el tiempo recurrente de corrección se vuelve más caro que el costo de la herramienta

**Principio de validación:** el trigger de compra no es "el usuario ve drift." Es cuando el usuario cree que la governance visual ahorra más tiempo, riesgo, o pérdida de calidad de lo que cuesta.

**Lo que falta:** validar empíricamente cuál de estos triggers produce la conversión más fuerte — esto es el objetivo central de Stage 1 con design partners.

## Exclusions

Los siguientes segmentos se excluyen en esta fase porque sus necesidades desplazarían el producto del core governance loop antes de que esté validado:

1. **Builders de MVP muy temprano sin producto real** — solo explorando una idea, sin UI real, sin usuarios, sin presión de calidad, sin costo adjunto a la inconsistencia. Pueden usar el free tier por curiosidad pero no deben guiar el roadmap.
2. **Usuarios que solo quieren inspiración o mejor gusto** — buscando hacer su diseño "más bonito" sin un producto que gobernar. Schemaflow no es un generador de diseño ni herramienta de inspiración.
3. **Equipos de design system enterprise con necesidades pesadas** — requieren permisos, roles, compliance, integraciones de Figma, Storybook, design tokens, approval workflows, audit trails, y colaboración multi-equipo. Optimizar para ellos prematuramente hace el producto pesado antes de probar el loop individual.
4. **Diseñadores desconectados de la implementación** — que operan solo en Figma o dirección de marca pero están desconectados del código, los agentes AI, o el producto vivo. Schemaflow vive en el gap entre diseño real, código real, e implementación AI-generada.
5. **Builders que aún no se preocupan por la consistencia visual** — aceptan inconsistencia como parte de un hackathon, exploración, o fase de validación temprana. Pueden convertirse en usuarios después, pero no deben definir decisiones de producto ahora.
6. **Usuarios que esperan un rediseño automático completo** — esperan que Schemaflow rediseñe todo el producto automáticamente. La tesis es governance, no "AI designer que crea una UI nueva desde cero."
7. **Equipos cuya necesidad principal es colaboración antes que valor individual** — roles, permisos, comentarios, aprobaciones, workflows multi-usuario. El producto debe probar valor individual antes de construir profundidad de colaboración de equipo.

**Exclusión estratégica central:** no construir para "cualquiera que hace UI con AI." Ese segmento es demasiado amplio y diluirá las decisiones de producto.

## Product Implications

Las siguientes implicaciones de producto se derivan directamente de la arquitectura de usuario:

**Del trigger de compra (costo de tiempo como umbral):** la propuesta de valor debe ser inmediatamente cuantificable en tiempo. El primer scan debe mostrar concretamente cuánto tiempo potencial se está perdiendo en correcciones manuales. No es suficiente mostrar que hay drift — debe quedar claro el costo.

**De los workarounds (prompting repetido, corrección manual):** el producto compite directamente con "pedir al AI que lo arregle." El output de Schemaflow debe ser más preciso y duradero que lo que el usuario obtiene de un prompt ad hoc. Los prompts de corrección deben tener valores exactos — no "hazlo consistente" sino "reemplaza `#3B2F8A` con `#4F3EAD` en estos componentes."

**De la lógica de adopción (curiosity hook → correction loop → re-scan):** el primer scan debe crear un aha moment observable en menos de 15 minutos. El re-scan debe ser de bajo costo de fricción — el usuario no debe tener que re-ingresar configuración, re-autenticar, o re-definir qué escanear.

**De las exclusiones (no enterprise, no early MVP):** el producto no debe requerir configuración de equipo, integración con herramientas de design system enterprise (Figma, Storybook, Zeplin), ni setup extenso antes de entregar el primer valor.

**De los segmentos monetizables (freelancers, multi-producto, pre-lanzamiento):** los límites del free tier deben estar donde estos segmentos necesitan ir — múltiples URLs, histórico de scans, exports AI-actionables persistentes, o scan autenticado.

## Open Questions

- OQ-001: ¿Cuál es el trigger específico de compra — qué evento concreto convierte awareness en purchase intent? Hipótesis: umbral de costo de tiempo visible.
- OQ-002: ¿Quién es el primer ICP monetizable — qué sub-segmento muestra WTP antes que los demás? Hipótesis: builders con productos serios y monetizables donde la consistencia visual importa.
