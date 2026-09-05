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
- Salidas de las corridas: `casos/<caso>/corridas/`.

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
