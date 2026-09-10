# Agente Evaluador — Parcial grupal

- **Materia:** Programación de y con Agentes de IA
- **Programa:** MBA UCEMA · 2026 2T
- **Profesor:** Alfredo B. Roisenzvit
- **Entrega:** jueves 10/9/2026, 18:59 (link del repo en la actividad *Parcial* del campus)
- **Prueba de fuego:** en vivo, esa misma noche

## Qué es este repositorio

El parcial de la materia es construir un **agente evaluador**: un sistema capaz de corregir los
trabajos finales de la cursada. Este repositorio contiene ese agente y la evidencia de que
funciona.

El agente aplica la **rúbrica ejecutable V3**: las cinco dimensiones de la rúbrica oficial del
trabajo final (con sus pesos) traducidas a criterios explícitos, con escalas por nivel y la
evidencia que exige cada puntaje. Recibe el repositorio de un trabajo final y devuelve, por cada
dimensión, un puntaje, la justificación de ese puntaje citando evidencia del trabajo, y una
sugerencia concreta de mejora. La salida tiene un formato estructurado fijo, idéntico en cada
corrida.

## Integrantes y roles

| Nombre | Rol |
| --- | --- |
| Andrea Vergara | Coordinación y seguimiento · revisión de rúbrica y cierre de H2 |
| Antonio Morelli | Gestión del repositorio · system prompt e integración |
| Ignacio Monteserin | Diseño y revisión de la rúbrica ejecutable |
| Leo Bordeira | Revisión del agente · configuración de las corridas |
| Mateo García | Caso excelente · calibración, estabilidad y ensayo externo |
| Tomás García | Casos flojo y tramposo |

## Estructura del repositorio

```
.
├── README.md            — este archivo
├── rubrica.md           — la rúbrica ejecutable (V3): dimensiones, subcriterios, escalas, topes y reglas de evidencia
├── agente/
│   ├── system_prompt.md — instrucciones del agente evaluador y contrato de formato de salida
│   └── configuracion.md — requisitos del entorno de ejecución y qué registra cada corrida
├── casos/
│   ├── excelente/       — trabajo final sintético de alta calidad (README, DECISIONES, prompts/, corridas/)
│   ├── flojo/           — trabajo final sintético de baja calidad
│   └── tramposo/        — trabajo final sintético que intenta manipular al evaluador
├── calibracion.md       — registro de calibración: notas humanas vs. agente, desacuerdos, ajustes y resultado
├── calibracion/         — corridas completas del evaluador sobre los tres casos (evidencia de la calibración)
└── docs/                — material de referencia: consignas oficiales y guía operativa del equipo
```

- **`rubrica.md`** — operacionaliza las cinco dimensiones oficiales (Sistema completo 30 · Proceso
  documentado 25 · Formato y reproducibilidad 15 · Análisis económico 15 · Gobierno y riesgo 15).
  Cada subcriterio tiene valores permitidos, la jerarquía de evidencia EV1–EV4, topes por
  dimensión y reglas transversales contra *gaming*.
- **`agente/`** — el agente no es un programa: es el `system_prompt.md` que corre dentro de una
  herramienta con acceso de sólo lectura al repositorio evaluado. `configuracion.md` fija qué debe
  cumplir esa herramienta (lectura de archivos e historial; sin ejecución de código, red ni
  escritura) y qué registra cada corrida.
- **`casos/`** — cada caso es un trabajo final completo construido por el grupo, con sus propios
  prompts, corridas y `DECISIONES.md`. El agente debe puntuar alto al excelente, bajo al flojo y
  detectar los intentos de manipulación del tramposo sin obedecerlos.
- **`calibracion.md` + `calibracion/`** — la evidencia de que las notas del agente coinciden con
  el criterio humano del grupo: qué puso el agente, qué esperábamos, dónde no coincidía, qué se
  ajustó y cómo quedó después. Las corridas crudas del evaluador viven en `calibracion/`.
- **`docs/`** — `parcial_agente_evaluador.pdf` y `trabajo_final.pdf` (consignas oficiales de la
  cátedra) y `Guia_operativa_Agente_Corrector_v3` (reparto de tareas y prompts del equipo).

## Cómo correr el agente evaluador

1. Abrir una herramienta con acceso de lectura al repositorio a evaluar (Claude Code, Codex u
   otra), **con ejecución de código y acceso a red desactivados**.
2. Cargar `agente/system_prompt.md` como system prompt. El agente lee `rubrica.md` de la raíz de
   este repositorio en cada corrida; sin rúbrica legible no evalúa.
3. Pasar como entrada la ruta o URL del repositorio del trabajo final a corregir.
4. El agente devuelve un único bloque delimitado (`===EVALUACION_INICIO=== … ===EVALUACION_FIN===`)
   con seis documentos YAML: uno por dimensión más un cierre con el `puntaje_total` sobre 100 y
   las banderas transversales.
5. El operador guarda esa salida en `calibracion/` como `corrida_evaluador_<caso>_<n>.md`, sin
   editarla, con un encabezado que consigne herramienta, modelo, fecha, repo y commit evaluados.

Ver `agente/configuracion.md` para el detalle de parámetros a registrar y `calibracion.md` para
el método de calibración.

## Estado

El agente está construido e integrado, con V3 como rúbrica ejecutable. H2 está cerrado e
integrado mediante el [PR #10](https://github.com/tonimorelli/agente-corrector/pull/10).
Los tres casos están calibrados y las segundas corridas demostraron estabilidad de niveles
en las cinco dimensiones; la diferencia de un punto en el caso flojo responde a un cambio
de rúbrica documentado en `calibracion.md`.

El ensayo sobre un repositorio externo real fue exitoso y quedó integrado mediante el
[PR #11](https://github.com/tonimorelli/agente-corrector/pull/11); valida el funcionamiento
sobre una estructura externa, no la calibración de su nota.

El proyecto está en etapa de **QA final y entrega**. Última actualización: 10 de septiembre de 2026.
Ver `QA_CONSIGNA.md` para el estado de cumplimiento punto por punto contra la consigna del parcial.
