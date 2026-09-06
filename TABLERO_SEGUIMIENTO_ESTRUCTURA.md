# Tablero de seguimiento — Estructura base

**Proyecto:** Agente Corrector — MBA UCEMA  
**Fuente de verdad del seguimiento:** Guía Operativa V3 + estado verificable del repositorio y branches.  
**Estados:** 🟢 Cerrado · 🔵 En curso · 🟡 Requiere revisión · 🔴 Bloqueado · ⬜ Pendiente

## 1. Gobierno del proyecto

| Frente | Responsable | Evidencia esperada | Estado | Próxima acción |
|---|---|---|---|---|
| Coordinación general y coherencia | Andrea Vergara | Guía, tablero, decisiones y revisión cruzada | ⬜ | — |
| Repo Owner / integración técnica / main | Antonio Morelli | Branches, merges, estructura y commits | ⬜ | — |
| Dupla 1 — Rúbrica | Andrea Vergara + Ignacio Monteserin | `rubrica.md` | ⬜ | — |
| Dupla 2 — Agente corrector | Antonio Morelli + Leo Bordeira | `agente/system_prompt.md`, configuración y salida | ⬜ | — |
| Dupla 3 — Casos + calibración | Mateo García + Tomás García | `casos/` + `calibracion.md` | ⬜ | — |

## 2. Flujo operativo maestro

| ID | Etapa | Responsable principal | Revisor / contraparte | Evidencia esperada | Estado | Próxima acción |
|---|---|---|---|---|---|---|
| 1.1 | Definir dimensiones, pesos y criterios de la rúbrica | Ignacio | Andrea | `rubrica.md` | ⬜ | — |
| 1.2 | Revisar escalas, evidencia, topes y anti-gaming | Andrea | Ignacio | Nueva iteración de `rubrica.md` | ⬜ | — |
| 1.3 | Consolidar rúbrica ejecutable | Andrea + Ignacio | Equipo | `rubrica.md` final | ⬜ | — |
| 2.1 | Traducir la rúbrica a reglas del agente | Antonio | Leo | `agente/system_prompt.md` | ⬜ | — |
| 2.2 | Diseñar flujo de evaluación del agente | Leo | Antonio | System prompt / configuración | ⬜ | — |
| 2.3 | Construir V1 del system prompt | Antonio | Leo | Commit / branch de trabajo | ⬜ | — |
| 2.4 | Revisar claridad, redundancias y consumo de tokens | Leo | Antonio | Versión revisada | ⬜ | — |
| 2.5 | Definir formato estructurado de salida | Antonio + Leo | Andrea / Dupla 1 | Configuración / esquema | ⬜ | — |
| 2.6 | Definir supervisión humana, límites y seguridad | Antonio + Leo | Andrea | Prompt / configuración | ⬜ | — |
| 3.1 | Diseñar caso excelente | Mateo | Tomás | `casos/excelente/` | ⬜ | — |
| 3.2 | Diseñar caso flojo | Tomás | Mateo | `casos/flojo/` | ⬜ | — |
| 3.3 | Diseñar caso tramposo | Mateo + Tomás | Dupla 2 | `casos/tramposo/` | ⬜ | — |
| 3.4 | Ejecutar corridas de los 3 casos | Mateo + Tomás | Dupla 2 | Corridas trazables | ⬜ | — |
| 4.1 | Comparar nota esperada vs. agente | Mateo + Tomás | Andrea + Ignacio | `calibracion.md` | ⬜ | — |
| 4.2 | Identificar discrepancias y causa | Mateo + Tomás | Equipo | `calibracion.md` | ⬜ | — |
| 4.3 | Ajustar rúbrica o prompt según hallazgo | Dueño del componente | Contraparte | Commit + decisión | ⬜ | — |
| 5.1 | Validar rúbrica ↔ agente ↔ casos | Andrea | Equipo | Revisión cruzada | ⬜ | — |
| 5.2 | Integrar componentes validados en main | Antonio | Andrea | Merge / commits | ⬜ | — |
| 5.3 | Actualizar README y evidencia final | Antonio | Andrea | `README.md` | ⬜ | — |
| 5.4 | QA final contra consigna | Andrea | Equipo | Checklist final | ⬜ | — |

## 3. Checkpoints obligatorios

| Checkpoint | Qué se valida | Quién valida | Evidencia mínima |
|---|---|---|---|
| CP1 — Rúbrica lista para agente | Precisión, escalas, evidencia y reglas anti-gaming | Andrea + Ignacio | `rubrica.md` revisada |
| CP2 — Agente listo para probar | Prompt, configuración, salida y límites coherentes con rúbrica | Dupla 2 + Andrea | Archivos de `agente/` |
| CP3 — Casos listos | Excelente, flojo y tramposo distinguen comportamientos esperados | Dupla 3 + Dupla 2 | Carpetas de `casos/` |
| CP4 — Calibración | Notas humanas vs. agente, discrepancias y ajustes | Equipo | `calibracion.md` |
| CP5 — Entrega | Repo completo, reproducible y trazable | Andrea + Antonio | `main` final |

## 4. Reglas operativas

1. GitHub se modifica desde la herramienta de trabajo mediante conectores/comandos; evitar edición manual en GitHub.
2. No mergear a `main` sin revisión del componente.
3. Usar copy/paste de fragmentos o screenshots sólo cuando sea la forma más eficiente de validar; evitar copiar archivos completos si el conector puede leerlos.
4. Cada iteración debe dejar evidencia: branch/commit, archivo cambiado, decisión y resultado.
5. El system prompt se itera en secuencia: **rúbrica → reglas → flujo → V1 → revisión de claridad/tokens → testing → calibración → ajuste final**.
6. `🟢 Cerrado` requiere artefacto desarrollado, revisado y con evidencia; la mera existencia del archivo no alcanza.
