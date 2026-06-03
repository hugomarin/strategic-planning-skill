# Input Analysis (internal scaffolding — delete after session)
Generated: 2026-06-01
Corpus: 12 documents (7 original + 5 nuevos)

---

## Sources available

| File | Type | Descripción |
|---|---|---|
| `Schemaflow Product Thesis.md` | Artefacto estratégico | Responde explícitamente PT-01 a PT-08; bet central, supuestos, evidencia, contraargumento, riesgos de falsificación, implicaciones de producto y roadmap. |
| `Schemaflow Product Architecture.md` | Artefacto estratégico | Responde PA-01 a PA-08; principios, módulos, flujos críticos, features indispensables, restricciones, dependencias, riesgos. |
| `User Architecture Schemaflow.md` | Artefacto estratégico | Responde UA-01 a UA-07; ICP de aprendizaje, señales observables, tensión central, workarounds, triggers de compra, exclusiones, lógica de adopción. Estado explícito: pre-ICP. |
| `Schemaflow Objectives Architecture.md` | Artefacto estratégico | Responde OA-01 a OA-05; 5 etapas de validación con KRs, North Star (Completed Governance Loop Rate), milestones observables. |
| `Schemaflow Feature Definition.md` | Framework táctico | 20 features con prioridad P0/P1/P2; definición de MVP; feature risks; anti-prioridades explícitas. |
| `strategy-and-competitive-analysis.md` | Análisis estratégico (anterior) | Good Strategy Kernel + Porter's 5 Forces; posicionamiento "format-first / New Creative"; 5 acciones coherentes. Parcialmente supersedido por docs nuevos en posicionamiento. |
| `SchemaFlow Strategy.pdf` | Deck presentación (anterior) | Duplica strategy-and-competitive-analysis.md. Agrega: Backlight cerrado el 1 jun 2025. Baja densidad de información única. |
| `JTBD-new-creative-segment.md` | Investigación JTBD (anterior) | Análisis JTBD profundo del segmento "New Creative (High Taste, Low Craft)"; jobs funcionales/sociales/emocionales; workarounds; fuerzas de progreso. |
| `solopreneurs-new-creatives-ui-builders.md` | Investigación secundaria (anterior) | Investigación sobre builders Bubble/Supabase. Principalmente relevante para una dirección de producto anterior (schema planning tool). Tratar como contexto de fondo únicamente. |
| `ai-design-consistency-new-creative.md` | Investigación secundaria (anterior) | Señales de dolor en comunidades; herramientas emergentes; workarounds prevalentes. Fuente clave para evidencia del problema. |
| `Propuesta Estrategica Ampliada.md` | Framework estratégico (anterior, sin fecha) | JTBD×competencia; lifecycle framing; buyer personas; "visual memory" como concepto organizador. Parcialmente integrado en docs nuevos. |
| `Strategic Analysis Document.md` | Notas de sesión (anterior) | Conversación estratégica; abre preguntas sobre WTP, ICP, free tier, defensibilidad. No es fuente de decisiones establecidas. |

## Missing sources

Ningún documento es referenciado desde Input/ sin estar presente en Input/. No hay fuentes faltantes.

## Ontological map

| Entity | Type | Appears in | Tension with |
|---|---|---|---|
| AI-native builder | User | Product Thesis, User Arch, Product Arch | Prior docs: "New Creative (High Taste, Low Craft)" — definición más estrecha |
| New Creative (High Taste, Low Craft) | User sub-type | JTBD doc, strategy doc, PDF | User Architecture: redefinido como sub-arquetipo, no ICP primario |
| Aesthetic drift / visual drift | Strategic | Todos los docs | Consistente — nombre del problema central |
| Visual governance layer | Strategic frame | Product Thesis, Product Architecture | C-02: vs. "format-first / DESIGN.md as moat" (strategy doc anterior) |
| Governance loop (re-scan) | Strategic frame | Product Thesis, Objectives Arch | C-03: vs. "DESIGN.md files/week" como North Star (strategy doc) |
| DESIGN.md / design file format | Strategic/Technical | Todos los docs | C-02: ¿es el producto o un output del producto? |
| Completed Governance Loop Rate | North Star | Objectives Architecture | C-03: strategy doc lo define como "files/week" |
| getdesign.md | Competitor | strategy doc, ai-design doc | Consistente — competidor más directo |
| Tokens Studio | Competitor | strategy doc, ai-design doc | Consistente — incumbente Tier 1 |
| Backlight | Competitor | strategy doc, PDF | C-04: cerrado jun 2025; quitar de lista activa |
| Bubble/Supabase builder | Segment | solopreneurs doc | C-06: legacy de dirección anterior del producto; no relevante para tesis actual |
| SchemaFlow | Product | Todos | Nombre consistente |

## Coverage map

| KA | Answered | Partial | Absent |
|---|---|---|---|
| strategy-brief | SB-01, SB-03, SB-05, SB-06, SB-08 | SB-02 (ICP pre-validado), SB-04 (diferenciación), SB-07 (targets sin timeline) | None |
| product-thesis | PT-01, PT-02, PT-03, PT-05, PT-06, PT-07, PT-08 | PT-04 (evidencia founder-led, sin investigación externa) | None |
| user-architecture | UA-02, UA-03, UA-04, UA-06, UA-07 | UA-01 (pre-ICP), UA-05 (trigger hipótesis), UA-08 (implicaciones implícitas) | None |
| product-architecture | PA-01, PA-02, PA-03, PA-04, PA-05, PA-06, PA-07, PA-08 | None | PA-09 (N/A, pre-lanzamiento) |
| objectives-architecture | OA-01, OA-02, OA-04, OA-06, OA-07 | OA-03 (KR targets sin método de medición), OA-05 (thesis link implícito), OA-08 (anti-métricas dispersas) | None |

## Claims with evidence

- Builders AI-nativos usan "make this consistent" como prompt de recuperación — Source: User Architecture Schemaflow.md, UA-04; corroborado por JTBD doc
- Builders editan manualmente CSS/Tailwind/componentes para restaurar consistencia — Source: User Architecture Schemaflow.md, UA-04; JTBD doc, Habit section
- Lovable, v0 y Bolt tienen design system consistency gateado detrás de Enterprise — Source: ai-design-consistency-new-creative.md, Key Finding 3; strategy doc, Diagnosis table
- Ningún competidor actual cierra el loop "describe once, AI reads always" end-to-end — Source: strategy doc, Key Dynamics; SchemaFlow Strategy.pdf
- getdesign.md es el competidor más directo: extrae design system de sitio existente, mismo target — Source: strategy doc, Tier 1; SchemaFlow Strategy.pdf
- Tokens Studio: 264K usuarios Figma, Figma-locked, sin integración AI coding tools — Source: strategy doc, Competitor 1
- "Silence in your design system = Claude defaults" — Source: ai-design-consistency-new-creative.md, Key Findings (MindStudio)
- Workarounds documentados: Notion color docs, screenshot pasting, long preambles — Source: ai-design-consistency-new-creative.md; JTBD doc; strategy doc, Threat of Substitutes
- El problema de "aesthetic drift" existe en comunidades de builders pero no tiene nombre — Source: ai-design-consistency-new-creative.md; JTBD doc, The Frame section
- Evidencia founder: alinear un botón, switch o fuente puede llevar más tiempo que construir un feature de backend — Source: Product Thesis.md, PT-04
- El sub-segmento relevante de "solopreneurs" son los builders AI-nativos que hacen SaaS, no solopreneurs lifestyle — Source: solopreneurs doc, Key Findings

## Assumed claims

- Los users adoptarán una capa de governance dedicada a medida que el desarrollo AI acelera — Appears in: Product Thesis.md, PT-01 — Proyección del founder; sin validación externa
- La calidad de diseño y consistencia visual se volverán diferenciadores más fuertes para productos digitales — Appears in: Product Thesis.md, PT-03 (Assumption 3) — Sin datos de mercado
- Mantener buen diseño en iteraciones AI-assisted permanecerá difícil sin una capa de control dedicada — Appears in: Product Thesis.md, PT-03 (Assumption 5) — Razonamiento fundacional; sin validación externa
- El segmento que paga será más estrecho: users con productos maduros, múltiples productos o trabajo con clientes — Appears in: Product Thesis.md, PT-05; User Architecture.md, UA-01 — Hipótesis, sin datos de comportamiento o compra
- El pago es probable cuando visual governance crea ROI claro (5–10 hrs/mes en correcciones) — Appears in: User Architecture.md, UA-05 — Sin datos de WTP observados
- Builders en etapa temprana tolerarán inconsistencia mientras priorizan validación y velocidad — Appears in: Product Thesis.md, PT-05 — Inferencia razonable; sin evidencia de usuario
- Distribución viral peer-to-peer en comunidades de builders — Appears in: strategy doc, Guiding Policy — Hipótesis de distribución; sin datos observados
- SchemaFlow puede diferenciarse vía design context, component ontology y AI-actionable governance — Appears in: Product Thesis.md, Summary — Intención estratégica; sin validación

## Source conflicts

| Conflict ID | Topic | Sources | Conflict | Strategic impact | Recommendation | NHR? |
|---|---|---|---|---|---|---|
| C-01 | Definición del segmento primario | strategy doc + PDF (anteriores) vs. Product Thesis + User Architecture (nuevos) | Docs anteriores: "New Creative (High Taste, Low Craft)" — definición aspiracional y de identidad. Docs nuevos: "AI-native builders con producto real en movimiento, experimentando visual governance como costo recurrente" — definición conductual y operacional. | High — diferentes definiciones implican diferentes filtros de adquisición, copy y onboarding | Docs nuevos son autoritativos; "High Taste, Low Craft" es sub-arquetipo, no ICP primario | No — usar docs nuevos |
| C-02 | Posicionamiento estratégico: format-first vs. governance layer | strategy-and-competitive-analysis.md (anterior) vs. Product Thesis + Product Architecture (nuevos) | Strategy doc: Schemaflow como "format-first, AI-native design identity standard" con DESIGN.md como moat. Docs nuevos: Schemaflow como "progressive visual governance layer" donde DESIGN.md es un output, no el producto. | **High — dos estrategias diferentes implican secuencias de build, métricas de éxito y approaches de distribución completamente distintos** | Orchestrator debe confirmar con founder cuál framing es autoritativo antes de finalizar strategy-brief | **Yes** |
| C-03 | North Star Metric | strategy doc: "DESIGN.md files created/week" (target: 100/semana Q3 2026) vs. Objectives Architecture: "Completed Governance Loop Rate" | Miden comportamientos completamente diferentes. Files/week = adopción de formato. Governance Loop Rate = retención del producto. Optimizar para uno puede dañar al otro. | High — si el equipo optimiza para el KPI incorrecto desde el inicio, el producto puede "crecer" sin validar la tesis | Objectives Architecture (más nuevo) es autoritativo; abandonar "files/week" como North Star a menos que se confirme posicionamiento format-first | No — usar Objectives Architecture |
| C-04 | Estado de Backlight como competidor | strategy doc (activo Tier 1) vs. SchemaFlow Strategy.pdf (cerrado jun 2025) | Strategy doc lo perfila como competidor activo; PDF confirma su cierre. | Low-Medium — análisis competitivo tiene una empresa muerta en Tier 1 | Remover de lista activa; notar como señal de fragilidad del mercado para plays full-platform | No |
| C-05 | Alcance del ICP | Propuesta Ampliada (amplio: AI-native builder general) vs. User Architecture (pre-ICP: 3 sub-segmentos) vs. JTBD doc (New Creative persona) | Tres framings de ICP distintos sin reconciliación completa | Medium — framings incompatibles producen artefactos de user-architecture incompatibles | Usar User Architecture Schemaflow.md como base (más reciente y estructurado); flags de sub-segmento learning vs. monetizable sin resolver | Yes |
| C-06 | Origen del producto / pivot previo | solopreneurs doc (schema design complexity) vs. todos los docs nuevos (visual governance) | solopreneurs doc es investigación para un problema y producto completamente diferente (schema planning tool para Bubble/Supabase builders) | Low (estratégico) — sugiere pivot significativo previo; investigación antigua no refleja dirección actual | Tratar solopreneurs doc como contexto de fondo únicamente; no informar generación de artefactos | No |

## Tactical inputs found

| Tactical item | Source | Strategic interpretation | Thesis link | Constraint | Recommendation |
|---|---|---|---|---|---|
| Publicar DESIGN.md spec como open source | strategy doc, Action 1 | Legitimidad del formato a través de apertura; adopción comunitaria | Solo relevante si se confirma posicionamiento format-first | Si governance-layer, es un output, no la acción inicial | Depends on C-02 resolution |
| CLI lint/validate (`npx schemaflow check`) | strategy doc, Action 3 | Capa de enforcement = superficie de producto separada | Solo relevante bajo format-first positioning | No requerido bajo governance-layer | Defer hasta resolución de C-02 |
| Artículo "aesthetic drift" | strategy doc, Action 4 | Problem naming crea demanda de búsqueda y thought leadership | Soporta ambas estrategias | Publicar concurrent con producto live; docs nuevos no lo incluyen explícitamente | Roadmap candidate bajo ambas estrategias |
| URL-based product scan como P0 | Feature Definition, Feature 2 | Entry point MVP acquisition | Core del loop de governance | Constrained to public pages; authenticated scan = P1 | Roadmap candidate (Fase 1) |
| Usage cost instrumentation como P0 interno | Feature Definition, Feature 17 | Economics deben entenderse antes de pricing | Required para monetización responsable | Desde el primer scan; no opcional | Roadmap candidate (Fase 1) |
| Reclutar 5–10 design partners (Stage 0) | Objectives Architecture, Stage 0 | Validación debe preceder definición del roadmap | Sin design partners no hay roadmap responsable | No se puede definir pricing sin datos de design partners | Acción inmediata pre-roadmap |
| Site access model decision para MVP | Feature Definition, Feature 15; Product Architecture, PA-06 | Decisión arquitectónica más importante del MVP | Determina calidad de scan, modelo de confianza y secuencia de build | Cuatro opciones analizadas; ninguna seleccionada aún | Non-omittable question #4 |
| Primer AI-actionable output format | Feature Definition, Feature 8; Product Architecture, PA-04 | La tesis requiere output AI-actionable desde el MVP | Cinco formatos listados; ninguno seleccionado | Determina qué significa "done" para el feature más diferenciador | Non-omittable question #5 |
| GitHub stars como señal de legitimidad | strategy doc | Riesgo de vanity metric | Anti-métrica: stars sin uso activo de files | Evitar optimización para visibilidad sobre outcomes | Registrar como anti-métrica en objectives-architecture |
| Seed DESIGN.md templates en builder communities | strategy doc, Action 5 | Distribución peer-to-peer | Relevante bajo ambas estrategias | Producto debe estar live y generando files | Roadmap candidate (Fase 1-2) |

## Candidates for open-questions.md

1. Posicionamiento estratégico primario: format-first o governance-layer (blocking: strategy-brief, product-thesis, objectives-architecture)
2. Trigger específico de compra — qué evento concreto, no dolor crónico (blocking: user-architecture, strategy-brief)
3. Primer ICP monetizable — qué sub-segmento específico muestra WTP antes que otros (blocking: user-architecture, objectives-architecture)
4. Modelo de acceso a sitio para MVP — server-side, browser-visible, local/desktop o hybrid (blocking: product-architecture)
5. Primer AI-actionable output format del MVP — copyable prompts, ui-kit.md, design.md, rules files, agent skills (blocking: product-architecture)
6. Evidencia externa del problema — validación no-founder del dolor (weakening: product-thesis)
7. Métodos de medición por KR — cómo se trackea cada métrica en la práctica (weakening: objectives-architecture)
8. Mapeo explícito etapa de validación → suposición PT-03 específica (weakening: objectives-architecture)
9. Nivel de completitud de scan requerido para preservar confianza en primer uso (weakening: product-architecture)
10. Mínimo viable governance loop para validar con design partners — subset irreducible de features P0 (weakening: objectives-architecture)
11. Modelo de pricing y frontera free/paid una vez que se conozca el economics del uso (tracked: strategy-brief, objectives-architecture)
12. Defensibilidad del posicionamiento si AI coding tools agregan visual consistency natively (tracked: strategy-brief, product-thesis)
13. Anti-métricas formalizadas — lista explícita de lo que el equipo no debe optimizar (tracked: objectives-architecture)
14. "New Creative (High Taste, Low Craft)" vs. "AI-native builder con producto real" — ¿son el mismo arquetipo? (tracked: user-architecture)

## Non-omittable questions

Preguntas que deben responderse, asumirse explícitamente, o convertirse en objetivos de validación antes de que se pueda generar el roadmap:

1. **Posicionamiento estratégico primario: format-first o governance-layer?** — Afecta: strategy-brief (todos los sections), product-thesis (PT-07, PT-08), objectives-architecture (North Star, OA-03). Dos estrategias con secuencias de build, métricas y distribución completamente distintas. Sin resolver, strategy-brief no puede finalizar su sección de diferenciación.

2. **¿Qué evento específico de compra causa que un usuario busque y pague por visual governance ahora mismo?** — Afecta: user-architecture (UA-05), strategy-brief (SB-02). El dolor crónico produce awareness, no compra. Sin trigger validado, la estrategia de adquisición no tiene un momento que targetear.

3. **¿Quién es el primer ICP monetizable y qué lo separa del ICP de aprendizaje?** — Afecta: user-architecture (UA-01, UA-07), strategy-brief (SB-02), objectives-architecture (OA-03 Stage 4). Tres framings de ICP coexisten sin reconciliación. Requiere decisión del founder o evidencia de design partners.

4. **¿Qué modelo de acceso a sitio usará el primer MVP?** — Afecta: product-architecture (PA-06), todos los módulos downstream. PA-06 identifica esto como "la dependencia más importante." Cuatro opciones analizadas; sin selección. Sin esta decisión, calidad de scan, modelo de confianza y secuencia de build no pueden finalizarse.

5. **¿Cuál es el primer AI-actionable output format que shippe el MVP?** — Afecta: product-architecture (PA-04), feature definition (Feature 8). La tesis requiere output AI-actionable desde el MVP. Cinco opciones listadas; ninguna seleccionada. El formato específico determina qué significa "done" para el feature más diferenciador del producto.

## Proposed generation order

Phase 1: `strategy-brief` + `product-thesis` — establecer qué es el producto y por qué existe. Suficiente material para ambos; NHR markers en SB-02, SB-04, PT-04.
Phase 2: `user-architecture` + `product-architecture` — definir para quién y cómo. NHR markers en UA-01, UA-05; decisiones no-omitibles en PA-06 y PA-04 deben presentarse al founder.
Phase 3 (conditional): `features/` children — evaluar después de `product-architecture`; activar solo si hay 5+ módulos con comportamiento diferenciado.
Phase 4: `objectives-architecture` — capa de validación medible. NHR markers en OA-03 y OA-05; requiere que los otros KAs estén estables.
Phase 5: `strategic-roadmap.md` — solo después de los 5 KAs completos y los dos review checkpoints.
