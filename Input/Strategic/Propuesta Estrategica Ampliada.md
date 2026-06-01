# Propuesta estratégica ampliada para SchemaFlow

## 1. Objetivo del documento

Este documento consolida una lectura estratégica de SchemaFlow a partir de cinco capas:

- ICP inicial y posibles buyer personas.

- Jobs To Be Done funcionales, sociales y emocionales.

- Ciclo de vida del usuario: adquisición, activación y retención.

- Mapa competitivo por momento del trabajo.

- Recomendaciones para construir una propuesta de producto más robusta.

La intención es ordenar una tesis clara sobre dónde puede existir SchemaFlow, para quién, contra qué alternativas compite y qué tipo de producto debería priorizar.

## 2. Tesis central

SchemaFlow puede entenderse como una capa de **design memory for AI-built products**.

Dicho en el lenguaje de la propuesta actual: si el problema de fondo es el **aesthetic drift at AI generation speed**, la oportunidad de SchemaFlow es crear una capa que preserve continuidad visual entre prompts, agentes, sesiones, componentes y cambios de producto.

El problema no es solamente que los usuarios necesiten un design system. El problema es que los procesos actuales de construcción con AI todavía no tienen suficiente gobernabilidad visual.

Cuando un usuario delega diseño o implementación a un agente, también delega parte del control sobre la identidad visual del producto. Incluso un diseñador con alto craft puede perder gobernabilidad si cada agente interpreta el sistema desde cero.

Por eso el problema no debe formularse como una carencia del usuario, sino como una limitación de las herramientas y procesos actuales.

La oportunidad de SchemaFlow es convertir una UI existente en contexto reutilizable por humanos y agentes:

- UI Kit.

- [Design.md](http://Design.md).

- Agent instructions.

- Reglas visuales.

- Criterios de consistencia.

- Detección de drift.

- Versionado de identidad visual.

Formulación simple:

> Tu producto ya tiene un lenguaje visual. SchemaFlow lo extrae, lo ordena y se lo entrega a tus agentes para que no lo rompan.

## 3. Coincidencias de la propuesta actual

La propuesta actual acierta en varios puntos importantes:

- El problema de fondo es el **aesthetic drift** en productos construidos con AI.

- El usuario siente el problema antes de poder diagnosticarlo técnicamente.

- La velocidad de generación aumenta la probabilidad de inconsistencia.

- La categoría de herramientas actual está fragmentada.

- Las soluciones existentes resuelven partes del flujo, pero no la continuidad completa.

- El job emocional no es solo “que se vea bien”, sino recuperar control creativo.

- La consistencia visual se vuelve más difícil cuando el producto pasa entre sesiones, agentes, modelos o colaboradores.

La intuición más fuerte es esta:

> El usuario no solo quiere producir UI. Quiere confiar en que lo que produce hoy sigue perteneciendo al mismo sistema que lo que produjo ayer.

## 4. Ajustes recomendados de framing

### 4.1. No plantear el problema como falta de craft

El framing “High Taste, Low Craft” ayuda a identificar un segmento, pero puede reducir demasiado el problema.

El dolor no aparece solo porque el usuario no sepa diseñar. Aparece porque el proceso de construcción con AI introduce una nueva pérdida de gobernabilidad.

Incluso usuarios con alto criterio visual pueden enfrentar el mismo problema:

- Founder técnico con buen ojo de producto.

- Diseñador que usa AI para acelerar implementación.

- Builder avanzado que trabaja con agentes.

- Agencia pequeña que entrega productos con AI.

- Product designer sin equipo de design ops.

- Equipo pequeño que construye rápido y cambia de contexto constantemente.

El problema no es falta de capacidad. Es falta de una infraestructura ligera para convertir decisiones visuales en contexto operativo heredable.

Mejor formulación:

> AI-native builders who need design continuity across agents, sessions and product changes.

O:

> Builders que crean con AI y necesitan preservar identidad visual sin construir un sistema enterprise de diseño.

### 4.2. Organizar la estrategia por ciclo de vida

Más que separar únicamente “visión de largo plazo” y “wedge inicial”, conviene mirar la estrategia según el ciclo de vida del usuario.

Lo que sirve para adquirir usuarios no necesariamente sirve para activarlos o retenerlos.

SchemaFlow puede tener una visión amplia sin obligar a que el primer producto comunique toda esa ambición.

Adquisición

Promesa simple y concreta:

> Convierte tu UI existente en un UI Kit y [Design.md](http://Design.md) para seguir construyendo con AI.

Aquí el usuario debe entender el valor en segundos.

Activación

Momento de valor:

> El usuario ve que SchemaFlow entendió su producto mejor que un prompt genérico con screenshots.

Outputs clave:

- UI Kit claro.

- Reglas visuales útiles.

- Agent instructions accionables.

- Detección inicial de inconsistencias.

Retención

Promesa recurrente:

> Cada vez que tu producto cambia, SchemaFlow mantiene viva la memoria visual y detecta drift.

Aquí aparece el valor del versionado, estándares internos, historial de decisiones, comparaciones y reglas propias del proyecto.

### 4.3. Pensar el estándar como estrategia de mercado, no como mensaje inicial

Crear un estándar puede ser importante, pero no necesariamente como primer mensaje comercial.

La idea de un formato AI-native de identidad visual puede generar:

- Lock-in positivo.

- Switching costs.

- Portabilidad entre agentes.

- Posicionamiento de categoría.

- Integraciones futuras.

- Efecto de estándar si otros agentes o herramientas lo adoptan.

Pero el usuario inicial no compra “un estándar”. Compra una solución inmediata:

> Dame la URL de mi app y devuélveme contexto visual útil para seguir construyendo con AI.

La estrategia puede ser:

- Adquirir por utilidad inmediata.

- Activar por calidad del análisis.

- Retener por memoria, versionado y formato propio.

- Expandir por integraciones y estándares.

## 5. ICP inicial

### ICP de entrada

El ICP inicial recomendado no debe entenderse como el ICP final del producto, sino como el mejor segmento para entrar, aprender, adquirir usuarios con baja fricción y validar recurrencia.

**AI-native product builders que ya están construyendo una interfaz real y sienten que el diseño empieza a perder coherencia.**

No son usuarios que apenas quieren imaginar una idea. Ya tienen algo construido o en proceso.

Tienen suficiente sensibilidad visual para notar inconsistencias, pero no necesariamente tienen una capa formal de design ops.

### Por qué este ICP sirve para entrar

- Tiene dolor inmediato.

- Usa herramientas AI-native.

- Ya tiene una superficie visual para analizar.

- No requiere ventas enterprise.

- Puede activar rápido si el output es útil.

- Permite aprender qué artefactos realmente usa el usuario.

- Puede evolucionar hacia uso recurrente si el producto detecta drift y versiona cambios.

### Señales del ICP

- Construyen con Cursor, Claude Code, Lovable, v0, Bolt, Replit, Windsurf u otras herramientas AI-native.

- Ya tienen varias pantallas, componentes o flujos.

- Iteran rápido.

- El producto empieza a mezclar estilos.

- Les cuesta mantener una estética consistente entre sesiones.

- No quieren construir un design system enterprise.

- Necesitan algo ligero, inmediato y accionable.

- Valoran que el producto “se sienta propio”.

### Exclusiones iniciales

SchemaFlow no debería enfocarse inicialmente en:

- Empresas con design systems maduros y equipos completos de design ops.

- Usuarios que solo quieren generar landing pages desde cero.

- Diseñadores que viven exclusivamente dentro de Figma y no construyen con agentes.

- Equipos que ya tienen pipelines robustos de tokens, Storybook, visual regression y governance.

- Usuarios sin producto existente o sin suficiente superficie visual para analizar.

Estas exclusiones son estratégicas, no permanentes. Algunos segmentos pueden volverse relevantes en fases posteriores.

## 6. Buyer personas posibles

### 6.1. Founder / indie hacker AI-native

Quiere lanzar rápido, pero teme que el producto se vea genérico o inconsistente.

Dolor principal:

- La AI produce rápido, pero cada parte parece de una app distinta.

Compra porque:

- Necesita verse serio sin contratar diseñador.

- Quiere preservar identidad mientras crece el producto.

- Necesita contexto visual reutilizable para seguir iterando.

### 6.2. Diseñador-builder

Tiene gusto visual y criterio, pero usa AI para acelerar implementación.

Dolor principal:

- La AI no preserva suficientemente la intención estética.

Compra porque:

- Quiere convertir su criterio visual en reglas que el agente pueda heredar.

- Quiere revisar drift sin hacerlo todo manualmente.

- Quiere cerrar la brecha entre sensibilidad estética y ejecución técnica.

### 6.3. Developer con sensibilidad de producto

Puede construir, pero no quiere mantener manualmente una capa de diseño.

Dolor principal:

- El código crece, los estilos se duplican y la UI pierde consistencia.

Compra porque:

- Necesita una auditoría visual rápida.

- Quiere instrucciones concretas para el agente.

- Quiere evitar deuda visual.

### 6.4. Agencia pequeña / estudio boutique

Construye productos o sitios para clientes con ayuda de AI.

Dolor principal:

- Cada proyecto necesita mantener identidad, pero el ritmo de producción dificulta la consistencia.

Compra porque:

- Puede usar SchemaFlow como parte de su proceso de entrega.

- Le permite documentar identidad visual sin crear un sistema pesado.

- Puede entregar artefactos más profesionales al cliente.

## 7. Jobs To Be Done principales

La propuesta actual distingue bien tres niveles de job: funcional, social y emocional. Conviene mantener esa estructura y conectarla con momentos concretos del workflow.

### Functional Job

> Construir y extender una UI consistente entre páginas, sesiones y componentes generados con AI sin explicar la estética desde cero cada vez.

Sub-jobs:

- Extraer el lenguaje visual de una app existente.

- Formalizar colores, tipografía, spacing, componentes y patrones.

- Convertir ese lenguaje en instrucciones para agentes.

- Detectar cuándo una nueva pantalla o componente se desvía.

- Facilitar handoff entre agentes, colaboradores o sesiones.

### Social Job

> Parecer alguien con intención visual, no alguien que simplemente “vibe-coded” una interfaz genérica.

Sub-jobs:

- Evitar el look AI-generated.

- Transmitir cuidado y criterio.

- Mantener identidad reconocible.

- Presentar un producto más serio frente a usuarios, clientes o inversionistas.

### Emotional Job

> Confiar en que el producto mantiene una identidad coherente mientras evoluciona.

Sub-jobs:

- Sentir control creativo.

- Reducir ansiedad por inconsistencia.

- Saber que los cambios futuros pertenecen al mismo sistema.

- Evitar sentirse pasajero dentro del propio producto.

## 8. Mapa JTBD × competencia

La competencia debe mapearse por momento del trabajo, no solo por categoría. Esto ayuda a distinguir dónde SchemaFlow compite fuerte, dónde compite parcialmente y dónde conviene integrarse.

Escala:

- **Alta**: competencia directa o sustituto fuerte.

- **Media**: solapa parcialmente.

- **Baja**: alternativa indirecta.

- **No foco**: zona que no conviene atacar al inicio.

- **Oportunidad SF**: zona donde SchemaFlow debería concentrarse.

| Momento / JTBD | AI UI generatorsv0, Lovable, Bolt | AI coding agentsCursor, Claude Code | Extraction [toolsgetdesign.md](http://toolsgetdesign.md), screenshots | Figma / Dev Mode | Tokens / Specify | Visual regressionChromatic, Percy | Docs / GovernanceZeroheight, Backlight | Oportunidad para SchemaFlow |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1\. Crear UI desde cero | Alta | Media | Baja | Baja | Baja | Baja | Baja | No competir frontalmente; integrarse después de la generación |
| 2\. Extraer lenguaje visual de UI existente | Baja | Media | Alta | Media | Media | Baja | Media | **Oportunidad SF: extracción + interpretación + artefactos AI-readable** |
| 3\. Convertir diseño en contexto para agentes | Baja | Media | Media | Baja | Media | Baja | Baja | **Oportunidad SF: agent instructions, [Design.md](http://Design.md), reglas de estilo** |
| 4\. Construir nuevas pantallas sin perder identidad | Alta | Alta | Media | Media | Media | Baja | Baja | **Oportunidad SF: contexto reutilizable para generación consistente** |
| 5\. Detectar drift estético | Baja | Baja | Media | Baja | Media | Alta | Baja | **Oportunidad SF: coherencia estética, no solo visual diff** |
| 6\. Handoff entre agentes, devs o colaboradores | Baja | Media | Media | Alta | Media | Baja | Media | **Oportunidad SF: memoria portable y ejecutable** |
| 7\. Versionar evolución visual | Baja | Baja | Baja | Media | Media | Media | Alta | Fase posterior: visual history, decisiones y cambios |
| 8\. Gobernanza enterprise | Baja | Baja | Baja | Alta | Alta | Alta | Alta | No foco inicial; expansión futura |

## 9. Lectura estratégica del mapa

### Dónde competimos fuerte

SchemaFlow compite con fuerza en los momentos donde el usuario necesita:

- Extraer el lenguaje visual de una app existente.

- Convertir diseño real en artefactos reutilizables por agentes.

- Darle contexto visual a herramientas como Claude Code, Cursor, v0 o Lovable.

- Evitar que nuevas generaciones rompan coherencia.

- Revisar si una nueva pantalla pertenece al sistema.

- Mantener continuidad entre sesiones de AI.

Competencia cercana:

- [getdesign.md](http://getdesign.md).

- Herramientas screenshot-to-design-system.

- Prompts/manual workflows para generar [DESIGN.md](http://DESIGN.md).

- Auditorías manuales de UI.

- Flujos caseros con screenshots + Claude/Cursor.

### Dónde competimos parcialmente

SchemaFlow toca, pero no reemplaza completamente:

- Figma.

- Tokens Studio.

- Specify.

- Zeroheight.

- Figma Dev Mode.

- Storybook.

- Chromatic.

- Percy.

Estas herramientas resuelven partes del sistema visual, pero están diseñadas para otros workflows:

- Diseño humano → desarrollo.

- Tokens → código.

- Componentes → documentación.

- Screenshots → regresión visual.

- Design systems enterprise → governance.

SchemaFlow puede convivir con ellas porque su centro es diferente:

> Diseño existente → memoria operativa para agentes.

### Dónde no conviene competir al inicio

SchemaFlow no debería iniciar compitiendo frontalmente en:

- Generación completa de UI desde cero.

- Figma replacement.

- Token management avanzado.

- Visual regression testing tradicional.

- Enterprise design system governance.

- Documentación de design systems para grandes organizaciones.

- Component libraries completas.

Estas zonas tienen competidores fuertes, workflows establecidos o requerimientos pesados.

## 10. Ciclo de vida: JTBD → funcionalidades → comunicación

La estrategia puede ordenarse mejor si cada fase del ciclo de vida tiene sus propios jobs, funcionalidades y mensajes.

| Ciclo de vida | Job principal | Funcionalidades clave | Mensaje recomendado |
| --- | --- | --- | --- |
| Adquisición | Entender qué lenguaje visual tiene mi app | URL scan, screenshot analysis, UI Kit preview | “Turn your existing UI into an AI-readable design system.” |
| Activación | Ver valor útil en minutos | UI Kit, [Design.md](http://Design.md), agent instructions, inconsistencias detectadas | “Your AI agents can now build in your product’s visual language.” |
| Retención | Mantener consistencia mientras el producto cambia | Re-scan, drift detection, version history, project rules | “Keep every AI-generated change consistent with your product.” |
| Expansión | Integrar memoria visual al workflow completo | Cursor/Claude Code integrations, Figma export, tokens, team workflows | “Design memory across your AI product workflow.” |
| Lock-in estratégico | Convertir el formato en infraestructura propia | SchemaFlow format, project history, custom rules, governance layer | “A living design memory your team and agents can inherit.” |

## 11. Sinergias posibles

SchemaFlow puede ser una capa intermedia entre herramientas ya existentes.

### Con AI coding tools

- Cursor.

- Claude Code.

- Windsurf.

- Replit.

- Lovable.

- v0.

SchemaFlow puede generar instrucciones, reglas y contexto visual para estas herramientas.

### Con Figma

No necesita reemplazar Figma.

Puede:

- Importar referencias.

- Exportar tokens o documentación.

- Comparar UI real contra diseño esperado.

- Servir a usuarios que no tienen Figma ordenado.

### Con visual regression tools

Chromatic y Percy detectan diferencias visuales.

SchemaFlow puede detectar otra cosa:

- Incoherencia con el lenguaje visual.

- Drift estético.

- Desviación semántica de estilo.

- Ruptura de intención visual.

### Con documentación

Zeroheight y similares documentan sistemas para equipos.

SchemaFlow puede documentar sistemas para agentes.

## 12. Recomendaciones estratégicas

### 12.1. Priorizar el job de extracción operativa para adquisición

El primer producto debería resolver:

> Tengo una app. Quiero que la AI entienda su lenguaje visual para seguir construyendo sin romperlo.

Outputs prioritarios:

- UI Kit visual.

- [Design.md](http://Design.md).

- Agent instructions.

- Component inventory.

- Style rules.

- Drift warnings.

### 12.2. Diseñar la activación alrededor de un “aha moment” claro

El usuario debe sentir rápido:

> Esta herramienta entendió mi producto y produjo algo que puedo usar con mis agentes.

Para eso, no basta con entregar un archivo. Debe mostrar:

- Patrones visuales dominantes.

- Componentes detectados.

- Reglas útiles.

- Inconsistencias reales.

- Instrucciones listas para pegar o instalar en el workflow.

### 12.3. Convertir la retención en memoria viva

La recurrencia no vendrá solo de generar un [Design.md](http://Design.md) una vez.

Vendrá de:

- Re-escanear cambios.

- Detectar drift.

- Comparar versiones.

- Guardar decisiones visuales.

- Mantener reglas de proyecto.

- Alimentar agentes con contexto actualizado.

### 12.4. Tratar el [Design.md](http://Design.md) como output, no como producto completo

El [Design.md](http://Design.md) es útil, pero no debe ser toda la propuesta.

El valor real está en:

- La extracción.

- La interpretación.

- La curaduría.

- La revisión.

- La continuidad.

- La capacidad de alimentar agentes.

### 12.5. Usar “memoria visual” como concepto organizador

“Memoria visual” permite unir producto, estrategia y metodología.

Explica:

- Por qué la AI pierde continuidad.

- Por qué los agentes necesitan contexto heredable.

- Por qué un simple screenshot no basta.

- Por qué el sistema debe versionarse.

- Por qué el usuario necesita sentir control.

SchemaFlow puede formularse como un harness visual:

> Un sistema que captura, estructura y preserva decisiones visuales para que puedan ser heredadas por agentes, colaboradores y futuras sesiones de trabajo.

## 13. Framing recomendado

### Versión funcional

> SchemaFlow turns your existing UI into an AI-readable design system.

### Versión estratégica

> SchemaFlow is design memory for AI-built products.

### Versión orientada a workflow

> Scan your app, extract its UI kit, and keep every AI-generated change consistent.

### Versión más conceptual

> Preserve visual continuity across AI agents, product sessions and design changes.

### Versión de mercado

> The design system layer for AI-native product development.

## 14. Implicaciones de producto

### Prioridades iniciales

- Escaneo de páginas existentes.

- Extracción de patrones visuales.

- Inventario de componentes.

- Generación de [Design.md](http://Design.md).

- Generación de instrucciones para agentes.

- Revisión humana de hallazgos.

- Detección inicial de drift.

### Prioridades de retención

- Comparación entre versiones.

- Re-scan programado o manual.

- Historial de decisiones visuales.

- Reglas persistentes por proyecto.

- Reportes de consistencia.

- Actualización de agent instructions.

### Prioridades posteriores

- Integración con Figma.

- Exportación de tokens.

- Integración directa con Cursor/Claude Code.

- Team workflows.

- Governance para equipos.

- Historial visual/versionado avanzado.

## 15. Conclusión

SchemaFlow debe evitar quedar atrapado en una categoría demasiado amplia como “design system tooling” o demasiado abstracta como “AI-native design governance”.

La entrada más fuerte es concreta:

> Escanear una app existente, extraer su lenguaje visual y convertirlo en contexto operativo para agentes de AI.

Pero la estrategia no termina ahí.

La adquisición puede venir por extracción simple y valor inmediato. La activación viene cuando el usuario ve que el sistema entendió su producto. La retención aparece cuando SchemaFlow se convierte en memoria viva: detecta drift, compara versiones, actualiza reglas y preserva continuidad visual mientras el producto evoluciona.

La tesis más robusta sería:

> SchemaFlow es memoria visual para productos construidos con AI: extrae el sistema visual de una app existente, lo convierte en contexto operativo para agentes y ayuda a preservar coherencia mientras el producto evoluciona.
