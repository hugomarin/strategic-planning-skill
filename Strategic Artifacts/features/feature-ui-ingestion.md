---
artifact: feature-ui-ingestion
version: 0.1
status: draft
current: true
last_updated: 2026-06-01
needs_human_review: true
technical_reference: Technical Artifacts/features/feature-ui-ingestion.md
---

# Feature: UI Ingestion

## What it does

Permite al usuario ingresar una o más URLs de su producto para iniciar un scan. Captura el estado visual real del producto — HTML renderizado, CSS, estilos computados, patrones de componentes, y evidencia visual observable — desde páginas accesibles según el modo de acceso disponible. Es el punto de entrada del governance loop.

## Why it exists

Sin acceso confiable a la UI real del producto, ningún módulo downstream puede funcionar. La ingestion es la dependencia más crítica del stack: calidad de scan → calidad de extracción → calidad de diagnóstico → calidad de corrección. Si Schemaflow no puede ver bien el producto del usuario, todo lo que sigue pierde credibilidad.

## Where it lives

Pantalla de inicio / onboarding de un nuevo proyecto. `/new` o `/scan/new`.

---

## Sub-feature: Product URL Intake

### What it does

El usuario ingresa una o más URLs de su producto para iniciar el proceso de scan. Schemaflow valida las URLs, muestra qué páginas serán escaneadas, y da feedback del estado durante el proceso.

### Why it exists

Es el momento de menor fricción posible para que el usuario llegue al primer valor. Si hay demasiada fricción en la entrada, el usuario abandona antes de ver el aha moment.

### Where it lives

`/scan/new` — pantalla inicial de onboarding.

### How it is composed

- Campo de input de URL (una o múltiples)
- Validación básica de URL (formato, accesibilidad básica)
- Selector del modo de scan (en MVP: solo public page; en P1+: autenticado, local)
- Indicador claro de qué páginas serán escaneadas y qué no
- Feedback de estado durante el scan (progreso, página actual, tiempo estimado)
- Mensaje de error si la URL no es accesible

### Who can use it

Cualquier usuario con una cuenta activa. En el free tier: limitado en número de URLs y scans por proyecto.

### Rules

- El MVP solo soporta páginas públicas — no se puede escanear content behind login en la primera versión
- Si una URL devuelve 404, redirect a login, o no es accesible por el servidor, se muestra un error explícito con el motivo
- El usuario debe saber exactamente qué va a ser escaneado antes de confirmar el inicio del scan
- El sistema nunca debe silenciosamente reducir el scope del scan sin notificar al usuario

### What happens when it fails or is empty

- URL inaccesible: mensaje explícito con causa ("La página redirige a login — prueba con otra URL pública o espera el modo autenticado")
- URL vacío: CTA para ingresar la primera URL
- Timeout: mensaje claro + opción de reintentar

### Known issues

- OQ-003: Modelo de acceso al sitio no completamente definido — el MVP arranca con server-side public scan; autenticado y MCP se definen con design partners

### How it should evolve

- OQ-003: Agregar modo autenticado (test account, browser-visible session, o MCP) cuando design partners lo requieran
- Bulk URL upload (sitemap o lista)
- Crawl depth settings — cuántas páginas profundizar desde la URL inicial
- Sitemap discovery automático

---

## Sub-feature: Public Page Scanner

### What it does

Schemaflow escanea páginas públicamente accesibles desde el servidor. Captura el DOM renderizado, CSS computado, screenshots, y evidencia visual de los componentes y estilos presentes en cada página.

### Why it exists

Es el modo de adquisición de menor fricción — el usuario no necesita instalar nada ni proveer credenciales. Permite validar el valor del producto (aha moment) sin resolver primero el problema del acceso autenticado.

### Where it lives

Proceso de backend invisible al usuario durante el scan. El usuario ve un indicador de progreso en `/scan/[id]/loading`.

### How it is composed

- Crawler server-side que accede a las URLs indicadas
- Captura de DOM renderizado (post-JavaScript execution)
- Extracción de CSS computado y estilos aplicados
- Screenshots de página completa y viewport
- Identificación de patrones de componentes visibles
- Queue de procesamiento con feedback de progreso

### Who can use it

Disponible para todos los usuarios. Limitado a páginas públicas en MVP.

### Rules

- Solo escanea páginas que responden con 200 sin redirigir a login
- Nunca almacena ni transmite credenciales del usuario
- Debe manejar gracefully: páginas con heavy JS, SPAs, páginas con lazy loading
- Si una página tarda más de X segundos, continúa con las otras páginas y reporta el timeout
- El scan no debe parecer ni comportarse como un scraper — respetar robots.txt como señal de intención del sitio

### What happens when it fails or is empty

- Página no accesible: marcada como "not scanned" con razón específica; el scan continúa con las demás páginas
- Solo páginas con errores: el scan falla completamente con mensaje claro
- Resultado vacío (página con poco contenido CSS/HTML): se muestra lo que se encontró con advertencia de cobertura baja

### Known issues

- OQ-003: El MVP con server-side solo cubre páginas públicas — dashboards y flujos autenticados quedan fuera
- OQ-009: El nivel de completitud de scan requerido para preservar la confianza del usuario aún no está definido — se validará con design partners

### How it should evolve

- OQ-003: Agregar scan autenticado (browser-visible, MCP, o test account) para productos con UI relevante detrás de login
- Local/desktop scanner para ambientes de desarrollo o entornos privados
- Session replay para flujos dinámicos
