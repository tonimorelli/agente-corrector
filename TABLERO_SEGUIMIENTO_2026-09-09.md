# Estado del proyecto — 09/09/2026

**Proyecto:** Agente Corrector — MBA UCEMA  
**Branch de seguimiento:** `andreavergara-seguimiento`  
**Corte revisado:** GitHub remoto al 09/09/2026  
**Leyenda:** 🟢 Terminado · 🔵 En curso · 🟡 Falta revisar/cerrar · ⬜ Pendiente

---

## 1. Estado actual

| Frente | Estado | Explicación simple |
|---|---|---|
| Rúbrica | 🟡 | La V3 está integrada y funcionando. H2 fue validada con 12 evaluaciones A/B, pero la prueba no demostró que la aclaración mejore el comportamiento. Falta una prueba mínima dirigida para decidir si se incorpora o se descarta. |
| Agente corrector | 🟡 | El agente está integrado y funcionando. Queda cerrar documentación y hacer la validación final del proyecto. |
| Caso Excelente | 🟢 | Está construido y el agente logró evaluarlo correctamente. |
| Caso Flojo | 🟢 | Está construido y el agente logró distinguirlo como trabajo débil. |
| Caso Tramposo | 🟢 | Está construido y el agente detectó los 4 intentos de manipulación. |
| Segunda corrida de los casos | 🟢 | Mateo realizó las segundas corridas de Excelente, Flojo y Tramposo. El agente mantuvo los mismos niveles y criterios. Se concluyó que es estable. Falta integrar esta evidencia a `main`. |
| Calibración | 🟡 | La segunda corrida ya está documentada en `mateogarcia-calibracion-estabilidad`. Falta integrarla a `main` y cerrar la calibración con la decisión final sobre H2. |
| Ruta de las salidas | 🟢 | El PR #7 fue revisado y mergeado. Las salidas del evaluador quedan correctamente ubicadas en `calibracion/`. |
| Documentación del guardado de salidas | 🟡 | El PR #8 está abierto y mergeable. Aclara que el agente no guarda por sí mismo: el operador conserva la salida siguiendo el procedimiento documentado. |
| Integración en `main` | 🔵 | Rúbrica, agente, casos, primera calibración y PR #7 están integrados. `main` está en `9c3414d`. Falta integrar estabilidad y resolver PR #8. |
| README | 🟡 | Existe, pero todavía indica “Repositorio en construcción”, mantiene fecha 03/09 y requiere actualización para reflejar el estado final. |
| Prueba con un trabajo externo | ⬜ | Todavía falta confirmar o ejecutar una prueba del agente con un repositorio real que no haya usado durante su construcción. |
| QA final contra la consigna | ⬜ | Falta revisar punto por punto que los entregables y criterios evaluados por el parcial estén efectivamente cubiertos. |
| Entrega final | 🔵 | El proyecto está construido. Estamos en etapa de integración, validación y cierre final. |

---

## 2. Novedades desde el último corte

- El PR #7 fue mergeado a `main` y quedó cerrada la corrección de la ruta de salidas.
- `main` avanzó al commit `9c3414d`.
- Mateo completó las segundas corridas de los tres casos en la branch `mateogarcia-calibracion-estabilidad`.
- Los resultados de estabilidad fueron:
  - Excelente: 100 → 100.
  - Flojo: 23 → 24.
  - Tramposo: 5 → 5.
  - Caso Tramposo: mantiene detección de 4/4 intentos de manipulación.
- La diferencia de +1 en Flojo fue atribuida a un cambio conocido de la rúbrica en G3 y no a inestabilidad del agente.
- La conclusión documentada es que el agente es ESTABLE bajo el criterio definido.
- Esta evidencia todavía no está integrada en `main`.
- Toni abrió el PR #8 para documentar correctamente quién y cómo guarda las salidas del evaluador.
- H2 completó la validación A/B de 12/12 evaluaciones.
- La prueba A/B no demostró que H2 mejore la consistencia porque la condición específica que modifica H2 no quedó aislada.
- Se decidió no repetir el experimento completo. Sólo queda una prueba mínima dirigida para cerrar H2.
- La branch H2 sigue local y no fue publicada, mergeada ni incorporada a `main`.
- Se revisó el proyecto contra la consigna del parcial.
- No se detectó un faltante estructural en la dimensión económica: está incluida en la rúbrica y ya fue probada durante la calibración.

---

## 3. Próximos pasos y responsables

| Orden | Qué hay que hacer | Responsable | Explicación simple |
|---:|---|---|---|
| 1 | Revisar e integrar `mateogarcia-calibracion-estabilidad` | Toni | Revisar el branch de estabilidad de Mateo y mergearlo a main. |
| 2 | Revisar y mergear PR #8 | Toni + Leo | Incorporar la documentación final sobre cómo se guardan las salidas del evaluador. |
| 3 | Cerrar H2 con una prueba mínima dirigida | Andrea + Ignacio | Ejecutar sólo una comparación específica main vs. H2. No repetir las 12 evaluaciones anteriores. |
| 4 | Decidir el cierre de H2 | Andrea + Ignacio | Si la prueba demuestra una mejora específica, proponer incorporación. Si no, documentar que H2 no se incorpora. |
| 5 | Probar el agente con un repositorio externo real | Equipo | Hacer una única prueba de fuego con un trabajo que el agente no haya utilizado durante su construcción. |
| 6 | Actualizar README | Toni + Andrea | Completar roles, estado, fecha, funcionamiento y situación final del proyecto. |
| 7 | Cerrar calibración | Mateo + Tomás + revisión Andrea/Ignacio | Incorporar estabilidad, resultado H2 y cualquier resultado relevante de la prueba externa. |
| 8 | QA final contra la consigna | Andrea + Toni | Revisar entregables, las cinco dimensiones del agente y el proceso grupal antes de entregar. |
| 9 | Congelar `main` para entrega | Toni | Cuando todo esté validado, identificar el commit final y no realizar más cambios. |

---

## 4. Mensaje simple para el equipo

No necesitamos construir componentes nuevos.

**Rúbrica, agente, casos y segunda corrida ya existen y funcionan.**

De acá a la entrega el objetivo es:

- integrar la evidencia ya producida;
- cerrar PR #8;
- resolver H2 con el mínimo trabajo necesario;
- hacer una prueba externa;
- actualizar la documentación;
- revisar el cumplimiento contra la consigna;
- realizar el QA final;
- congelar `main`.

La prioridad es no repetir pruebas ni abrir nuevos frentes que no sean necesarios para la entrega.

---

## 5. Pendientes que NO deben bloquear el trabajo de hoy

H2 todavía no está cerrado, pero no impide avanzar con:

- integración de las segundas corridas;
- PR #8;
- prueba externa;
- actualización del README;
- actualización de calibración;
- QA contra la consigna.

Lo que no debe cerrarse definitivamente hasta resolver los pendientes críticos es:

- la calibración final;
- el QA final;
- el congelamiento de `main`.

Con menos de 24 horas para la entrega, cualquier nueva prueba debe realizarse sólo si puede cambiar una decisión necesaria para entregar.

---

## 6. Cumplimiento contra la consigna del parcial

### 6.1 Entregables principales

| Requisito del parcial | Estado | Evidencia actual / faltante |
|---|---|---|
| Rúbrica ejecutable | 🟢 | Existe `rubrica.md`, con criterios observables, escalas y reglas de evidencia. V3 es la versión ejecutable seleccionada. |
| Agente corrector funcionando | 🟢 | Existe `agente/system_prompt.md`, configuración y múltiples evaluaciones reales sobre los casos. |
| Tres casos de prueba | 🟢 | Existen los casos Excelente, Flojo y Tramposo y producen resultados claramente diferenciados. |
| Calibración documentada | 🟡 | Existe primera calibración y segunda corrida de estabilidad. Falta integrar la segunda corrida y cerrar H2. |
| Proceso grupal documentado | 🟡 | Existen branches, commits, PRs, decisiones y responsables. Falta consolidar el cierre en README y QA final. |

### 6.2 Cobertura de las cinco dimensiones que debe evaluar el agente

| Dimensión | Peso | Rúbrica | Prueba/calibración | Estado |
|---|---:|---|---|---|
| Sistema completo y funcionando | 30% | Sí | Probada en los tres casos | 🟢 |
| Proceso documentado | 25% | Sí | Probada en los tres casos | 🟢 |
| Formato y reproducibilidad | 15% | Sí | Probada en los tres casos | 🟢 |
| Análisis económico | 15% | Sí | Excelente: 15/15 · Flojo: 0/15 · Tramposo: 0/15 | 🟢 |
| Gobierno y riesgo | 15% | Sí | Probada en los tres casos, incluyendo manipulación y controles | 🟢 |

### 6.3 Análisis económico

El componente económico **sí está cubierto**.

El agente debe evaluar:

- costo por corrida;
- proyección de costo;
- justificación de la elección de modelo/herramienta;
- evidencia suficiente para respaldar esos cálculos o decisiones.

La calibración demuestra que el agente diferencia correctamente la presencia o ausencia de esa evidencia:

- Caso Excelente: 15/15.
- Caso Flojo: 0/15.
- Caso Tramposo: 0/15.

Por lo tanto, hoy no se identifica un gap estructural en análisis económico.

### 6.4 Gaps reales antes de entregar

Los faltantes prioritarios no son nuevas funcionalidades. Son cierres:

1. integrar las segundas corridas de estabilidad;
2. cerrar PR #8;
3. resolver H2;
4. ejecutar una prueba externa real;
5. actualizar README;
6. cerrar calibración;
7. hacer QA final contra la consigna;
8. congelar `main`.

### 6.5 Lectura general

El proyecto cubre actualmente los principales componentes exigidos por el parcial y las cinco dimensiones que el agente debe poder evaluar.

**Estado de cumplimiento estimado: 🟡 ALTO, pero todavía no listo para congelar.**

El riesgo principal ya no es que falte una dimensión del agente, sino que quede evidencia producida sin integrar, documentación desactualizada o algún requisito de cierre sin demostrar antes de la entrega.
