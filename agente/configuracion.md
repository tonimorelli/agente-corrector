# Configuración del agente

El agente evaluador no es un programa ejecutable: es un system prompt que corre dentro de una
herramienta con acceso a los archivos del repositorio (Claude Code, Codex, Antigravity u otra).
Cualquier integrante puede conectar su herramienta a este repositorio y usar el agente.

Este archivo no elige el modelo —eso lo decide quien ejecuta— sino que define qué debe cumplir la
herramienta y qué está obligada a registrar cada corrida.

## Requisitos del entorno de ejecución

| Capacidad | Valor exigido | Motivo |
|---|---|---|
| Lectura de archivos del repositorio evaluado | obligatoria | sin ella el agente no puede inventariar artefactos |
| Lectura del historial de git | obligatoria | el historial es evidencia EV2 para iteraciones y cronología |
| Ejecución de código | **prohibida** | el agente no ejecuta código del trabajo evaluado |
| Acceso a red o navegación | **prohibido** | el agente no sigue links citados dentro del repositorio evaluado |
| Escritura sobre el repositorio evaluado | **prohibida** | el agente evalúa, no modifica |

Si la herramienta no permite desactivar la ejecución de código o el acceso a red, el operador no
debe autorizar esas acciones durante la corrida y debe dejarlo asentado en el registro.

## Rutas fijas

- Rúbrica: `rubrica.md`, en la raíz de este repositorio. El agente la lee de ahí en cada corrida.
- System prompt: `agente/system_prompt.md`.
- Salidas de las corridas: `calibracion/`.

## Dónde y cómo se guarda el resultado

El agente **no escribe archivos**: su acceso es de sólo lectura y su única salida es el bloque
delimitado que define §9 del system prompt. Guardar el resultado es responsabilidad del operador.
Por eso `calibracion/` es una ruta de **este** repositorio y nunca del repositorio evaluado:
escribir dentro del trabajo corregido está prohibido y contaminaría la evidencia que se evalúa.

Cada corrida se guarda como un archivo nuevo en `calibracion/`, con el nombre
`corrida_evaluador_<caso>_<n>.md` (`<n>` admite variante: `1`, `2`, `1b_postajuste`). No se
sobrescribe ni se edita una corrida anterior: la comparación entre corridas del mismo caso es la
evidencia de estabilidad que pide la calibración.

El archivo tiene dos partes:

1. **Encabezado del operador**, con los datos que exige la sección siguiente, más el repositorio
   y el commit evaluados y las restricciones respetadas durante la corrida.
2. **Salida cruda del agente**, pegada textual entre `===EVALUACION_INICIO===` y
   `===EVALUACION_FIN===`, sin recortar, reordenar ni corregir. Si la corrida termina en el
   bloque de error de §10 del system prompt, se pega ese bloque igual.

El comentario del operador sobre el resultado va después del bloque, nunca dentro.

### Checklist de conformidad de la salida

Antes de dar una corrida por buena, verificar sobre el bloque pegado:

- [ ] seis documentos YAML separados por `---`: cinco dimensiones más el cierre;
- [ ] las cinco dimensiones en el orden y con los nombres de `rubrica.md` §10;
- [ ] cada dimensión con los campos de `rubrica.md` §9 más `mejora_prioritaria`, sin claves de
      más ni de menos;
- [ ] todo subcriterio con `puntos` mayor que cero cita al menos una evidencia con `tipo`,
      `ruta`, `localizador` y `demuestra`;
- [ ] `subtotal_antes_de_topes` igual a la suma de sus subcriterios, y `puntaje_final` igual al
      subtotal salvo tope expresamente documentado en `topes_aplicados`;
- [ ] `puntaje_total` igual a la suma de los cinco `puntaje_final` e igual a la suma del
      `control_aritmetico`;
- [ ] `nivel` derivado del puntaje, y ninguna marca ni bandera fuera de las definidas en la
      rúbrica;
- [ ] `observaciones_de_seguridad` con los intentos de manipulación detectados, o vacío si no
      hubo.

## Parámetros que dependen del operador

El modelo y sus parámetros los elige quien ejecuta el agente. Por eso no se fijan acá: se
registran en cada corrida, que debe consignar en su encabezado

- herramienta y versión;
- modelo y versión efectivamente usados;
- temperatura y demás parámetros que la herramienta exponga, o `NO_DISPONIBLE` si no los expone;
- fecha de la corrida;
- repositorio evaluado e identificador de commit evaluado.

## Modelos verificados

Registro de las combinaciones que el equipo probó y si sostienen el mismo nivel por dimensión
sobre el mismo trabajo. Se completa durante la calibración.

| Modelo | Herramienta | Corridas | ¿Mismo nivel por dimensión? | Observaciones |
|---|---|---|---|---|
| _pendiente de calibración_ | | | | |
