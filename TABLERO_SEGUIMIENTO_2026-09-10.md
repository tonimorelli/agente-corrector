# TABLERO DE SEGUIMIENTO — 10/09/2026

**Proyecto:** MBA | Agente corrector grupal  
**Repositorio:** `tonimorelli/agente-corrector`  
**Branch de entrega:** `main`  
**Corte verificado:** `af3baa14cd91a0d327946a3c54c358e8bd0ec904`  
**Estado general:** 🟢 LISTO PARA ENTREGA

### Leyenda

- 🟢 Completo / validado
- 🔵 En curso
- 🟡 Pendiente de cierre
- 🔴 Bloqueante
- ⬜ No iniciado

---

## 1. Estado actual

| Frente | Estado | Explicación |
|---|---|---|
| Rúbrica ejecutable V3 | 🟢 | Versión final integrada en `main`, con criterios, escalas, evidencia, topes y reglas anti-gaming. |
| Agente corrector | 🟢 | System prompt y configuración integrados; salida estructurada y evidenciada en las corridas. |
| Casos excelente / flojo / tramposo | 🟢 | Los tres casos están construidos y evaluados. Excelente puntúa alto, flojo bajo y tramposo activa correctamente controles de manipulación. |
| Calibración | 🟢 | Comparación humano–agente, discrepancias, ajustes y resultado posterior documentados. |
| Estabilidad | 🟢 | Segundas corridas realizadas; se mantienen niveles y comportamiento. La diferencia de 1 punto del flojo está explicada por un cambio versionado de rúbrica. |
| H2 EV1–EV3 | 🟢 | Cerrado, validado e integrado mediante PR #10. |
| Ensayo sobre repo externo | 🟢 | Ejecutado sobre una estructura no construida como caso por el grupo e integrado mediante PR #11. |
| Incidente de lectura / sandbox (D2) | 🟢 | Problema real diagnosticado y resuelto mediante ajuste de configuración; evidencia documentada en `calibracion.md`. |
| README final | 🟢 | Integrado en `main`, con integrantes, roles, estructura, uso y estado del proyecto. |
| QA contra consigna | 🟢 | QA final integrado. Resultado: 16 CUMPLE / 1 PARCIAL / 0 NO CUMPLE. |
| Integración final en `main` | 🟢 | Todo el paquete de cierre está integrado. Último commit: `af3baa14`. |
| Entrega en campus | 🟡 | Único pendiente: un integrante debe subir el link del repositorio y confirmar la entrega. |

**Lectura ejecutiva:** no quedan desarrollos, correcciones funcionales ni validaciones técnicas necesarias antes de entregar. El único paso pendiente es administrativo: **subir el link del repositorio al campus**.

---

## 2. Novedades desde el último status

| Novedad | Estado | Evidencia / resultado |
|---|---|---|
| H2 integrado | 🟢 | PR #10 cerrado e integrado en `main`. |
| Ensayo externo integrado | 🟢 | PR #11 cerrado e integrado en `main`. |
| README final incorporado | 🟢 | El README ya refleja estado, integrantes, roles y procedimiento de ejecución. |
| QA V2 actualizado | 🟢 | Se corrigieron gaps obsoletos y el resultado pasó a 16 CUMPLE / 1 PARCIAL / 0 NO CUMPLE. |
| D2 cerrado | 🟢 | Se documentó el incidente `RUBRICA_NO_DISPONIBLE`, su causa de sandbox y la configuración que permitió continuar. |
| QA final congelado | 🟢 | Se eliminaron referencias de “precierre” y branches intermedias. |
| `main` actualizado | 🟢 | Commit final verificado: `af3baa14cd91a0d327946a3c54c358e8bd0ec904`. |

---

## 3. Próximos pasos y responsables

| Orden | Qué hacer | Responsable | Estado | Explicación |
|---:|---|---|---|---|
| 1 | Subir el link de `tonimorelli/agente-corrector` en la actividad Parcial del campus | Integrante designado / Toni | 🟡 | Es el único requisito todavía no confirmado. |
| 2 | Guardar evidencia de la entrega | Quien realice la entrega | 🟡 | Screenshot o confirmación del campus con fecha/hora. |
| 3 | Confirmar al equipo que la entrega quedó realizada | Andrea | 🟡 | Una vez confirmado, E1 pasa de PARCIAL a CUMPLE. |
| 4 | No modificar `main` después de la entrega salvo error crítico | Todo el equipo | 🟢 | El repositorio debe considerarse congelado para preservar la versión entregada. |
| 5 | Participar de la prueba de fuego en vivo | Equipo | ⬜ | Es la instancia posterior de clase; no constituye un gap pendiente del repositorio antes de entregar. |

---

## 4. Mensaje al equipo

**Estado al 10/09: LISTOS PARA ENTREGAR.**

La construcción y validación del agente están cerradas. Rúbrica, agente, tres casos, calibración, estabilidad, H2, ensayo externo, documentación y QA final ya están integrados en `main`.

El QA contra la consigna da:

**16 CUMPLE / 1 PARCIAL / 0 NO CUMPLE.**

El único PARCIAL es administrativo: **falta confirmar la subida del link al campus**.

Por favor, no abrir nuevas mejoras ni modificar el agente, la rúbrica o la calibración salvo que aparezca un error crítico verificable.

---

## 5. Pendientes no bloqueantes

| Tema | Estado | Decisión |
|---|---|---|
| Verificación cruzada con otro modelo/herramienta | ⬜ Opcional | Deseable metodológicamente, pero no requerida para cerrar la entrega. No ejecutar ahora. |
| Comparación V3 vs A1 | 🟢 Cerrado | Se conserva como evidencia histórica/comparativa. V3 continúa como rúbrica ejecutable. |
| Tableros anteriores | 🟢 Histórico | No requieren integración adicional para cumplir la consigna. |
| Nuevas corridas | 🟢 No necesarias | La evidencia existente es suficiente; evitar consumo y riesgo innecesario antes de entregar. |

**No bloquean la entrega.**

---

## 6. Cumplimiento contra la consigna del parcial

### 6.1 Resumen

| Bloque | Ítems | CUMPLE | PARCIAL | NO CUMPLE |
|---|---:|---:|---:|---:|
| A · Las cuatro piezas | 4 | 4 | 0 | 0 |
| B · Estructura obligatoria del repo | 6 | 6 | 0 | 0 |
| C · Proceso grupal | 3 | 3 | 0 | 0 |
| D · Reglas de la casa | 2 | 2 | 0 | 0 |
| E · Entrega y prueba de fuego | 2 | 1 | 1 | 0 |
| **TOTAL** | **17** | **16** | **1** | **0** |

### 6.2 Las cuatro piezas obligatorias

| Entregable | Estado | Evidencia principal |
|---|---|---|
| Rúbrica ejecutable | 🟢 CUMPLE | `rubrica.md` |
| Agente corrector | 🟢 CUMPLE | `agente/system_prompt.md` + `agente/configuracion.md` |
| Tres casos de prueba | 🟢 CUMPLE | `casos/excelente/`, `casos/flojo/`, `casos/tramposo/` |
| Calibración | 🟢 CUMPLE | `calibracion.md` + `calibracion/` |

### 6.3 Cobertura de las cinco dimensiones oficiales

| Dimensión | Peso | Estado |
|---|---:|---|
| Sistema completo y funcionando | 30 | 🟢 CUMPLE |
| Proceso documentado | 25 | 🟢 CUMPLE |
| Formato y reproducibilidad | 15 | 🟢 CUMPLE |
| Análisis económico | 15 | 🟢 CUMPLE |
| Gobierno y riesgo | 15 | 🟢 CUMPLE |
| **Total** | **100** | 🟢 |

**Control importante:** Análisis económico está efectivamente incorporado en la rúbrica como dimensión de 15 puntos y fue ejercitado en la calibración. No constituye un gap.

### 6.4 Requisitos académicos críticos

| Requisito de la consigna | Estado | Comentario |
|---|---|---|
| Rúbrica suficientemente precisa para aplicación repetible | 🟢 | Estabilidad comprobada mediante segundas corridas. |
| Rúbrica discutible por humanos | 🟢 | Criterios, evidencia y ejemplos explícitos; H1/H2 muestran discusión y ajuste real. |
| Puntaje por dimensión | 🟢 | Incluido en el contrato de salida. |
| Justificación citando evidencia | 🟢 | Incluida por dimensión. |
| Mejora concreta | 🟢 | Campo obligatorio del agente. |
| Formato estructurado y consistente | 🟢 | Contrato YAML delimitado. |
| Caso excelente | 🟢 | Resultado final 100/100. |
| Caso flojo | 🟢 | Resultado 23–24/100. |
| Caso tramposo | 🟢 | 4/4 vectores de manipulación detectados y no obedecidos. |
| Calibración humano–agente | 🟢 | Documentada con expectativas, discrepancias, ajustes y resultados. |
| Proceso grupal visible en commits | 🟢 | Historia incremental y trabajo distribuido. |
| Resolver problemas de herramientas en lugar de abandonar | 🟢 | Incidente D2 documentado y resuelto. |
| Preparación para corregir estructura no vista | 🟢 | Ensayo externo completado. |
| Subir link al campus | 🟡 | Único pendiente real. |
| Prueba de fuego en vivo | ⬜ Posterior | Se realiza en la instancia prevista por la materia; no debe marcarse como fallo previo a la entrega. |

### 6.5 Evaluación final

**Resultado de QA:** 🟢 **GO PARA ENTREGA**

No existen NO CUMPLE ni gaps técnicos abiertos.

El repositorio cumple sustantivamente con todos los componentes exigidos por la consigna que deben estar construidos antes de la entrega.

**Único pendiente:** confirmar la carga del link del repositorio en el campus antes del horario límite.

Una vez confirmada esa acción:

**17 / 17 requisitos cerrados para la instancia de entrega.**

---

## Estado de congelamiento

**Commit final de referencia:**  
`af3baa14cd91a0d327946a3c54c358e8bd0ec904`

**Decisión:** no realizar nuevas modificaciones ni corridas antes de la entrega salvo error crítico verificable.

**Próximo hito:** entrega en campus → prueba de fuego en vivo.
