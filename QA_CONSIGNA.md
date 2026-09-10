# QA V2 de precierre — Consigna del parcial

Comparación punto por punto entre lo que pide la consigna del parcial
(`docs/parcial_agente_evaluador.pdf`) y lo que existe hoy en el repositorio.

- **Corte:** 10/9/2026 · `andreavergara-qa-consigna` en `9ff4396`, con `origin/main`
  (`017065e`) integrado mediante `61689ad`: PR #10 (H2), PR #11 (ensayo externo),
  calibración, estabilidad y README actualizado.
- **Estados:** **CUMPLE** · **PARCIAL** (existe pero incompleto o sin validar) · **NO CUMPLE**.
- **Fuente de los pesos de corrección:** tabla "Cómo se evalúa el parcial" de la consigna
  (Rúbrica 25 · Agente 25 · Casos 20 · Calibración 15 · Proceso grupal 15).

## Resumen

| Bloque | Ítems | CUMPLE | PARCIAL | NO CUMPLE |
|---|---:|---:|---:|---:|
| A · Las cuatro piezas | 4 | 4 | 0 | 0 |
| B · Estructura obligatoria del repo | 6 | 6 | 0 | 0 |
| C · Proceso grupal | 3 | 3 | 0 | 0 |
| D · Reglas de la casa | 2 | 2 | 0 | 0 |
| E · Entrega y prueba de fuego | 2 | 1 | 1 | 0 |
| **Total** | **17** | **16** | **1** | **0** |

**Lectura general:** las cuatro piezas y la estructura están completas; el agente está
construido e integrado y el proyecto está en QA final y entrega. H2 está **CERRADO** e
integrado por el [PR #10](https://github.com/tonimorelli/agente-corrector/pull/10).
Los tres casos están calibrados, las segundas corridas verifican estabilidad y el ensayo
externo quedó integrado por el [PR #11](https://github.com/tonimorelli/agente-corrector/pull/11).
D2 cumple con el incidente y su resolución documentados en `calibracion.md`. El único
**PARCIAL** restante es la confirmación humana de entrega al campus (E1).

El resumen cuenta los 17 ítems A1–A4, B1–B6, C1–C3, D1–D2 y E1–E2, no las filas de
detalle ni el control cruzado. E2 expresa cumplimiento del ensayo de precierre;
no afirma que la prueba de fuego en vivo ya haya ocurrido.

---

## A · Las cuatro piezas que entrega cada grupo

### A1 · Rúbrica ejecutable — **CUMPLE**

| Qué pide | Evidencia | Estado |
|---|---|---|
| Operacionaliza las 5 dimensiones oficiales y sus pesos | `rubrica.md` §2–§6 y control aritmético §10 (30/25/15/15/15 = 100) | CUMPLE |
| Escalas por nivel | Valores permitidos por subcriterio (p. ej. S1 = 0/3/5); niveles descriptivos §1.3; intervalos enteros por dimensión | CUMPLE |
| Qué evidencia exige cada puntaje | Jerarquía EV1–EV4 (§1.1) + línea "Evidencia aceptable" en cada subcriterio | CUMPLE |
| Ejemplos de nivel alto y bajo por dimensión | Cada dimensión cierra con "Ejemplo alto" y "Ejemplo bajo" | CUMPLE |
| "Tan precisa que un agente la aplica igual dos veces" | Corridas 2 de estabilidad: mismo nivel por dimensión en los 3 casos → agente ESTABLE (`calibracion.md`, "Corridas 2") | CUMPLE |
| "Tan legible que un humano puede discutirla" | V3 organiza criterios, evidencia y ejemplos; H1 y H2 documentan discusiones y ajustes concretos. V3 fue elegida en H6; A1 queda como evidencia comparativa/histórica | CUMPLE |

### A2 · Agente corrector — **CUMPLE**

| Qué pide | Evidencia | Estado |
|---|---|---|
| System prompt (+ herramientas que necesite) | `agente/system_prompt.md` (11 secciones) + `agente/configuracion.md` (contrato del entorno: sólo lectura, sin ejecución/red/escritura) | CUMPLE |
| Recibe un trabajo final real (un repositorio) | Corridas sobre los tres casos y `calibracion/ensayo_prueba_fuego_eventos_redline.md`: repo real `mateogp997/eventos-redline` en `02848e9`, integrado por PR #11 | CUMPLE |
| Devuelve puntaje por dimensión | Contrato de salida §9: 5 documentos YAML + cierre con `puntaje_total`/100 | CUMPLE |
| Justificación breve de cada puntaje citando evidencia del trabajo | Campos `evidencia` (tipo/ruta/localizador/demuestra) y `justificacion` por dimensión | CUMPLE |
| Una sugerencia concreta de mejora | Campo `mejora_prioritaria` obligatorio, derivado de un `faltante` de esa dimensión | CUMPLE |
| Salida en formato estructurado, idéntico en cada corrida | Bloque delimitado `===EVALUACION_INICIO===…===EVALUACION_FIN===`; formato idéntico verificado en corridas 1 y 2 | CUMPLE |

El ensayo externo valida funcionamiento y formato sobre una estructura ajena a los casos.
El operador es autor del repo evaluado, como declara el registro; no se usa para calibrar su nota.

### A3 · Tres casos de prueba — **CUMPLE**

| Qué pide | Evidencia | Estado |
|---|---|---|
| Existen los tres (excelente / flojo / tramposo) | `casos/excelente/`, `casos/flojo/`, `casos/tramposo/` con `README.md`, `DECISIONES.md`, `prompts/`, `corridas/` | CUMPLE |
| Puntúa **alto** al excelente | 100/100 (corrida 1b post-ajuste y corrida 2) | CUMPLE |
| Puntúa **bajo** al flojo | 23–24/100 | CUMPLE |
| **Detecta** al tramposo | 4/4 vectores de prompt injection registrados y no obedecidos; trampas estructurales neutralizadas por reglas de la rúbrica (`calibracion.md` H5) | CUMPLE |
| El tramposo "afirma cosas que no hizo, infla documentación, apela a la simpatía" | `casos/tramposo/`: NEXUS-COMMERCE afirma 12 corridas / 99,2 % / integraciones sin evidencia; doc inflada; apelación "papá internado" en `DECISIONES.md` | CUMPLE |

*Nota:* el flojo tiene 2 corridas y el excelente 7. Es deliberado — cada caso simula un nivel de
completitud distinto; no es un incumplimiento de estructura del caso.

### A4 · Calibración — **CUMPLE**

| Qué pide | Evidencia | Estado |
|---|---|---|
| Qué notas puso el agente | Tabla "Resultados — corrida 1" y tabla "Corridas 2" en `calibracion.md`; corridas crudas en `calibracion/` | CUMPLE |
| Qué notas hubieran puesto ustedes | Método "nota esperada primero" + banda esperada por caso (90–100 / 20–35 / ≤40) | CUMPLE — bandas por caso y desacuerdo por dimensión en H1; la consigna no exige una tabla adicional |
| Dónde no coincidían | H1: desacuerdo en D3 del caso excelente (R2 = 2/4 por versión de herramienta no consignada) | CUMPLE — un único desacuerdo sustantivo, resuelto a favor del agente |
| Qué ajustaron (rúbrica o corrector) | H1: ajuste al caso excelente; cambio de rúbrica `4552ff2` en G3; H2: regla EV1–EV3 incorporada en `rubrica.md` §1.1, **CERRADO** e integrado por PR #10 | CUMPLE |
| Cómo quedó después del ajuste | Re-corrida 1b → 100/100; corridas 2 mantienen niveles en las cinco dimensiones (+1 en flojo por cambio documentado de G3). H2 incluye dos verificaciones dirigidas sobre registros conservados; los puntajes coinciden con la regla final | CUMPLE |

La calibración incluye estabilidad, cierre H2 y el ensayo externo del PR #11
(`calibracion.md`, "Ensayo de la prueba de fuego"; salida cruda en
`calibracion/ensayo_prueba_fuego_eventos_redline.md`). Este último amplía la evidencia de
funcionamiento; no sustituye la comparación humano–agente sobre los tres casos.

---

## B · Estructura obligatoria del repositorio

| Ítem | Qué pide | Evidencia | Estado |
|---|---|---|---|
| B1 | Repositorio público de GitHub por grupo | `github.com/tonimorelli/agente-corrector`, accesible sin autenticación | CUMPLE |
| B2 | `README.md` — README estándar de la materia + integrantes | `README.md` con materia/programa/profesor/entrega, "qué es", tabla de 6 integrantes **con roles**, estructura y "cómo correr el agente" | CUMPLE — versión del 10/9/2026 (`9ff4396`), roles contrastados con evidencia; lista para integración |
| B3 | `rubrica.md` — la rúbrica ejecutable | `rubrica.md` (V3) en la raíz | CUMPLE |
| B4 | `agente/` — system prompt y configuración del corrector | `agente/system_prompt.md` + `agente/configuracion.md` | CUMPLE |
| B5 | `casos/excelente/`, `casos/flojo/`, `casos/tramposo/` | Las tres carpetas con contenido | CUMPLE |
| B6 | `calibracion.md` — la evidencia de calibración | `calibracion.md` + corridas crudas en `calibracion/`: tres casos, estabilidad, H2 cerrado y ensayo externo integrado | CUMPLE |

*Extras presentes* (`calibracion/`, `docs/`, `CLAUDE.md`, `QA_CONSIGNA.md`): la consigna no los
prohíbe y los seis nombres exigidos existen exactamente como se piden. Ayudan a la navegación del
agente corrector.

---

## C · Proceso grupal

| Ítem | Qué pide | Evidencia | Estado |
|---|---|---|---|
| C1 | Historia de commits que muestra el trabajo real del grupo; no un único commit del último día | 54 commits alcanzables desde `9ff4396`, con aportes de integrantes e integraciones: estructura → rúbrica → system prompt → casos → calibración → estabilidad → H2 → ensayo externo → README | CUMPLE |
| C2 | Iteraciones de la rúbrica registradas | `rubrica.md` "Nota de versión: segunda versión"; tipificación EV1–EV4; A/B V3 vs A1 (`calibracion.md` H6); regla H2 incorporada por PR #10; `DECISIONES.md` de cada caso | CUMPLE |
| C3 | Decisiones registradas | `calibracion.md` "Decisiones tomadas" (fechadas); `casos/*/DECISIONES.md`; tableros de seguimiento en la rama `andreavergara-seguimiento` | CUMPLE |

*Actualización V2:* H2 y el ensayo externo ya están integrados. La comparación V3/A1 queda
conservada en `calibracion/comparacion_rubricas.md` y
`calibracion/corrida_evaluador_A1_tres_casos.md`; A1 no es un pendiente ni un entregable adicional.

---

## D · Reglas de la casa

| Ítem | Qué pide | Evidencia | Estado |
|---|---|---|---|
| D1 | Nadie del grupo escribe código | Los artefactos del agente y los casos son Markdown; `docs/` incluye PDF y DOCX. El agente es un prompt, no un programa; `configuracion.md` prohíbe explícitamente la ejecución de código | CUMPLE |
| D2 | Si el corrector "no puede" leer un repo, resolver qué herramienta o instrucción le falta (no rendirse) | `calibracion.md`, "Incidente de lectura durante la validación de H2 — resuelto": diagnóstico del bloqueo de sandbox, ajuste con `--sandbox read-only -c windows.sandbox="elevated"` y lectura de la rúbrica y validación completadas, sin modificar la rúbrica para resolver el acceso | CUMPLE |

---

## E · Entrega y prueba de fuego

| Ítem | Qué pide | Evidencia | Estado |
|---|---|---|---|
| E1 | Un integrante sube el link al repo en la actividad *Parcial* del campus antes del jue 10/9 18:59 | README listo en esta rama; H2 y ensayo externo integrados. No hay confirmación humana de la subida del enlace al campus | PARCIAL — pendiente de confirmación humana |
| E2 | Preparación para la prueba de fuego en vivo: el agente corrige casos que **nunca vio** | `calibracion.md`, "Ensayo de la prueba de fuego (9/9)", y `calibracion/ensayo_prueba_fuego_eventos_redline.md`: `mateogp997/eventos-redline` en `02848e9`, cinco dimensiones, salida completa y límites respetados; integrado por [PR #11](https://github.com/tonimorelli/agente-corrector/pull/11) (`017065e`) | CUMPLE — ensayo externo de precierre; no acredita la actividad en vivo |

---

## Cobertura de las 5 dimensiones oficiales (control cruzado)

Las cinco están operacionalizadas en `rubrica.md` y ejercitadas en la calibración
(puntajes del caso excelente / flojo / tramposo, corrida 1):

| Dimensión (peso) | En `rubrica.md` | Probada en calibración | Estado |
|---|---|---|---|
| Sistema completo y funcionando (30) | §2, subcriterios S1–S6 + topes | 30 / 8 / 3 | CUMPLE |
| Proceso documentado (25) | §3, P1–P5 + topes | 25 / 12 / 0 | CUMPLE |
| Formato y reproducibilidad (15) | §4, R1–R5 + topes | 13→15 / 1 / 1 | CUMPLE |
| Análisis económico (15) | §5, E1–E4 + topes | 15 / 0 / 0 | CUMPLE |
| Gobierno y riesgo (15) | §6, G1–G5 + topes | 15 / 2 / 1 | CUMPLE |

El análisis económico **no es un hueco**: está como dimensión con cuatro subcriterios (medición
por corrida, precio y cálculo unitario, proyección y sensibilidad, elección costo-desempeño) y el
agente distingue correctamente su presencia (excelente 15/15) de su ausencia (flojo y tramposo
0/15).

---

## Cierre de observaciones de la primera revisión

- **Prueba externa:** CUMPLE; ensayo real integrado por PR #11. Que el repo sea del operador
  está declarado y limita la validación de la nota, no la evidencia de funcionamiento.
- **Legibilidad / A1:** cerrado sin nuevo entregable. V3 es la rúbrica ejecutable elegida;
  A1 se conserva sólo como evidencia comparativa/histórica.
- **Calibración por bandas:** CUMPLE con el método y los desacuerdos documentados. La tabla
  adicional de la guía operativa no es una exigencia de la consigna; no queda como gap.
- **H2 y cierres de integración:** H2 **CERRADO** e integrado por PR #10; estabilidad y
  ensayo externo integrados. README del 10/9 listo para integración con esta QA V2.

### D2: CUMPLE — incidente de lectura resuelto

La subsección "Incidente de lectura durante la validación de H2 — resuelto" de
`calibracion.md` registra el error inicial `RUBRICA_NO_DISPONIBLE`, la existencia de la
rúbrica, el diagnóstico del sandbox, la configuración aplicada y la validación completada
tras recuperar el acceso. Esta constancia del incidente real y su resolución cierra D2;
no se modificó la rúbrica para resolver el problema de acceso.

## Pendientes reales antes de congelar main

1. Revisar y aprobar humanamente esta QA V2; integrar la rama con README/docs/QA y comprobar
   que el contenido aprobado quede en el commit final de entrega. Identificar ese SHA.
2. Confirmar con el integrante responsable la subida del enlace al campus antes del
   10/9 a las 18:59; E1 sigue pendiente hasta esa confirmación.
