# Estado del proyecto — 09/09/2026

**Proyecto:** Agente Corrector — MBA UCEMA  
**Branch de seguimiento:** `andreavergara-seguimiento`  
**Corte revisado:** GitHub remoto al 09/09/2026  
**Main actual:** `0dce76f`  
**Leyenda:** 🟢 Terminado · 🔵 En curso · 🟡 Falta revisar/cerrar · 🔴 Prioridad crítica · ⬜ Pendiente

---

## 1. Estado actual

| Frente | Estado | Explicación simple |
|---|---|---|
| Rúbrica V3 | 🟡 | La V3 sigue siendo la rúbrica ejecutable integrada en `main`. H2 ya fue resuelto por Andrea + Ignacio en una branch específica, pero todavía falta integrarlo formalmente a `main`. |
| H2 — EV1 / EV3 | 🟡 | La solución ya está publicada en `andreavergara-h2-ev1-ev3`. Se hicieron dos pruebas dirigidas y la regla quedó cerrada por Dupla A. Falta revisión/integración por Toni. |
| Agente corrector | 🟢 | El system prompt y la configuración están integrados y funcionando. No requiere rediseño. |
| Ruta de las salidas | 🟢 | El PR #7 fue mergeado. Las evaluaciones del agente ahora se guardan correctamente en `calibracion/`. |
| Caso Excelente | 🟢 | Construido y validado. Puntaje estable: 100/100. |
| Caso Flojo | 🟢 | Construido y validado. Se mantiene dentro de la banda baja esperada. |
| Caso Tramposo | 🟢 | Construido y validado. El agente mantiene detección 4/4 de los intentos de manipulación. |
| Segunda corrida / estabilidad | 🟢 | Las segundas corridas de los tres casos fueron completadas y mergeadas mediante PR #9. El agente mantiene el mismo nivel por dimensión. |
| Calibración | 🟢/🟡 | Ya demuestra discriminación y estabilidad. Falta incorporar formalmente el cierre H2 en `main` y completar la prueba externa. |
| README final | 🟡 | El README de `main` sigue desactualizado. Existe una versión actualizada en `andreavergara-qa-consigna`, con roles, estructura y modo de uso. Falta revisión e integración. |
| QA contra consigna | 🟡 | Ya existe `QA_CONSIGNA.md` en `andreavergara-qa-consigna`. Identifica los gaps restantes y permite controlar la entrega punto por punto. Falta revisión final e integración. |
| Prueba externa | 🔴 | Sigue pendiente probar el agente sobre un repositorio real que el grupo no haya construido. Es el principal gap restante. |
| Documentación del incidente de lectura | 🟡 | Hubo un caso real de `RUBRICA_NO_DISPONIBLE` por sandbox y se resolvió. Conviene dejarlo documentado para demostrar cómo se resolvió la limitación del entorno. |
| Legibilidad / A1 resumen | 🟡 | La V3 funciona pero es extensa. Queda decidir si se incorpora A1 como resumen legible o si se deja sólo como evidencia histórica. No requiere rediseñar la rúbrica. |
| QA final integrado | ⬜ | Falta revisar el conjunto final una vez integrados H2 y la documentación. |
| Entrega final | 🔵 | El proyecto está en etapa de cierre. Ya no faltan componentes principales; quedan integración, prueba externa, documentación y QA final. |

---

## 2. Avances desde el status anterior

### Ruta de salida — CERRADO

El PR #7 fue mergeado a `main`.

Antes:

`casos/<caso>/corridas/`

Ahora:

`calibracion/`

Esto evita mezclar las corridas internas de los trabajos sintéticos con las evaluaciones realizadas por el agente.

### Estabilidad — CERRADO

Se completaron las segundas corridas de los tres casos y se integraron mediante PR #9.

Resultados:

| Caso | Corrida anterior | Segunda corrida | Resultado |
|---|---:|---:|---|
| Excelente | 100 | 100 | 🟢 Estable |
| Flojo | 23 | 24 | 🟢 Estable; +1 explicado por cambio previo en G3 |
| Tramposo | 5 | 5 | 🟢 Estable; mantiene 4/4 detecciones |

La diferencia de un punto en Flojo no corresponde a inestabilidad del agente sino a una modificación conocida de la rúbrica.

### H2 — RESUELTO EN BRANCH

La branch:

`andreavergara-h2-ev1-ev3`

ya está publicada.

Andrea + Ignacio cerraron la regla EV1/EV3 y se realizaron dos pruebas dirigidas:

- registro completo → aplica equivalencia para S2/E1;
- registro incompleto → no recibe la equivalencia.

La decisión metodológica está cerrada en la branch. Falta revisión de Toni e integración a `main`.

### QA contra consigna — AVANZADO

Se creó:

`andreavergara-qa-consigna`

Incluye:

- README actualizado;
- `QA_CONSIGNA.md`;
- consignas de la materia;
- guía operativa;
- documentación para facilitar la navegación del repositorio.

El QA confirma que la mayoría de los requisitos están cubiertos y que el gap más importante es la prueba externa.

---

## 3. Pendientes reales a esta altura

Ya NO necesitamos construir nuevas versiones del agente ni nuevos casos.

Los pendientes son de cierre:

1. probar el agente sobre un repositorio externo real;
2. integrar H2;
3. integrar README + QA final;
4. documentar el incidente de lectura/sandbox;
5. decidir si A1 se incluye como resumen legible;
6. hacer QA final sobre `main`;
7. congelar el commit de entrega;
8. subir el link al campus.

---

## 4. Próximos pasos y responsables

| Orden | Prioridad | Acción | Responsable | Explicación simple |
|---:|---|---|---|---|
| 1 | 🔴 P0 | Ejecutar prueba externa | Antonio + Leo | Correr el agente sobre una Entrega 1 o 2 real que no haya sido construida por el grupo y guardar el resultado. |
| 2 | 🔴 P0 | Revisar e integrar H2 | Toni + Andrea + Ignacio | Revisar la branch `andreavergara-h2-ev1-ev3` y, si no hay observaciones, incorporarla a `main`. |
| 3 | 🔴 P0 | Revisar branch QA | Andrea + Toni | Revisar `andreavergara-qa-consigna` e integrar README, QA y documentación necesaria. |
| 4 | 🟡 P1 | Corregir QA | Andrea | Revisar la inconsistencia del resumen: actualmente los totales declarados deben verificarse antes del merge. |
| 5 | 🟡 P1 | Documentar incidente sandbox | Andrea / Antonio | Dejar una nota breve explicando `RUBRICA_NO_DISPONIBLE`, causa y solución aplicada. |
| 6 | 🟡 P1 | Resolver destino de A1 | Andrea + Ignacio | Decidir si se incorpora como resumen legible o queda sólo como histórico. No hacer nuevas iteraciones. |
| 7 | 🔴 P0 | QA final integrado | Andrea + Toni | Revisar la consigna punto por punto contra el `main` final. |
| 8 | 🔴 P0 | Congelar `main` | Toni | Identificar el SHA final y no realizar nuevos cambios después de la aprobación. |
| 9 | 🔴 P0 | Entregar link | Integrante designado / Toni | Subir el enlace al repositorio público en el campus antes del plazo. |

---

## 5. Qué NO debemos volver a trabajar

No reabrir salvo que aparezca un defecto concreto:

- diseño general de la rúbrica;
- diseño del agente;
- casos Excelente / Flojo / Tramposo;
- ruta de salidas;
- segunda corrida de estabilidad;
- comparación V3 vs A1;
- estructura general del repositorio.

El foco desde ahora es **cerrar, integrar, probar externamente y entregar**.

---

## 6. Mensaje para el equipo

Estamos en la etapa final.

Los componentes principales ya están construidos y el agente demostró estabilidad sobre nuestros tres casos.

### Para cerrar la entrega faltan principalmente tres cosas:

1. **prueba externa**;
2. **integrar H2 y documentación final**;
3. **QA final + congelar `main`**.

No debemos agregar funcionalidades nuevas salvo que el QA detecte un incumplimiento concreto de la consigna.
