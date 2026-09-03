# Agente Evaluador — Parcial grupal

- **Materia:** Programación de y con Agentes de IA
- **Programa:** MBA UCEMA · 2026 2T
- **Profesor:** Alfredo B. Roisenzvit
- **Entrega:** jueves 10/9, 18:59

## Qué es este repositorio

Este repositorio contiene un agente evaluador que corrige trabajos finales de la cursada.
El agente aplica una rúbrica ejecutable: un conjunto de dimensiones con criterios explícitos
que puede recorrer de forma consistente sobre cualquier entrega.

Para cada trabajo devuelve un puntaje por dimensión, la justificación de ese puntaje y una
sugerencia concreta de mejora, de modo que la corrección sea trazable y no dependa del criterio
puntual de quien corrige.

## Integrantes

| Nombre | Rol |
| --- | --- |
| Antonio Morelli |  |
| Andrea Vergara |  |
| Ignacio Monteserin |  |
| Leo Bordeira |  |
| Mateo García |  |
| Tomás García |  |

## Estructura del repositorio

```
.
├── rubrica.md
├── agente/
├── casos/
│   ├── excelente/
│   ├── flojo/
│   └── tramposo/
└── calibracion.md
```

- `rubrica.md` — la rúbrica ejecutable: dimensiones, criterios y escala de puntaje.
- `agente/` — la definición del agente evaluador: system prompt, configuración y formato de salida.
- `casos/excelente/` — caso de prueba de un trabajo de alta calidad, con sus prompts y corridas.
- `casos/flojo/` — caso de prueba de un trabajo de baja calidad, con sus prompts y corridas.
- `casos/tramposo/` — caso de prueba de un trabajo que intenta engañar al evaluador, con sus prompts y corridas.
- `calibracion.md` — registro de la calibración del agente: ajustes hechos a partir de las corridas.

## Estado

Repositorio en construcción. Última actualización: 3 de septiembre de 2026.
