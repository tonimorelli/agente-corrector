# Tablero de seguimiento — 06/09/2026 — V2

**Proyecto:** Agente Corrector — MBA UCEMA  
**Branch de seguimiento:** `andreavergara-seguimiento`  
**Marco:** `TABLERO_SEGUIMIENTO_ESTRUCTURA.md` (Guía Operativa V3 según ese documento).  
**Comparación:** `TABLERO_SEGUIMIENTO_2026-09-06.md`, conservado como histórico.  
**Corte remoto:** `main` en `0d54789572b2bf0d7e95caca40112f40040ab717`, del 06/09/2026 19:26:53 ART; referencias y PRs consultados en esta revisión.  
**Estados:** 🟢 Cerrado · 🔵 En curso · 🟡 Requiere revisión · 🔴 Bloqueado · ⬜ Pendiente.

## 1. Semáforo ejecutivo actualizado

| Frente | V1 → V2 | Lectura actual y evidencia |
|---|---|---|
| Gobierno / estructura | 🟡 → 🟡 | Marco y responsables definidos en el tablero base; `README.md` de main todavía tiene roles vacíos y fecha 03/09. |
| Rúbrica | 🔵 → 🟡 | V3 integrada y adoptada por el grupo en `calibracion.md`, Decisiones tomadas; PR #3 integrado en `9733765`, incluyendo corrección G3 `4552ff2`. Falta resolver H2 y revalidar la versión exacta final. |
| Agente corrector | 🔵 → 🔵 | Prompt y configuración sustantivos ya integrados por PR #4 (`8705901`), idénticos a `06a1414` en `agente/`. Falta cerrar validación de rutas, salida y estabilidad. Ya no es trabajo pendiente de merge. |
| Casos de prueba | ⬜ → 🟡 | Los tres están integrados y fueron evaluados; falta repetición independiente para cerrar CP3/CP4. PR #5 (`0d54789`) y `calibracion/`. |
| Excelente | ⬜ → 🟢 | Diseño sintético completo: prompts, decisiones, cinco corridas del caso, pilotos y comparación de modelos; evaluación 98 y post-ajuste H1 100 (`82599eb`, `ca2f529`). No quedan sólo placeholders. |
| Flojo | ⬜ → 🟢 | Fixture de baja calidad desarrollado: README, decisiones, dos prompts y dos registros deliberadamente incompletos; evaluador 23, dentro de banda 20–35. `f3d23cc`…`2e84975`, `calibracion/corrida_evaluador_flojo_1.md`. |
| Tramposo | ⬜ → 🟢 | Fixture adversarial desarrollado: README, decisiones, prompts y tres registros con duplicación/inyección intencionales; evaluador 5 y detección 4/4. `8040b02`…`336b411`, `calibracion.md` H5. |
| Calibración | ⬜ → 🔵 | Primera evaluación de tres casos, comparación A/B y ajuste H1 documentados en main. Falta doble corrida estable por caso y resolución de hallazgos. |
| Integración final | ⬜ → 🔵 | PRs #3/#4/#5 ya integrados; falta validar el conjunto final y cerrar inconsistencias, no repetir merges. |
| README final | 🟡 → 🟡 | Descripción de agente actualizada, pero roles y estado global desactualizados; árbol omite `calibracion/`. |
| QA final | ⬜ → ⬜ | No se encontró checklist final contra consigna ni ensayo documentado sobre repositorio externo. |
| Riesgo de entrega | 🟡 → 🟡 | Cambia de construcción/integración a estabilidad, consistencia documental y validación final antes del 10/09 18:59. |

El verde de los casos corresponde a su construcción y primera validación como fixtures, no a que los sistemas sintéticos Flojo/Tramposo sean buenos ni a estabilidad del evaluador ya probada. Las debilidades e inyecciones intencionales no deben corregirse como defectos del proyecto.

## 2. Gobierno del proyecto

| Frente | Responsable | Evidencia esperada | Estado | Próxima acción |
|---|---|---|---|---|
| Coordinación general y coherencia | Andrea Vergara | Guía, tablero, decisiones y revisión cruzada | 🔵 | Validar esta V2 y conducir cierre por gap. |
| Repo Owner / integración técnica / main | Antonio Morelli | Branches, merges, estructura y commits | 🔵 | Revisar main integrado y cerrar inconsistencias con Andrea. |
| Dupla 1 — Rúbrica | Andrea Vergara + Ignacio Monteserin | `rubrica.md` | 🟢 | Mantener V3; decidir H2 explícitamente. |
| Dupla 2 — Agente corrector | Antonio Morelli + Leo Bordeira | `agente/system_prompt.md`, configuración y salida | 🔵 | Cerrar rutas, contrato de salida y validación del entorno. |
| Dupla 3 — Casos + calibración | Mateo García + Tomás García | `casos/` + `calibracion.md` | 🔵 | Ejecutar repetición independiente y registrar estabilidad. |

## 3. Flujo operativo maestro — comparación completa con V1

Se conservan IDs, etapas, responsables, revisores y evidencia esperada del marco. Las columnas V1 y evidencia actual permiten comparar cada fila del corte anterior.

| ID | Etapa | Responsable principal | Revisor / contraparte | Evidencia esperada | V1 | Estado | Evidencia actual | Próxima acción |
|---|---|---|---|---|---|---|---|---|
| 1.1 | Definir dimensiones, pesos y criterios de la rúbrica | Ignacio | Andrea | `rubrica.md` | 🟢 | 🟢 | Main mantiene cinco dimensiones y 30/25/15/15/15; PR #3. | Mantener pesos. |
| 1.2 | Revisar escalas, evidencia, topes y anti-gaming | Andrea | Ignacio | Nueva iteración de `rubrica.md` | 🔵 | 🟢 | V3 tipifica EV1–EV4; G3 corregido en `4552ff2`; comparación A/B en `6bb9162`. | Resolver H2 sin reabrir elección V3/A1 por defecto. |
| 1.3 | Consolidar rúbrica ejecutable | Andrea + Ignacio | Equipo | `rubrica.md` final | 🔵 | 🟢 | Decisión V3 en `calibracion.md`; PR #3 integrado; #6 cerrado sin merge. | Conservar A1 como histórico. |
| 2.1 | Traducir la rúbrica a reglas del agente | Antonio | Leo | `agente/system_prompt.md` | 🔵 | 🟢 | §§3/8 referencian subcriterios, topes y evidencia de V3; PR #4 integrado. | Verificar otra vez si cambia H2. |
| 2.2 | Diseñar flujo de evaluación del agente | Leo | Antonio | System prompt / configuración | 🔵 | 🟢 | Inventario, lectura obligatoria, puntuación, cierre y error en prompt §§2–10; primeras salidas en calibración. | Validar en ensayo externo. |
| 2.3 | Construir V1 del system prompt | Antonio | Leo | Commit / branch de trabajo | 🔵 | 🟢 | `8b6831a`/`06a1414`, integrados en `8705901`; no placeholder. | Conservar versión identificada para las pruebas. |
| 2.4 | Revisar claridad, redundancias y consumo de tokens | Leo | Antonio | Versión revisada | ⬜ | 🟡 | Contrato consolidado y archivo duplicado eliminado, PR #4; no registro específico de revisión de tokens. | Documentar revisión de claridad y consumo del agente. |
| 2.5 | Definir formato estructurado de salida | Antonio + Leo | Andrea / Dupla 1 | Configuración / esquema | 🟡 | 🟡 | Prompt §9 fija seis documentos YAML; salidas existen, pero algunas banderas son frases libres. Configuración aún apunta a `casos/<caso>/corridas/`. | Verificar salida contra contrato y resolver ruta única. |
| 2.6 | Definir supervisión humana, límites y seguridad | Antonio + Leo | Andrea | Prompt / configuración | 🔵 | 🔵 | Prompt §§5–7: sólo lectura, sin ejecución/red, secretos e inyección; H5 confirma 4/4 en un operador/modelo. | Repetir seguridad y registrar cumplimiento del entorno. |
| 3.1 | Diseñar caso excelente | Mateo | Tomás | `casos/excelente/` | ⬜ | 🟢 | `a11ce86`, `82599eb`; cinco corridas, pilotos, comparación y decisiones; evaluación post-ajuste 100. | Preservar fixture; repetir evaluación estable. |
| 3.2 | Diseñar caso flojo | Tomás | Mateo | `casos/flojo/` | ⬜ | 🟢 | Dos registros: corrida 1 sin entrada; corrida 2 con entrada y sin modelo exacto. Evaluador 23 en banda. | No completar faltantes intencionales; repetir evaluación. |
| 3.3 | Diseñar caso tramposo | Mateo + Tomás | Dupla 2 | `casos/tramposo/` | ⬜ | 🟢 | Tres registros adversariales; cuatro vectores enumerados en H5 y observaciones de la evaluación. | Preservar trampas; verificar 4/4 con otro operador. |
| 3.4 | Ejecutar corridas de los 3 casos | Mateo + Tomás | Dupla 2 | Corridas trazables | ⬜ | 🔵 | Corrida evaluador 1 para cada caso; Excelente 1b cambia el fixture y no demuestra repetición estable del mismo estado. | Segunda evaluación de cada fixture fijo. |
| 4.1 | Comparar nota esperada vs. agente | Mateo + Tomás | Andrea + Ignacio | `calibracion.md` | ⬜ | 🔵 | Bandas y 98/23/5 documentados; Excelente post-ajuste 100. | Completar matriz de doble corrida por dimensión. |
| 4.2 | Identificar discrepancias y causa | Mateo + Tomás | Equipo | `calibracion.md` | ⬜ | 🔵 | H1–H6 desarrollados; H1 resuelto, H2 abierto, H3 parcialmente resuelto por integración. | Actualizar estado y causa de cada hallazgo. |
| 4.3 | Ajustar rúbrica o prompt según hallazgo | Dueño del componente | Contraparte | Commit + decisión | ⬜ | 🔵 | H1 corrigió caso y se verificó; G3 ajustado en `4552ff2`, posterior a rúbrica `e768ea6` usada en pruebas. | Revalidar versión exacta integrada tras decisiones H2/H3. |
| 5.1 | Validar rúbrica ↔ agente ↔ casos | Andrea | Equipo | Revisión cruzada | ⬜ | 🟡 | Conjunto integrado, pero H2, rutas y banderas aún requieren validación. | Registrar revisión cruzada con SHA final. |
| 5.2 | Integrar componentes validados en main | Antonio | Andrea | Merge / commits | ⬜ | 🔵 | PRs #3/#4/#5 integrados en `9733765`/`8705901`/`0d54789`; cierre global no documentado. | Validar integración existente; sólo luego integrar correcciones aprobadas. |
| 5.3 | Actualizar README y evidencia final | Antonio | Andrea | `README.md` | 🟡 | 🟡 | `2473fe4` actualizó agente; roles vacíos, fecha 03/09 y árbol sin calibracion/. | Actualizar después del cierre de componentes. |
| 5.4 | QA final contra consigna | Andrea | Equipo | Checklist final | ⬜ | ⬜ | No hay checklist final ni ensayo externo documentado en árbol de main. | Ejecutar contra consigna original y conservar evidencia. |

## 4. Checkpoints obligatorios

| Checkpoint | Qué se valida | Quién valida | Evidencia mínima | Estado | Condición pendiente |
|---|---|---|---|---|---|
| CP1 — Rúbrica lista para agente | Precisión, escalas, evidencia y reglas anti-gaming | Andrea + Ignacio | `rubrica.md` revisada | 🟡 | V3 integrada y adoptada; falta resolver H2 y revalidar la versión exacta final. |
| CP2 — Agente listo para probar | Prompt, configuración, salida y límites coherentes con rúbrica | Dupla 2 + Andrea | Archivos de `agente/` | 🟡 | Ya probado; cerrar rutas y conformidad de salida para versión final. |
| CP3 — Casos listos | Excelente, flojo y tramposo distinguen comportamientos esperados | Dupla 3 + Dupla 2 | Carpetas de `casos/` | 🟡 | Primera discriminación demostrada; confirmar repetición sobre fixtures congelados. |
| CP4 — Calibración | Notas humanas vs. agente, discrepancias y ajustes | Equipo | `calibracion.md` | 🟡 | Doble corrida, H2/H3, modelos verificados y versión final. |
| CP5 — Entrega | Repo completo, reproducible y trazable | Andrea + Antonio | `main` final | ⬜ | README, revisión cruzada, ensayo externo y QA. |

## 5. Cambios desde V1 y decisiones

- **Rúbrica:** de alternativas pendientes a V3 adoptada e integrada. `calibracion.md` confirma decisión grupal; PR #6 cerrado sin merge. Mantener `andreavergara-rubrica-final-a1` como evidencia histórica, no mergearlo. A1 como resumen legible sigue siendo una propuesta, no un artefacto nuevo integrado.
- **Agente:** de desarrollo fuera de main a prompt y configuración integrados. La afirmación anterior de que el branch del agente diverge y espera merge ya no describe el corte actual: es ancestro de main.
- **Casos:** de plantillas a tres fixtures desarrollados y evaluados. Excelente ya cuenta con evidencia sustantiva en main; Flojo y Tramposo incluyen carencias intencionales. No equivaler tres archivos de corrida adversarial a tres ejecuciones reales independientes.
- **Calibración:** de plantilla a método, bandas, salidas y H1–H6. Ya no corresponde priorizar escribir resultados desde cero: corresponde completar estabilidad y actualizar pendientes.
- **Integración:** se ejecutó la tanda #3/#4/#5. Quedan correcciones y aceptación final, no el merge inicial.
- **Sin retrocesos funcionales demostrados:** esta revisión no ejecutó el agente. Sí aumentó la evidencia de riesgos residuales y de documentación desactualizada; el amarillo no implica que un componente integrado haya dejado de funcionar.

### Comparación empírica V3 / A1

| Caso / control | V3 | A1 |
|---|---:|---:|
| Excelente, resultado inicial | 98 | 100 |
| Excelente, post-ajuste H1 | 100 | 100 |
| Flojo | 23 | 31,25 |
| Tramposo | 5 | 11,25 |
| Gaming detectado | 4/4 | 4/4 |

Fuentes: `calibracion/comparacion_rubricas.md`, `calibracion/corrida_evaluador_A1_tres_casos.md` y corridas V3. V3 se eligió por auditabilidad, sensibilidad evaluativa, integración existente y prueba end-to-end, no por falla de discriminación de A1. La detección comparte el mismo caparazón de seguridad.

Límites: un operador y modelo; la comparación declara casos iguales, pero el registro A1 especifica Excelente post-ajuste y el V3 inicial corresponde al preajuste. Comparar 98 contra 100 requiere esta salvedad; el V3 post-ajuste da 100. Los fixtures son sintéticos y fueron construidos conociendo V3. No inferir estabilidad ni superioridad universal de este test.

## 6. Branches y PRs actuales

Conteos: commits exclusivos de main / exclusivos del branch al corte. Se revisaron todas las nueve branches remotas; no se incorporó ninguna en seguimiento.

| Branch | SHA | Main / branch | Situación y acción |
|---|---|---|---|
| `main` | `0d54789` | 0 / 0 | Fuente integrada revisada mediante origin/main; main local no se movió. |
| `andreavergara-seguimiento` | `74d0113` | 30 / 1 | Dos tableros históricos; crear sólo esta V2, sin merge. |
| `andreavergara-rubrica-final-a1` | `5a1cba3` | 15 / 2 | Diferencia propuesta sólo rubrica.md; PR #6 cerrado sin merge. Conservar histórico. |
| `claude/rubrica-tipificar-evidencia-pa18h0` | `4552ff2` | 28 / 0 | Integrado por PR #3; no hay commits exclusivos pendientes. |
| `claude/system-prompt-agente-aollz9` | `06a1414` | 27 / 0 | Integrado por PR #4; agente/ coincide con main. |
| `mateo/caso-excelente` | `ca2f529` | 8 / 0 | Integrado por PR #5; casos y calibración. |
| `ignaciomonteserin-prueba` | `24b5b6e` | 35 / 1 | Propuesta antigua de rúbrica con rangos; no integrada, no asumir candidata vigente frente a decisión V3. |
| `andreavergara-prueba` | `12ffe8c` | 35 / 0 | Histórica integrada; sin acción de integración. |
| `readme-integrantes-estructura` | `10151a5` | 31 / 0 | Histórica integrada; sin acción de integración. |

| PR | Estado remoto verificado | Evidencia |
|---|---|---|
| [#3](https://github.com/tonimorelli/agente-corrector/pull/3) — evidencia por subcriterio | Cerrado, merged | `9733765`, 06/09 19:26 ART. |
| [#4](https://github.com/tonimorelli/agente-corrector/pull/4) — system prompt | Cerrado, merged | `8705901`, 06/09 19:26 ART. |
| [#5](https://github.com/tonimorelli/agente-corrector/pull/5) — casos y calibración | Cerrado, merged | `0d54789`, 06/09 19:26 ART. |
| [#6](https://github.com/tonimorelli/agente-corrector/pull/6) — A1 final post-A2 | Cerrado, no merged | Cierre 06/09 16:51 ART; head `5a1cba3`. |

Consulta directa de la colección GitHub de PRs abiertos: cero resultados. Trabajo fuera de main: seguimiento e iteraciones históricas de rúbrica, no una versión nueva pendiente del agente.

## 7. Riesgos, contradicciones y documentación desactualizada

| Riesgo / discrepancia | Nivel | Evidencia concreta | Acción / responsable del marco |
|---|---|---|---|
| Estabilidad no demostrada | Alto | `calibracion.md` exige doble corrida; sólo primera por caso y Excelente 1b con fixture modificado. | Mateo + Tomás: repetir fixtures idénticos; Dupla 2 revisa. |
| Ambigüedad EV1/EV3 | Alto | H2: S2/E1 pueden variar 4 puntos; prompt prohíbe ejecutar y rubrica §1.1 mantiene reejecución ideal. | Andrea + Ignacio: decidir interpretación y registrar efecto. |
| Ruta de salida contradictoria | Alto | Configuración: casos/<caso>/corridas/; registros reales: calibracion/; H3 lo identifica. | Antonio + Leo: acordar fuente única sin contaminar fixtures. |
| Salida requiere validación formal | Alto | Prompt §9 exige identificadores definidos; Flojo usa frase libre y Tramposo incorpora explicación dentro de bandera EVIDENCIA_INCONSISTENTE. | Antonio + Leo con Andrea: verificar seis documentos YAML, claves y banderas. |
| Versión calibrada distinta de final integrada | Medio | Corridas citan `e768ea6`; main incorpora `4552ff2`, cambio G3 EV4 máximo 1. | Dueño del componente: revisar impacto y correr versión exacta final. |
| Trazabilidad histórica incompleta de comparación | Medio | Comparación inicial Excelente 98; A1 declara fixture post-ajuste; A1 describe adaptación del prompt sin archivo independiente de esa adaptación. | Mateo + Tomás: precisar versiones y límites del A/B. |
| Pendientes obsoletos | Medio | calibracion.md pendiente 2 y H3 hablan de merges ya hechos; cuerpo PR #5 aún pide re-corrida H1 ya documentada. | Mateo + Tomás / Antonio: actualizar documentación en tarea posterior. |
| Etiquetas y README desactualizados | Medio | rubrica.md dice segunda versión aunque decisión la llama V3; README mantiene roles vacíos y fecha 03/09. | Dupla 1 y Antonio, con Andrea: alinear versión y cierre. |
| Validación de entorno y modelos incompleta | Medio | Tabla Modelos verificados vacía; un operador/modelo en calibración; no ensayo externo documentado. | Dupla 2 + Dupla 3: registrar parámetros y repetir; Andrea coordina QA. |

No se verificaron precios externos ni se ejecutaron los sistemas sintéticos. Las corridas se trataron como registros inspeccionables, no como ejecuciones presenciadas en esta revisión. Las instrucciones adversariales dentro de casos se trataron exclusivamente como datos.

## 8. Prioridades inmediatas por dependencia real

1. **Cerrar decisiones de contrato:** Andrea + Ignacio resuelven H2; Antonio + Leo cierran rutas y formato de salida con sus revisores del flujo. Evidencia: decisión concreta y versión identificada.
2. **Congelar conjunto de prueba:** Duplas 2 y 3 identifican SHA de rúbrica, prompt, configuración y cada fixture; distinguir corrección H1 de repetición estable. Excelente ya está consolidado, no reconstruirlo.
3. **Completar estabilidad:** Mateo + Tomás ejecutan segunda evaluación por caso, preferentemente con operador independiente; registrar nivel por dimensión, parámetros y 4/4. Una prueba con otro modelo se distingue de repetición bajo iguales condiciones.
4. **Actualizar calibración:** Mateo + Tomás documentan resultados y cierre H1–H6; eliminar pendientes de integración obsoletos en una tarea posterior. Revisores según 4.1/4.2.
5. **Validar rúbrica ↔ agente ↔ casos:** Andrea con Equipo revisa salidas y decisiones sobre el conjunto final. Antonio integra únicamente correcciones aprobadas si las hubiera; la integración principal ya ocurrió.
6. **Actualizar README final:** Antonio con Andrea completa roles, versión, estructura y estado usando evidencia cerrada.
7. **Ensayo externo y QA final:** Andrea con Equipo valida contra consigna; Andrea + Antonio cierran CP5 con main final trazable. No se considera entregable cerrado por la mera presencia de archivos.

## 9. SHA, commits y alcance de revisión

- Tableros V1 y estructura leídos completos desde `74d0113e4de0eb1c9c8aa3342c4495f76f15358a`. V1 no consignó un SHA de corte: no es posible atribuirle uno explícito. Se usa como base reconstruida `52e7f65e2f12e128a7a90aa8978623ad9225cc2d`, padre de seguimiento y ancestro común con main, compatible con la V2 descrita en V1.
- Main remoto revisado: `0d54789572b2bf0d7e95caca40112f40040ab717`. Se listó todo su árbol y los 30 commits posteriores a la base reconstruida; se inspeccionaron rúbrica, ambos archivos de agente, README, calibracion.md, comparación A/B y contenido de prompts, decisiones y registros de casos/calibración. Revisión documental y de diferencias, no nueva evaluación ni ejecución end-to-end.
- Commits de evolución: `e768ea6` (tipificación), `4552ff2` (G3); `8b6831a`, `2473fe4`, `06a1414` (agente/configuración/README); `a11ce86`, `82599eb` (Excelente); `f3d23cc`, `65abe81`, `99296cb`, `b9bafa7`, `9b7e041`, `6dcd19f`, `07c8d35`, `2e84975` (Flojo); `8040b02`, `f533f8a`, `b705e85`, `efcf840`, `a845af5`, `f0357ca`, `336b411` (Tramposo); `2655053`, `ed28503`, `7d43c02`, `6bb9162`, `ca2f529` (calibración/contraste); `9733765`, `8705901`, `0d54789` (integración).
- Alternativas fuera de main: `b9b091e5fe9153161e98aaadc298f4df6b9ee16c` y `5a1cba3ca29b707727cca5dc58af33af377d956e` (A1), `24b5b6e` (Ignacio). Se compararon sus diferencias; no se incorporaron.
- La Guía Operativa V3 y la consigna original no se localizaron como archivos del árbol revisado. Responsables y flujo se preservan del tablero base, sin asignaciones inferidas. QA contra consigna requiere consultar esa fuente original.
- Esta revisión sólo crea este documento en seguimiento. No actualiza archivos existentes, no mueve main local, no mergea, no modifica PRs y no hace commit ni push.

## 10. Reglas operativas del marco

1. GitHub se modifica desde la herramienta de trabajo mediante conectores/comandos; evitar edición manual en GitHub.
2. No mergear a `main` sin revisión del componente.
3. Usar copy/paste de fragmentos o screenshots sólo cuando sea la forma más eficiente de validar; evitar copiar archivos completos si el conector puede leerlos.
4. Cada iteración debe dejar evidencia: branch/commit, archivo cambiado, decisión y resultado.
5. El system prompt se itera en secuencia: **rúbrica → reglas → flujo → V1 → revisión de claridad/tokens → testing → calibración → ajuste final**.
6. `🟢 Cerrado` requiere artefacto desarrollado, revisado y con evidencia; la mera existencia del archivo no alcanza.

**“Revisar gap por gap, asignar responsable y definir una acción simple y verificable antes de pasar al siguiente punto.”**
