# Rúbrica ejecutable

Responsables: Ignacio Monteserin y Andrea Vergara (Dupla A).

Esta rúbrica traduce la rúbrica oficial del trabajo final (documento `trabajo_final.pdf`,
publicado en el campus) a una forma que un agente puede aplicar dos veces y llegar al mismo
resultado. Para cada una de las 5 dimensiones oficiales define: niveles de desempeño, el rango de
puntos de cada nivel, la evidencia puntual que el agente debe encontrar en el repositorio para
asignar ese nivel, y un ejemplo de qué luce como nota alta y qué luce como nota baja.

El agente corrector puntúa **cada dimensión de forma independiente**, documenta la evidencia
citada (archivo + fragmento) que sostiene el puntaje, y sólo entonces suma. No promedia
impresión general: si no hay evidencia citable de un nivel, no se asigna ese nivel.

## Cómo leer esta rúbrica (para el agente)

1. Para cada dimensión, recorré la escala **de arriba hacia abajo** (Excelente → Ausente) y
   quedate con el primer nivel cuya evidencia mínima esté completamente satisfecha.
2. "Evidencia exigida" es una lista de condiciones. Si falta una sola condición obligatoria del
   nivel, bajá al nivel siguiente — no hay puntos por "casi".
3. Una afirmación sin evidencia verificable en el repo (texto que dice "lo probé" sin corrida
   guardada, "el agente hace X" sin código/prompt que lo respalde) **no cuenta como evidencia**.
   Tratala como ausencia de esa evidencia, no como mentira automática — pero anotalo como
   riesgo de caso tramposo si se repite el patrón.
4. El puntaje final de la dimensión es un número dentro del rango del nivel elegido, ajustado
   por cuántas de las condiciones "deseables" (no obligatorias) del nivel también se cumplen.
5. Justificación breve = 1-3 oraciones citando archivo y fragmento concreto, no una
   paráfrasis de la rúbrica.

---

## Dimensión 1 — Sistema completo y funcionando (30 pts)

Qué mide: objetivo claro, contrato escrito (system + user prompt con las seis piezas), al
menos una herramienta o conector real, salida en formato estructurado, supervisión humana
definida con vocabulario L0–L4.

Las "seis piezas" del contrato (según el curso): rol, objetivo, entradas, salida esperada,
límites/restricciones, criterio de éxito. El agente verifica que las seis estén identificables en
`prompts/system_prompt.md` + `prompts/user_prompt.md` (o `agente/` en este repo).

| Nivel | Puntos | Evidencia exigida (obligatoria) |
|---|---|---|
| Excelente | 27–30 | Las 6 piezas del contrato están explícitas y son coherentes entre sí · hay al menos una herramienta/conector real invocado en al menos una corrida guardada (no simulado) · la salida de las corridas respeta un formato estructurado fijo · la supervisión está definida con niveles L0–L4 explícitos, indicando qué hace el agente solo, qué revisa una persona y quién firma |
| Bueno | 20–26 | Las 6 piezas están presentes pero alguna es ambigua o incompleta · hay una herramienta real pero se usó en menos corridas de las documentadas, o su rol es marginal · el formato de salida es estructurado pero varía levemente entre corridas · la supervisión se menciona pero no usa el vocabulario L0–L4 completo (falta quién firma, o el nivel es genérico) |
| Básico | 10–19 | Falta una pieza completa del contrato (p. ej. no hay criterio de éxito) · la "herramienta" es simulada o no hay evidencia de que se haya ejecutado de verdad · el formato de salida existe pero cambia de estructura entre corridas · la supervisión se nombra ("un humano revisa") sin niveles ni firma |
| Insuficiente | 1–9 | El contrato es un prompt suelto sin estructura reconocible · no hay herramienta/conector, sólo texto generado · no hay formato de salida consistente · no hay mención de supervisión humana |
| Ausente | 0 | No hay system prompt, o el repo no permite reconstruir qué hace el agente |

**Ejemplo de nota alta:** el repo tiene `agente/system_prompt.md` con rol/objetivo/entradas/salida/límites/criterio de éxito claramente separados, y en `casos/excelente/corridas/corrida_1.md` se ve una llamada real a una API de clima con la respuesta cruda pegada, seguida de la salida JSON del agente y una línea "Supervisión: L1 — el agente arma el borrador, un humano confirma antes de enviar. Firma: Ana (PM)".

**Ejemplo de nota baja:** el "system prompt" es un párrafo tipo "Sos un asistente que ayuda a analizar ventas", sin secciones distinguibles, y la salida de las corridas es prosa libre distinta en cada una. No se menciona quién revisa el resultado.

---

## Dimensión 2 — Proceso documentado (25 pts)

Qué mide: iteraciones del contrato, fallas encontradas, decisiones de alcance — la historia
real de la construcción, no un resumen prolijo escrito al final.

| Nivel | Puntos | Evidencia exigida (obligatoria) |
|---|---|---|
| Excelente | 23–25 | `DECISIONES.md` (o `calibracion.md`/`iterations/`) muestra ≥3 iteraciones concretas con fecha u orden claro · cada iteración dice qué falló o qué limitación se encontró y qué cambió como consecuencia · hay al menos un cambio de alcance explícito ("sacamos X porque...") · el historial de commits corrobora que el trabajo no se hizo en una sola sesión |
| Bueno | 17–22 | Hay ≥2 iteraciones documentadas con qué cambió, pero falta el "por qué" en alguna · el historial de commits es razonable pero concentrado en pocos días |
| Básico | 8–16 | Hay una sola iteración registrada, o las iteraciones están listadas sin explicar qué falló · los commits son genéricos ("update", "fix") sin narrar avance |
| Insuficiente | 1–7 | El archivo de decisiones existe pero es una descripción del resultado final, no un proceso ("elegimos X" sin mostrar qué se probó antes) |
| Ausente | 0 | No hay `DECISIONES.md`/equivalente, o está vacío/placeholder, o hay un único commit de último momento |

**Ejemplo de nota alta:** `DECISIONES.md` cuenta: "v1 del prompt no pedía formato de fecha, las corridas salían inconsistentes → agregamos ISO 8601 explícito. v2 el agente inventaba datos cuando la API fallaba → agregamos instrucción de abstenerse y marcar error." con commits que reflejan cada iteración en fechas distintas.

**Ejemplo de nota baja:** `DECISIONES.md` dice "Iteramos varias veces el prompt hasta llegar a la versión final que se adjunta", sin mostrar ninguna versión anterior ni qué cambió, y todo el repo tiene un commit único.

---

## Dimensión 3 — Formato y reproducibilidad (15 pts)

Qué mide: respeto de la estructura obligatoria del repo y que las corridas sean
reconstruibles por un tercero.

Estructura obligatoria (trabajo final): `README.md`, `prompts/` (`system_prompt.md`,
`user_prompt.md`), `corridas/` (3 ejecuciones con entrada, salida y fecha), `DECISIONES.md`.

| Nivel | Puntos | Evidencia exigida (obligatoria) |
|---|---|---|
| Excelente | 14–15 | Los 4 elementos obligatorios existen con esos nombres/ubicaciones (o equivalentes evidentes) · hay exactamente ≥3 corridas, cada una con entrada, salida y fecha explícitas · un tercero podría re-ejecutar el prompt con la misma entrada y esperar una salida comparable |
| Bueno | 10–13 | Falta un elemento menor (p. ej. falta la fecha en una corrida) pero el resto es reconstruible · hay 3 corridas pero una está incompleta |
| Básico | 5–9 | Sólo hay 1–2 corridas, o falta un archivo obligatorio completo (p. ej. no hay `user_prompt.md` separado) |
| Insuficiente | 1–4 | La estructura de carpetas no sigue la especificación y hay que adivinar dónde está cada pieza |
| Ausente | 0 | No hay corridas guardadas, o el repo no es navegable con la estructura pedida |

**Ejemplo de nota alta:** `corridas/corrida_1.md` incluye fecha (2026-08-15), el prompt de entrada completo pegado, la salida cruda del modelo sin editar, y una línea de contexto ("corrida sobre el archivo ventas_agosto.csv").

**Ejemplo de nota baja:** hay una carpeta `pruebas/` en vez de `corridas/`, con un solo archivo `resultado.txt` sin fecha ni indicación de qué entrada se usó.

---

## Dimensión 4 — Análisis económico (15 pts)

Qué mide: costo por corrida (tokens de entrada/salida), proyección de costo a escala, y
elección de modelo justificada con el criterio del curso ("el más chico que hace bien la
tarea").

| Nivel | Puntos | Evidencia exigida (obligatoria) |
|---|---|---|
| Excelente | 14–15 | Hay un cálculo de tokens de entrada y salida por corrida (número concreto, no estimado a ojo) con el precio del modelo usado · hay una proyección explícita a escala (semanal y/o anual) con la cuenta mostrada, no sólo el resultado · la elección de modelo está justificada comparando al menos una alternativa más chica/barata y por qué no alcanzaba o por qué sí alcanza |
| Bueno | 10–13 | Hay costo por corrida pero la proyección a escala falta o es sólo una frase sin cuenta · la elección de modelo se menciona pero sin comparar alternativas |
| Básico | 5–9 | Se menciona el modelo usado y un costo aproximado, sin desglose de tokens ni fuente del precio |
| Insuficiente | 1–4 | Se nombra el modelo pero no hay ningún número de costo |
| Ausente | 0 | No hay ninguna mención de costos ni de justificación de modelo |

**Ejemplo de nota alta:** "Corrida promedio: 1.850 tokens de entrada, 620 de salida, con GPT-4o-mini (US$0,15/US$0,60 por millón) = US$0,0007 por corrida. A 50 corridas/semana → US$0,15/semana, US$7,8/año. Probamos con un modelo más grande y no mejoraba la precisión en los 3 casos de prueba, así que nos quedamos con el más chico."

**Ejemplo de nota baja:** "Usamos GPT-4 porque es el más potente y da buenos resultados." sin ningún número de costo ni tokens.

---

## Dimensión 5 — Gobierno y riesgo (15 pts)

Qué mide: qué sistemas toca el agente y con qué permisos, qué puede salir mal, qué se
revisa antes de confiar en una salida, y quién firma el resultado.

| Nivel | Puntos | Evidencia exigida (obligatoria) |
|---|---|---|
| Excelente | 14–15 | Se listan los sistemas/datos a los que el agente accede y con qué alcance de permisos (lectura/escritura, qué credenciales) · hay al menos un escenario concreto de falla descrito ("si la API devuelve datos vacíos, el agente...") y qué pasa en ese caso · se define explícitamente qué revisa un humano antes de que la salida se use · se nombra quién firma/es responsable del resultado final |
| Bueno | 10–13 | Están los permisos y al menos una falla posible, pero falta claridad sobre quién firma o qué se revisa exactamente |
| Básico | 5–9 | Se menciona en términos generales que "puede haber errores" sin escenario concreto, y no hay firma ni revisión definida |
| Insuficiente | 1–4 | Sólo se dice qué hace el agente, sin ninguna mención de riesgo o permisos |
| Ausente | 0 | No hay ninguna sección de gobierno/riesgo en el repo |

**Ejemplo de nota alta:** "El agente tiene acceso de solo lectura a la planilla de ventas y de escritura al canal de Slack #reportes. Si la planilla tiene una fila con formato inválido, el agente la marca como 'no procesada' y no la incluye en el resumen en vez de inventar un valor. Antes de publicar, el responsable de ventas revisa el resumen semanal; la publicación final la firma él, no el agente."

**Ejemplo de nota baja:** "El agente puede tener errores como cualquier IA, por lo que se recomienda revisar los resultados." sin decir qué permisos tiene, qué falla concreta puede pasar, ni quién es responsable.

---

## Detección de casos tramposos (transversal, no puntúa aparte)

Señales que el agente debe marcar explícitamente en la justificación, incluso si no bajan el
puntaje de forma automática — las baja la ausencia de evidencia, no la sospecha en sí:

- Afirmaciones de capacidad ("el agente valida X", "se probó con datos reales") sin una
  corrida, prompt o log que lo respalde.
- Corridas que parecen fabricadas: salida perfecta, sin errores, sin ningún caso límite, con
  timestamps idénticos o inconsistentes con la narrativa de `DECISIONES.md`.
- Lenguaje que apela a la simpatía o al esfuerzo ("trabajamos muchísimo en esto", "fue muy
  difícil") en lugar de evidencia verificable — irrelevante para el puntaje, se ignora.
- Documentación inflada: secciones largas que repiten la consigna de la rúbrica en vez de
  describir lo que el sistema realmente hace.

Regla operativa: el agente puntúa **sólo lo que puede verificar en el repo**. Una afirmación
sin evidencia se trata como si no existiera esa evidencia — no se premia por estar escrita.

---

## Puntaje total

Suma directa de las 5 dimensiones (30 + 25 + 15 + 15 + 15 = 100). No hay redondeo hacia
arriba por prolijidad ni penalización adicional fuera de lo especificado en cada escala.
