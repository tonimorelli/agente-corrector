# Rúbrica ejecutable del Trabajo Final

Responsables: Andrea Vergara e Ignacio Monteserin (Dupla A).

> **Nota de versión:** esta es la segunda versión de la rúbrica ejecutable, elaborada a partir de
> la revisión y mejora de la propuesta inicial.

Esta rúbrica operacionaliza las cinco dimensiones y los pesos de la rúbrica oficial. El agente
debe asignar puntos únicamente mediante los subcriterios de este documento: no puede elegir
libremente un número dentro de un rango ni compensar una falta con una impresión general.

## 1. Procedimiento obligatorio de evaluación

1. Inventariar los artefactos del repositorio antes de puntuar.
2. Evaluar cada subcriterio por separado y seleccionar uno de sus valores permitidos.
3. Registrar para cada valor mayor que cero evidencia con `ruta`, localizador (líneas, sección,
   clave o identificador de corrida) y una descripción breve de qué demuestra.
4. Buscar contradicciones entre documentación, configuración, prompts, código y corridas.
5. Sumar los subcriterios de cada dimensión.
6. Aplicar los topes (*score caps*) de la dimensión. El resultado de una dimensión es el menor
   entre la suma obtenida y todos los topes aplicables.
7. Sumar las cinco dimensiones. El máximo es 100 puntos.

Si la evidencia no está disponible, no es legible o no permite comprobar el requisito, se usa
el menor valor compatible. La carga de aportar evidencia corresponde al trabajo evaluado.

### 1.1 Jerarquía de evidencia

De mayor a menor fuerza:

1. **EV1 — Ejecución verificable:** artefacto ejecutable más entrada, salida o log crudo y datos
   suficientes para relacionarlos; idealmente, reejecución exitosa por el evaluador.
2. **EV2 — Artefacto técnico:** código, prompt, esquema, configuración, prueba automatizada,
   historial o archivo de dependencias inspeccionable.
3. **EV3 — Registro de ejecución:** corrida o log conservado con entrada, salida, fecha y
   configuración identificables, aunque el evaluador no pueda reejecutarlo.
4. **EV4 — Declaración:** README, explicación o tabla sin respaldo técnico independiente.

Una declaración EV4 puede probar decisiones, responsables o supuestos, pero **no prueba por sí
sola** que el sistema funciona, que una herramienta fue invocada, que una prueba ocurrió, que
un costo fue medido o que un control está implementado.

**Regla operativa EV1–EV3:** cuando la reejecución esté impedida por el entorno del evaluador, un registro completo que vincule inequívocamente artefacto ejecutable/prompt, entrada íntegra, configuración, salida cruda y resultado se considera equivalente a EV1 exclusivamente a efectos de S2 y E1. Esta equivalencia excepcional no modifica ni restringe la clasificación que corresponda aplicar en otros subcriterios conforme a la definición general de EV1–EV4. Si falta alguno de esos elementos o su vinculación inequívoca, el registro debe tratarse como EV3. Una restricción del entorno del evaluador no debe degradar por sí sola la evidencia aportada por el trabajo.

### 1.2 Reglas de evidencia y contradicción

- La evidencia debe demostrar el subcriterio; la mera existencia de un archivo no alcanza.
- Varias copias del mismo resultado cuentan como una sola corrida independiente.
- Una salida pegada manualmente sin entrada o configuración relacionada no prueba ejecución.
- Ante contradicción material prevalece, en este orden: EV1, EV2, EV3 y EV4.
- Una contradicción es **material** únicamente si coincide con alguno de estos patrones: (a)
  discrepancia entre lo declarado en README/prompt y la configuración observable, (b) discrepancia
  entre el formato prometido y el formato efectivamente producido, (c) discrepancia entre la
  cronología de artefactos (commits, fechas) y la narrativa de decisiones. Cualquier otra
  discrepancia se registra pero no dispara la regla de jerarquía EV1>EV2>EV3>EV4.
- Si dos fuentes de igual jerarquía se contradicen y no puede resolverse cuál es vigente, se usa
  el menor valor compatible y se registra `CONTRADICCION_NO_RESUELTA`.
- No se penaliza dos veces el mismo defecto, salvo que afecte requisitos distintos de manera
  independiente. Todo tope aplicado debe citar su causa.
- Un requisito marcado “cuando corresponda” no exige usar herramientas, credenciales o
  escritura si la tarea no los necesita. El evaluador debe justificar la no aplicabilidad; los
  puntos no se redistribuyen.
- “Cuando corresponda” aplica si el objetivo declarado en S1 requiere esa acción o dato para
  cumplir su función; el evaluador debe citar la línea de S1 que sustenta la no aplicabilidad.

### 1.3 Niveles descriptivos

Los niveles se derivan del puntaje exacto; no se usan para calcularlo.

| Nivel | Porcentaje del máximo de la dimensión |
|---|---:|
| Excelente | 90–100 % |
| Bueno | 70–89 % |
| Básico | 40–69 % |
| Insuficiente | 1–39 % |
| Ausente | 0 % |

Para evitar diferencias por redondeo, cada dimensión incluye sus intervalos enteros.

---

## 2. Dimensión 1 — Sistema completo y funcionando (30 puntos)

**Definición operacional:** existe un contrato reconstruible y evidencia técnica de que el
sistema realiza su objetivo con entradas representativas, produce salidas utilizables, integra
los componentes necesarios y asigna la supervisión adecuada al impacto.

### 2.1 Subcriterios

**S1. Contrato del agente — 0, 3 o 5 puntos**

- **5:** se identifican sin contradicción rol, objetivo, entradas, salida esperada,
  límites/restricciones y criterio observable de éxito.
- **3:** el objetivo, las entradas y la salida son reconstruibles, pero falta o es ambiguo uno o
  más de los otros tres elementos.
- **0:** no puede reconstruirse qué debe hacer el sistema, con qué entrada o qué debe entregar.
- Evidencia aceptable: EV2 en prompts/configuración. EV4 sólo puede complementar.

**S2. Funcionamiento del flujo principal — 0, 3, 6 u 8 puntos**

- **8:** al menos dos ejecuciones independientes y trazables completan el flujo principal con
  entradas representativas; sus salidas satisfacen el criterio de éxito definido.
- **6:** una ejecución trazable completa el flujo principal y satisface el criterio de éxito.
- **3:** hay salida registrada, pero falta trazabilidad completa entre entrada, configuración,
  ejecución y resultado, o el éxito sólo puede comprobarse parcialmente.
- **0:** no hay ejecución verificable o las ejecuciones fallan el objetivo principal.
- Evidencia aceptable: EV1 para 8; EV1 o EV3 suficientemente completo para 6; EV3 para 3.

**S3. Integraciones y herramientas necesarias — 0, 2 o 4 puntos**

- **4:** todas las integraciones necesarias para el objetivo tienen configuración identificable
  y al menos una invocación trazable con resultado o error controlado.
- **2:** la integración está implementada o registrada, pero su invocación no es completamente
  trazable, o falta comprobar un camino relevante.
- **0:** falta una integración necesaria, está simulada sin declararlo o sólo se afirma su uso.
- Evidencia aceptable: EV1 combinado con EV2 para 4; EV2 o EV3 incompleto para 2; EV4 sola no
  alcanza para ningún valor mayor que 0.
- Si el objetivo no requiere herramientas externas, se evalúa con la misma escala la integración
  entre los componentes internos indispensables y se documenta esa decisión.
- La necesidad de herramientas externas se determina exclusivamente por lo declarado en S1. Si S1
  no las menciona, se asume que no son necesarias.

**S4. Formato y validez de la salida — 0, 2 o 4 puntos**

- **4:** todas las corridas evaluables cumplen el formato declarado y, si existe un esquema,
  pasan su validación; contienen los campos necesarios para el objetivo.
- **2:** la salida es utilizable, pero hay una desviación menor que no altera su significado, o
  no existe una validación mecánica para un formato que la admite.
- **0:** la salida contradice el contrato, pierde información necesaria o no es procesable.
- Evidencia aceptable: EV1 (salidas reales evaluadas contra el formato declarado), complementado
  por EV2 si existe esquema formal de validación.

**S5. Casos límite y manejo de fallas — 0, 2 o 4 puntos**

- **4:** existe al menos un caso límite o de falla relevante ejecutado; el sistema se abstiene,
  informa o degrada de la manera definida, sin inventar éxito.
- **2:** la conducta ante fallas está implementada en prompt/código, pero no fue ejecutada, o
  se ejecutó un caso poco relevante.
- **0:** no hay conducta definida o una falla observada produce una salida engañosa.
- Evidencia aceptable: EV1 para 4; EV2 para 2.
- Es relevante el caso que corresponde a una entrada fuera del dominio declarado en S1 (dato
  faltante, formato inválido, entrada vacía, fallo de herramienta) o a un riesgo listado en G2.
  Todo otro caso ejecutado se considera poco relevante.

**S6. Supervisión y responsabilidad — 0, 2 o 5 puntos**

- **5:** se especifica qué puede hacer el agente autónomamente, qué condición obliga revisión,
  qué verifica la persona y qué rol aprueba el uso de la salida; las corridas no contradicen el
  circuito. Puede expresarse con L0–L4 u otro vocabulario inequívoco.
- **2:** se requiere revisión humana, pero falta el objeto de revisión, el disparador o el rol
  responsable.
- **0:** no hay supervisión definida cuando el resultado puede producir una decisión o acción,
  o se atribuye responsabilidad final al agente.
- Evidencia aceptable: EV2 (especificación explícita), verificada contra EV1 o EV3 (corridas) para
  descartar contradicción.

### 2.2 Topes de la dimensión

- Sin contrato reconstruible (`S1 = 0`): máximo **9/30**.
- Sin evidencia de ejecución del flujo principal (`S2 = 0`): máximo **12/30**.
- El flujo principal falla o la salida afirma éxito ante una falla crítica: máximo **9/30**.
- Una acción externa irreversible o de alto impacto puede ejecutarse sin control humano
  explícito: máximo **15/30**.

Niveles: Excelente 27–30; Bueno 21–26; Básico 12–20; Insuficiente 1–11; Ausente 0.

**Ejemplo alto (30):** contrato completo en prompts; dos corridas trazables cumplen criterios de
éxito; una invocación real queda registrada; el JSON valida contra su esquema; un caso de datos
vacíos devuelve estado de abstención; una persona revisa campos definidos antes de publicar.

**Ejemplo bajo (3–9):** el README afirma que el agente analiza ventas y usa una API, pero sólo
hay una respuesta en prosa sin entrada, log ni configuración; no puede probarse funcionamiento,
formato estable, manejo de errores ni responsable de aprobación.

---

## 3. Dimensión 2 — Proceso documentado (25 puntos)

**Definición operacional:** el repositorio permite reconstruir una secuencia auténtica de
problema observado, decisión tomada, cambio realizado y efecto comprobado. El historial Git es
evidencia corroborante, no requisito de haber trabajado en días diferentes.

### 3.1 Subcriterios

**P1. Secuencia de iteraciones — 0, 3 o 5 puntos**

- **5:** hay tres o más iteraciones ordenadas, con artefacto o versión identificable.
- **3:** hay dos iteraciones ordenadas y vinculadas a artefactos.
- **0:** sólo se presenta el resultado final o una lista sin versiones distinguibles.
- Evidencia aceptable: EV2 o EV3 (artefacto o versión con identificador verificable); EV4 sola no
  cuenta como iteración.

**P2. Problemas y evidencia de diagnóstico — 0, 2 o 5 puntos**

- **5:** al menos dos iteraciones registran una falla, limitación o hipótesis y citan la corrida,
  prueba u observación que la reveló.
- **2:** se explican problemas concretos, pero sólo uno tiene evidencia vinculada.
- **0:** se afirma que “se iteró” sin describir problemas observados.
- Evidencia aceptable: EV4 (narrativa) debe estar vinculada a EV1, EV2 o EV3 (la corrida u
  observación citada); EV4 aislada no alcanza ningún valor mayor que 0.
- Cuenta como hipótesis registrada sólo si el texto identifica (i) qué se observó como problema y
  (ii) a qué corrida, prueba o artefacto específico se atribuye esa observación. Si falta (i) o
  (ii), no cuenta como tal aunque use la palabra “hipótesis”.

**P3. Decisiones y cambios trazables — 0, 3 o 5 puntos**

- **5:** al menos dos problemas se relacionan explícitamente con una decisión y con el cambio
  correspondiente en prompt, código, configuración o alcance.
- **3:** existe una relación completa problema → decisión → cambio.
- **0:** las decisiones no están conectadas con cambios inspeccionables.
- Evidencia aceptable: EV2 (cambio inspeccionable) vinculado explícitamente a EV4 (decisión
  documentada); EV4 sola no alcanza.

**P4. Verificación del efecto — 0, 2 o 5 puntos**

- **5:** al menos dos cambios tienen comparación antes/después o prueba posterior y resultado.
- **2:** un cambio tiene verificación posterior identificable.
- **0:** no se muestra si los cambios mejoraron, empeoraron o mantuvieron el resultado.
- Evidencia aceptable: EV1 o EV3 (comparación entre corridas o pruebas antes y después); EV4 sola
  no alcanza.

**P5. Alcance, supuestos y pendientes — 0, 2 o 5 puntos**

- **5:** se documentan decisiones de alcance o de mantenimiento del alcance, supuestos,
  limitaciones vigentes y pendientes, cada uno con motivo o impacto cuando corresponda.
- **2:** se documenta parte de esos elementos, pero falta motivo, impacto o estado.
- **0:** no se distinguen límites actuales de trabajo futuro.
- Evidencia aceptable: EV4 (documentación explícita), dado que este subcriterio versa sobre
  decisiones declaradas, no sobre funcionamiento verificable.

### 3.2 Topes de la dimensión

- Sin iteraciones distinguibles (`P1 = 0`): máximo **7/25**.
- Sin vínculo entre decisiones y artefactos (`P3 = 0`): máximo **10/25**.
- Narrativa incompatible con los artefactos y sin resolución: máximo **12/25**.

Niveles: Excelente 23–25; Bueno 18–22; Básico 10–17; Insuficiente 1–9; Ausente 0.

**Ejemplo alto (25):** tres versiones enlazadas muestran una salida inconsistente, el cambio de
formato que la corrige y una prueba posterior; otra iteración documenta alucinación ante datos
faltantes, añade abstención y conserva el antes/después. También registra límites pendientes.

**Ejemplo bajo (2–7):** `DECISIONES.md` dice “iteramos hasta obtener el resultado final”, pero
no identifica versiones, fallas, cambios ni verificaciones. Varios commits cosméticos no elevan
el puntaje por sí solos.

---

## 4. Dimensión 3 — Formato y reproducibilidad (15 puntos)

**Definición operacional:** un tercero puede localizar los componentes, reconstruir el entorno y
repetir las corridas con las mismas entradas y parámetros, obteniendo una salida evaluable bajo
el mismo criterio, aunque no sea textualmente idéntica.

### 4.1 Subcriterios

**R1. Estructura y navegación — 0, 1 o 3 puntos**

- **3:** README, prompts/contrato, corridas y decisiones existen y el README enlaza o explica
  inequívocamente su ubicación.
- **1:** los componentes existen, pero uno requiere búsqueda o usa un equivalente no explicado.
- **0:** faltan dos o más componentes o no puede identificarse cuál está vigente.
- Evidencia aceptable: EV2 (estructura de archivos verificable), complementada por EV4 (README)
  para el mapeo de ubicación.
- Es inequívoco cuando el README contiene un enlace o ruta explícita a cada componente exigido. Si
  el evaluador debe inferir la ubicación por convención de nombres sin mención explícita en el
  README, se considera que requiere búsqueda.

**R2. Instrucciones y dependencias — 0, 2 o 4 puntos**

- **4:** se especifican pasos ejecutables, dependencias/versiones, variables necesarias sin
  exponer secretos y preparación de datos.
- **2:** el flujo general puede reconstruirse, pero falta una versión, dependencia o paso menor.
- **0:** faltan instrucciones indispensables o requieren conocimiento no documentado.
- Evidencia aceptable: EV2 (instrucciones y archivo de dependencias inspeccionables).

**R3. Registro de corridas — 0, 2 o 4 puntos**

- **4:** hay al menos tres corridas independientes, cada una con identificador/fecha, entrada o
  referencia inmutable, salida cruda y resultado/estado.
- **2:** hay dos corridas completas, o tres con un campo obligatorio ausente en alguna.
- **0:** hay menos de dos corridas reconstruibles.
- Evidencia aceptable: EV1 si la corrida es reejecutable; EV3 si sólo es registro conservado con
  los campos exigidos.

**R4. Configuración de ejecución — 0, 1 o 2 puntos**

- **2:** cada corrida identifica modelo/versión y los parámetros que pueden afectar el resultado;
  si una plataforma no expone un dato, se registra como `NO_DISPONIBLE`.
- **1:** se identifica modelo, pero faltan parámetros relevantes.
- **0:** no puede saberse con qué configuración se generaron las salidas.
- Evidencia aceptable: EV2 o EV3 (dato de configuración identificable junto a la corrida).

**R5. Criterio de reproducción — 0, 1 o 2 puntos**

- **2:** se define qué campos, propiedades o métricas deben mantenerse y la tolerancia admitida;
  al menos una reproducción se compara con ese criterio.
- **1:** existe criterio objetivo, pero no una reproducción comparada.
- **0:** “resultado similar/comparable” no está operacionalizado.
- Evidencia aceptable: EV2 para el criterio definido; EV1 o EV3 para la reproducción comparada
  contra ese criterio.

### 4.2 Topes de la dimensión

- Menos de dos corridas reconstruibles (`R3 = 0`): máximo **4/15**.
- Sin instrucciones indispensables (`R2 = 0`): máximo **6/15**.
- Secretos reales incluidos en archivos o historial: máximo **4/15**, además de marcar
  `SECRETO_EXPUESTO` y omitir su valor de la devolución.

Niveles: Excelente 14–15; Bueno 11–13; Básico 6–10; Insuficiente 1–5; Ausente 0.

**Ejemplo alto (15):** README navegable, instalación versionada, variables de entorno de ejemplo,
tres corridas con entradas y salidas crudas, configuración identificada y un criterio que acepta
variaciones de redacción pero exige campos y totales numéricos iguales dentro de una tolerancia.

**Ejemplo bajo (1–4):** existe un único `resultado.txt` sin entrada, fecha, modelo ni pasos de
ejecución. El README afirma que cualquiera puede reproducirlo, pero no aporta instrucciones.

---

## 5. Dimensión 4 — Análisis económico (15 puntos)

**Definición operacional:** los costos relevantes se calculan con unidades, fuentes y supuestos
trazables; se proyectan a un volumen definido y la elección de modelo/arquitectura relaciona costo
con desempeño observado.

### 5.1 Subcriterios

**E1. Medición por corrida — 0, 1 o 3 puntos**

- **3:** se registran unidades consumidas por corrida (por ejemplo, tokens de entrada/salida y
  llamadas a herramientas) obtenidas de logs, API o método reproducible.
- **1:** se usa una estimación explicada sobre entradas representativas.
- **0:** no hay medición ni método de estimación.
- Evidencia aceptable: EV1 o EV2 para 3; EV4 con método de estimación explicado para 1.

**E2. Precio y cálculo unitario — 0, 2 o 4 puntos**

- **4:** fuente, fecha, moneda, modelo/servicio y precios por unidad están citados; la fórmula es
  correcta y separa componentes con tarifas distintas.
- **2:** el cálculo es reconstruible, pero falta fuente/fecha o un costo menor.
- **0:** sólo se declara un costo final o el cálculo usa un modelo/precio incompatible.
- Evidencia aceptable: EV2 (fórmula y cálculo inspeccionables); EV4 aceptable únicamente para la
  cita de fuente y fecha de precios.

**E3. Proyección y sensibilidad — 0, 2 o 4 puntos**

- **4:** proyecta volumen por período mostrando fórmula y supuestos, e incluye al menos un
  escenario alternativo relevante (volumen, longitud, errores, revisión o herramienta).
- **2:** existe una proyección correcta con fórmula, pero sin sensibilidad.
- **0:** no hay proyección reconstruible.
- Evidencia aceptable: EV2 (fórmula y supuestos inspeccionables).

**E4. Elección costo-desempeño — 0, 2 o 4 puntos**

- **4:** compara al menos dos opciones bajo las mismas entradas y criterio de éxito, conserva
  evidencia de resultados y justifica la opción elegida por costo y calidad.
- **2:** explica la elección con datos parciales o una comparación no completamente controlada.
- **0:** usa afirmaciones como “más potente” o “más barato” sin evaluación vinculada.
- Evidencia aceptable: EV1 o EV3 (resultados conservados de ambas opciones bajo las mismas
  entradas).
- Es completamente controlada cuando ambas opciones se evalúan con el mismo conjunto de entradas y
  el mismo criterio de éxito de S1. Cualquier variación en entradas, criterio o cantidad de
  corridas entre opciones la vuelve no controlada.

### 5.2 Topes de la dimensión

- Sin cálculo unitario reconstruible (`E2 = 0`): máximo **4/15**.
- Modelo o servicio costeado distinto del usado, sin reconciliación: máximo **7/15**.
- Cifras aritméticamente incompatibles con sus propios supuestos: máximo **7/15**.

Niveles: Excelente 14–15; Bueno 11–13; Básico 6–10; Insuficiente 1–5; Ausente 0.

**Ejemplo alto (15):** logs registran tokens por corrida; una fuente fechada aporta tarifas; la
fórmula separa entrada, salida y herramienta; se proyectan escenarios base y pico; dos modelos se
comparan con las mismas pruebas y se elige el menor costo que alcanza el umbral de calidad.

**Ejemplo bajo (1–4):** “usamos el modelo X porque es económico” sin consumo, fuente, fórmula,
volumen ni comparación verificable.

---

## 6. Dimensión 5 — Gobierno y riesgo (15 puntos)

**Definición operacional:** están identificados activos, accesos, fallas relevantes, controles,
supervisión y responsables; los controles declarados son compatibles con la configuración y con
el impacto de las acciones del sistema.

### 6.1 Subcriterios

**G1. Sistemas, datos y permisos — 0, 1 o 3 puntos**

- **3:** presenta un inventario de sistemas y categorías de datos, especifica lectura/escritura, alcance mínimo
  y mecanismo de credenciales sin revelar secretos; coincide con la implementación observable.
- **1:** inventario parcial o permisos descritos genéricamente.
- **0:** no puede determinarse qué accede o las declaraciones contradicen la configuración.
- Evidencia aceptable: EV4 (inventario declarado) contrastado con EV2 (configuración o permisos
  observables); prevalece EV2 ante discrepancia.

**G2. Riesgos priorizados — 0, 1 o 3 puntos**

- **3:** documenta al menos dos escenarios relevantes con causa, consecuencia e impacto o
  prioridad; incluye privacidad/seguridad cuando corresponda.
- **1:** menciona un escenario concreto, pero sin consecuencia o prioridad.
- **0:** sólo afirma que “la IA puede equivocarse”.
- Evidencia aceptable: EV4 (documentación de riesgos con causa, consecuencia e impacto).

**G3. Controles y comportamiento seguro — 0, 1 o 3 puntos**

- **3:** cada riesgo prioritario tiene prevención/detección y respuesta; al menos un control es
  visible en prompt, código, configuración o corrida.
- **1:** hay mitigaciones documentadas, pero ninguna se comprueba o queda un riesgo prioritario
  sin respuesta.
- **0:** no hay mitigaciones accionables o el sistema oculta la falla.
- Evidencia aceptable: EV1, EV2 o EV3 (control visible en ejecución, código/configuración o
  registro de corrida) para 3; EV4 sola —mitigación documentada sin comprobar— alcanza como
  máximo 1 y nunca 3.

**G4. Supervisión, aprobación y escalamiento — 0, 1 o 3 puntos**

- **3:** define qué revisa la persona, cuándo interviene, qué rol aprueba y cómo se escala una
  excepción, de modo proporcional al impacto.
- **1:** menciona revisión humana, pero faltan objeto, disparador, rol o escalamiento.
- **0:** no hay supervisión para decisiones/acciones relevantes.
- Evidencia aceptable: EV2 (especificación explícita), verificada contra EV1 o EV3 para descartar
  contradicción.
- Si la acción puede tener efectos externos irreversibles, la supervisión exige aprobación previa
  de un rol humano identificado; si los efectos son internos y reversibles, alcanza con revisión
  posterior. Todo control que no alcance el nivel correspondiente a esta clasificación se
  considera no proporcional.

**G5. Responsabilidad, auditoría y reversibilidad — 0, 1 o 3 puntos**

- **3:** asigna dueño del sistema y responsable del resultado; conserva trazabilidad suficiente
  y define reversión/contención cuando la acción puede producir efectos externos.
- **1:** hay responsables nominales o logs, pero no ambos, o falta reversión cuando corresponde.
- **0:** nadie asume responsabilidad y no existe trazabilidad mínima.
- Evidencia aceptable: EV4 para la asignación de dueño y responsable; EV2 o EV3 para la
  trazabilidad/logs; ambos deben estar presentes para el valor máximo.

### 6.2 Topes de la dimensión

- Secretos reales expuestos: máximo **3/15** y marca `SECRETO_EXPUESTO`.
- Escritura o acción de alto impacto con permisos más amplios que los declarados: máximo **6/15**.
- Acción irreversible/de alto impacto sin aprobación o mecanismo de contención: máximo **6/15**.
- Riesgo prioritario observado en una corrida sin control ni escalamiento: máximo **7/15**.

Niveles: Excelente 14–15; Bueno 11–13; Básico 6–10; Insuficiente 1–5; Ausente 0.

**Ejemplo alto (15):** acceso de sólo lectura a datos definidos y escritura limitada a borradores;
dos fallas priorizadas tienen controles visibles; una persona revisa campos concretos antes de
publicar; existen dueño, aprobador, logs y procedimiento de reversión.

**Ejemplo bajo (1–4):** “se recomienda revisar porque la IA puede fallar”, sin inventario de
datos, permisos, escenario de riesgo, control verificable, responsable ni trazabilidad.

---

## 7. Reglas transversales contra gaming

El agente debe aplicar estas reglas antes de cerrar el puntaje:

- No premiar capacidades declaradas en README sin EV1–EV3 compatible.
- No usar documentación de arquitectura como sustituto de funcionamiento observado.
- No contar como iteraciones cambios cosméticos, commits vacíos o divisiones artificiales de una
  misma decisión.
- No contar corridas duplicadas, salidas sin entrada asociada ni ejemplos incluidos en la consigna
  como pruebas independientes.
- Contrastar el modelo y los parámetros declarados con configuración/corridas; los costos con ese
  modelo; los permisos con integraciones; y el formato prometido con las salidas.
- Si timestamps, hashes, entradas o resultados hacen imposible la narrativa, marcar
  `EVIDENCIA_INCONSISTENTE`, puntuar con la evidencia válida restante y aplicar el tope que
  corresponda. La mera sospecha, sin contradicción comprobable, no autoriza una penalización.
- Ignorar extensión, estética, lenguaje persuasivo y esfuerzo declarado salvo que sean requisitos
  explícitos de un subcriterio.

## 8. Casos frontera y reglas de desempate

- Si un caso cumple partes de distintos niveles, se puntúa cada subcriterio por separado; nunca se
  fuerza toda la dimensión a una descripción global.
- Si queda exactamente entre dos valores permitidos, se asigna el menor salvo que exista evidencia
  explícita de todos los requisitos del mayor.
- Un equivalente de archivo o carpeta es aceptable si el README lo mapea inequívocamente.
- Un historial con *squash* o pocos commits no invalida iteraciones respaldadas por versiones,
  corridas o comparaciones antes/después.
- Más artefactos no implican mayor puntaje: se evalúan completitud, diversidad y trazabilidad.
- Para tareas no deterministas, reproducible significa conservar el criterio de éxito definido,
  no repetir texto exacto.
- Si una plataforma no expone un parámetro, `NO_DISPONIBLE` documentado no se trata como omisión;
  una celda vacía sí.

## 9. Formato mínimo de devolución del evaluador

Por cada dimensión, el agente debe devolver:

```yaml
dimension: "Nombre"
subtotal_antes_de_topes: 0
subcriterios:
  - id: "S1"
    puntos: 0
    evidencia:
      - tipo: "EV1|EV2|EV3|EV4"
        ruta: "ruta/archivo"
        localizador: "líneas, sección, clave o corrida"
        demuestra: "hecho observado"
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 0
nivel: "Ausente|Insuficiente|Básico|Bueno|Excelente"
justificacion: "Síntesis basada en evidencia"
```

Al final debe incluir `puntaje_total` sobre 100 y una lista de banderas transversales. No debe
mostrar secretos encontrados; sólo su ubicación y la marca `SECRETO_EXPUESTO`.

## 10. Control aritmético

| Dimensión | Máximo |
|---|---:|
| Sistema completo y funcionando | 30 |
| Proceso documentado | 25 |
| Formato y reproducibilidad | 15 |
| Análisis económico | 15 |
| Gobierno y riesgo | 15 |
| **Total** | **100** |

No hay redondeos, puntos por prolijidad ni penalizaciones implícitas. Todos los puntos provienen
de un valor permitido y toda reducción adicional proviene de un tope expresamente documentado.
