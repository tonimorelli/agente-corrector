# QA de cumplimiento — Consigna del parcial

Comparación punto por punto entre lo que pide la consigna del parcial
(`docs/parcial_agente_evaluador.pdf`) y lo que existe hoy en el repositorio.

- **Corte:** `main` en `0dce76f` (9/9/2026) + los cambios de esta rama (`docs/`, README, este archivo).
- **Estados:** **CUMPLE** · **PARCIAL** (existe pero incompleto o sin validar) · **NO CUMPLE**.
- **Fuente de los pesos de corrección:** tabla "Cómo se evalúa el parcial" de la consigna
  (Rúbrica 25 · Agente 25 · Casos 20 · Calibración 15 · Proceso grupal 15).

## Resumen

| Bloque | Ítems | CUMPLE | PARCIAL | NO CUMPLE |
|---|---:|---:|---:|---:|
| A · Las cuatro piezas | 4 | 3 | 1 | 0 |
| B · Estructura obligatoria del repo | 6 | 6 | 0 | 0 |
| C · Proceso grupal | 3 | 3 | 0 | 0 |
| D · Reglas de la casa | 2 | 1 | 1 | 0 |
| E · Entrega y prueba de fuego | 2 | 0 | 1 | 1 |
| **Total** | **17** | **13** | **4** | **1** |

**Lectura general:** los cinco entregables y la estructura están completos y probados sobre los
tres casos. El único **NO CUMPLE** es la prueba de fuego: no hay ninguna corrida del agente sobre
un repositorio externo que el grupo no haya construido. Los **PARCIAL** son cierres, no
construcción: legibilidad de la rúbrica, corrida externa del agente, incidente de "no puedo leer
el repo" sin documentar, y la subida del link al campus.

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
| "Tan legible que un humano puede discutirla" | La V3 es discutible pero densa (~30 KB). El grupo lo reconoció en H6 y propuso una A1 más corta como "resumen legible" | CUMPLE con reserva — ver Gap 2 |

### A2 · Agente corrector — **CUMPLE** (con reserva)

| Qué pide | Evidencia | Estado |
|---|---|---|
| System prompt (+ herramientas que necesite) | `agente/system_prompt.md` (11 secciones) + `agente/configuracion.md` (contrato del entorno: sólo lectura, sin ejecución/red/escritura) | CUMPLE |
| Recibe un trabajo final real (un repositorio) | 8 corridas registradas en `calibracion/` sobre los 3 casos, que son repos-trabajo completos | CUMPLE sobre los casos; sin validar sobre un repo externo — ver Gap 1 |
| Devuelve puntaje por dimensión | Contrato de salida §9: 5 documentos YAML + cierre con `puntaje_total`/100 | CUMPLE |
| Justificación breve de cada puntaje citando evidencia del trabajo | Campos `evidencia` (tipo/ruta/localizador/demuestra) y `justificacion` por dimensión | CUMPLE |
| Una sugerencia concreta de mejora | Campo `mejora_prioritaria` obligatorio, derivado de un `faltante` de esa dimensión | CUMPLE |
| Salida en formato estructurado, idéntico en cada corrida | Bloque delimitado `===EVALUACION_INICIO===…===EVALUACION_FIN===`; formato idéntico verificado en corridas 1 y 2 | CUMPLE |

*Reserva:* el contrato está completo y funciona de punta a punta, pero toda la evidencia es sobre
casos construidos por el grupo. La robustez sobre estructura no vista se mide en E2 y hoy no tiene
evidencia.

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
| Qué notas hubieran puesto ustedes | Método "nota esperada primero" + banda esperada por caso (90–100 / 20–35 / ≤40) | CUMPLE — es banda por caso, no tabla consensuada por dimensión (ver Gap 4) |
| Dónde no coincidían | H1: desacuerdo en D3 del caso excelente (R2 = 2/4 por versión de herramienta no consignada) | CUMPLE — un único desacuerdo sustantivo, resuelto a favor del agente |
| Qué ajustaron (rúbrica o corrector) | H1: ajuste **al caso** (se agregó la versión de la herramienta al README del excelente); cambio de rúbrica `4552ff2` en G3 documentado | CUMPLE |
| Cómo quedó después del ajuste | Re-corrida 1b → 100/100 sin topes ni banderas; corridas 2 confirman estabilidad | CUMPLE |

---

## B · Estructura obligatoria del repositorio

| Ítem | Qué pide | Evidencia | Estado |
|---|---|---|---|
| B1 | Repositorio público de GitHub por grupo | `github.com/tonimorelli/agente-corrector`, accesible sin autenticación | CUMPLE |
| B2 | `README.md` — README estándar de la materia + integrantes | `README.md` con materia/programa/profesor/entrega, "qué es", tabla de 6 integrantes **con roles**, estructura y "cómo correr el agente" | CUMPLE (actualizado en esta rama; antes decía "en construcción" y sin roles) |
| B3 | `rubrica.md` — la rúbrica ejecutable | `rubrica.md` (V3) en la raíz | CUMPLE |
| B4 | `agente/` — system prompt y configuración del corrector | `agente/system_prompt.md` + `agente/configuracion.md` | CUMPLE |
| B5 | `casos/excelente/`, `casos/flojo/`, `casos/tramposo/` | Las tres carpetas con contenido | CUMPLE |
| B6 | `calibracion.md` — la evidencia de calibración | `calibracion.md` + corridas crudas en `calibracion/` | CUMPLE |

*Extras presentes* (`calibracion/`, `docs/`, `CLAUDE.md`, `QA_CONSIGNA.md`): la consigna no los
prohíbe y los seis nombres exigidos existen exactamente como se piden. Ayudan a la navegación del
agente corrector.

---

## C · Proceso grupal

| Ítem | Qué pide | Evidencia | Estado |
|---|---|---|---|
| C1 | Historia de commits que muestra el trabajo real del grupo; no un único commit del último día | 42 commits entre el 30/8 y el 9/9, 7 identidades de autor (los 6 integrantes por su usuario de GitHub + la co-autoría de la herramienta); evolución visible: estructura → rúbrica v1 → tipificación EV1–EV4 → system prompt → casos → calibración → estabilidad | CUMPLE |
| C2 | Iteraciones de la rúbrica registradas | `rubrica.md` "Nota de versión: segunda versión"; commit de tipificación EV1–EV4; A/B V3 vs A1 (`calibracion.md` H6); ajuste H1; `DECISIONES.md` de cada caso | CUMPLE |
| C3 | Decisiones registradas | `calibracion.md` "Decisiones tomadas" (fechadas); `casos/*/DECISIONES.md`; tableros de seguimiento en la rama `andreavergara-seguimiento` | CUMPLE |

*Observación:* parte del proceso (H2, A1, tableros) vive en ramas no mergeadas. No afecta el
cumplimiento de C, pero conviene que el proceso relevante quede referenciado desde `main` antes de
congelar.

---

## D · Reglas de la casa

| Ítem | Qué pide | Evidencia | Estado |
|---|---|---|---|
| D1 | Nadie del grupo escribe código | El repo es 100 % Markdown; el agente es un prompt, no un programa; `configuracion.md` prohíbe explícitamente la ejecución de código | CUMPLE |
| D2 | Si el corrector "no puede" leer un repo, resolver qué herramienta o instrucción le falta (no rendirse) | Contemplado en el diseño: `configuracion.md` define las capacidades exigidas al entorno; `system_prompt.md` §4 define el bloque de error `RUBRICA_NO_DISPONIBLE`; H3/H3b tratan rutas de salida. Pero **no hay una corrida documentada** de un incidente real de lectura resuelto por ajuste de herramienta/instrucción | PARCIAL — ver Gap 3 |

---

## E · Entrega y prueba de fuego

| Ítem | Qué pide | Evidencia | Estado |
|---|---|---|---|
| E1 | Un integrante sube el link al repo en la actividad *Parcial* del campus antes del jue 10/9 18:59 | El repo es público y entregable. La subida del link al campus no está confirmada; README, este QA y la decisión de H2 todavía se están cerrando | PARCIAL — acción pendiente + cierres en curso |
| E2 | Prueba de fuego en vivo: el agente corrige casos que **nunca vio** | No existe ninguna corrida del agente sobre un repositorio externo real no construido por el grupo. `calibracion.md` lo lista como pendiente #1 y `calibracion.md` H4 anticipa que la estructura libre puede traer sorpresas | **NO CUMPLE** — ver Gap 1 |

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

## Gaps priorizados

### Gap 1 — Sin prueba sobre un repo externo (E2) · **P0**
- **Impacto:** es el único NO CUMPLE y pega en el criterio de mayor visibilidad — la prueba de
  fuego es pública y define qué agente corrige todos los finales.
- **Recomendación:** una corrida del evaluador sobre una Entrega 1 o 2 real que el grupo no
  construyó, guardada en `calibracion/` con encabezado de operador. Si no llega, dejar constancia
  explícita de la limitación en `calibracion.md`.

### Gap 2 — Legibilidad de la rúbrica / destino de A1 · **P1**
- **Impacto:** la consigna pide una rúbrica "legible para que un humano pueda discutirla". La V3
  cumple lo sustantivo pero es densa; la A1 pensada como resumen legible quedó fuera de `main`
  (PR #6 cerrado, vive en `andreavergara-rubrica-final-a1` y en un archivo suelto de la carpeta
  padre).
- **Recomendación:** decidir. Si A1 se entrega como resumen, incorporarla al repo (p. ej.
  `rubrica_resumen.md`) enlazada desde el README y `rubrica.md`. Si no, no hace falta acción.

### Gap 3 — Incidente "no puedo leer el repo" sin documentar (D2) · **P2**
- **Impacto:** la consigna valora explícitamente resolver esto ("la pregunta es qué herramienta o
  instrucción le falta"). Hubo un caso real (bloqueo `RUBRICA_NO_DISPONIBLE` por sandbox) que no
  quedó registrado en el repo.
- **Recomendación:** documentar en `calibracion.md` o en `agente/configuracion.md` el incidente y
  cómo se resolvió (permisos de lectura del entorno). Idealmente, una corrida corta que muestre el
  bloque de error `RUBRICA_NO_DISPONIBLE` funcionando y luego la corrida exitosa.

### Gap 4 — Calibración: comparación por banda, no por dimensión consensuada · **P2**
- **Impacto:** la calibración registra una banda esperada por caso y un único desacuerdo a nivel
  dimensión (H1). La guía operativa (Prompt 6) pedía una tabla humano-vs-agente por dimensión.
- **Recomendación:** si hay tiempo, agregar a `calibracion.md` la tabla por dimensión de al menos
  un caso (el que más se discutió). Si no, es defendible como está: "un desacuerdo honesto bien
  resuelto vale más que una calibración perfecta sin historia" (consigna).

### Gap 5 — Cierres de `main` antes de congelar (E1) · **P1**
- **Impacto:** README ya actualizado en esta rama; falta integrarla, mergear PR #8, resolver H2
  (incorporar o descartar), y actualizar `calibracion.md` con el resultado de la prueba de fuego.
- **Recomendación:** seguir el orden del tablero del 9/9; Antonio integra; identificar el commit
  final y no tocar más `main`.
