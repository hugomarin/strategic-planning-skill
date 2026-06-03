---
artifact: open-questions
version: 0.1
status: active
last_updated: 2026-06-01
---

# Open Questions

## Open Questions

| ID | Question / Gap | Artifact | Section | Current assumption | Blocks | Priority |
|---|---|---|---|---|---|---|
| OQ-001 | ¿Cuál es el trigger específico de compra — el evento concreto que convierte awareness en purchase intent? | user-architecture | UA-05 | Founder: el usuario alcanza un umbral de costo de tiempo — se da cuenta de que gasta demasiado tiempo arreglando temas visuales sin poder resolverlo fácilmente. No es un evento discreto observado externamente. | none — generación puede proceder con esta suposición marcada como NHR | High |
| OQ-002 | ¿Quién es el primer ICP monetizable — qué sub-segmento específico muestra WTP antes que los demás? | user-architecture | UA-01, UA-07 | Founder: "builders con productos serios y monetizables donde la consistencia visual importa." Candidatos: freelancers con trabajo de cliente, indie builders con 2+ productos, founders pre-launch. No validado — requiere design partners. | none — generación puede proceder con NHR; blocking para Stage 4 de objectives-architecture | High |
| OQ-003 | ¿Qué modelo de acceso a sitio usará el MVP — server-side, browser-visible, local/desktop o hybrid? | product-architecture | PA-06 | Founder: solución web con server-side; posiblemente MCP montado en el servidor. Detalle a definir durante etapa de design partners y Stage 0. | none — dirección clara, detalle pendiente; puede proceder con NHR en PA-06 | High |
| OQ-004 | ¿Qué evidencia externa (entrevistas, datos de comportamiento de no-founders) valida que el drift visual es urgente y no solo tolerable? | product-thesis | PT-04 | Toda la evidencia actual es founder-led y secundaria. El dolor "aparece más como incomodidad recurrente que como categoría validada de mercado." | none — generación puede proceder con NHR explícito en PT-04 | High |
| OQ-005 | ¿Cómo se mapea explícitamente cada etapa de validación a cada suposición específica de PT-03? | objectives-architecture | OA-05 | El vínculo es implícito en los docs nuevos (Stage 1 valida el core loop, Stage 2 valida retención). Sin mapeo explícito. | none — generación puede proceder con NHR | Medium |
| OQ-006 | ¿Cuáles son los métodos de medición para cada KR — cómo se trackea cada métrica en la práctica? | objectives-architecture | OA-03 | KR targets marcados como "hipótesis iniciales, no targets permanentes" en el doc de Objectives Architecture. | none — targets provisionales aceptables en esta etapa | Medium |
| OQ-007 | ¿Cuál es el TAM/SAM del ICP primario? | strategy-brief | SB-01 | Sin cuantificar en ningún documento. | none — generación puede proceder; no blocking para KAs | Low |
| OQ-008 | ¿Cómo se defiende el posicionamiento de governance-layer si AI coding tools (Cursor, Claude, Lovable) agregan visual consistency nativamente? | strategy-brief | SB-04 | La defensibilidad depende del switching cost del historial de re-scans y la ontología de componentes embebida. Reconocido como riesgo en PT-06. | none — registrado como riesgo en product-thesis | Low |
| OQ-009 | ¿Qué nivel de completitud de scan es suficiente para preservar la confianza del usuario en el primer uso? | product-architecture | PA-05, PA-07 | El producto debe detectar los componentes/estilos suficientes para que el usuario sienta que Schemaflow "realmente ve su producto." Umbral exacto sin definir. | none | Medium |
| OQ-010 | ¿Cuál es el minimum viable governance loop — qué subset de features P0 es verdaderamente irreducible para validar la tesis? | product-architecture | PA-08 | El loop mínimo hipotético es: URL → scan → real UI kit → drift → prompts de corrección → re-scan. Pendiente de validar con design partners. | none | Medium |
| OQ-011 | ¿Cuáles son las anti-métricas formales — qué métricas no debe optimizar el equipo? | objectives-architecture | OA-08 | Señaladas de forma dispersa: total de scans, signups, stars sin uso activo del output. No formalizadas como sección. | none — puede proceder con advertencias incorporadas en objectives-architecture | Low |

## Resolved Decisions

| ID | Original question | Decision | Resolution date | Decided by |
|---|---|---|---|---|
| NQ-01 | Posicionamiento: format-first o governance-layer | governance-layer — el producto es el workflow de governance (scan → diagnose → govern → re-scan) | 2026-06-01 | Founder |
| NQ-05 | Primer AI-actionable output format del MVP | Dos outputs del mismo loop: (1) prompts de corrección precisos con valores exactos para arreglar drift actual; (2) design context file generado en officialization para prevenir drift futuro. El primero entrega valor inmediato; el segundo entrega retención. | 2026-06-01 | Founder |
| C-02 | Posicionamiento estratégico | governance-layer (ver NQ-01) | 2026-06-01 | Founder |
| C-03 | North Star Metric | Completed Governance Loop Rate — no "files/week" | 2026-06-01 | Founder |
| C-01 | Definición del segmento primario | Docs nuevos son autoritativos: AI-native builders con producto real en movimiento | 2026-06-01 | Implícito en docs nuevos |
| C-04 | Backlight como competidor activo | Remover de lista activa — cerrado jun 2025 | 2026-06-01 | Confirmado por PDF |
| C-05 | Alcance de solopreneurs doc | Fuera de scope — legacy de dirección anterior del producto | 2026-06-01 | Founder |
