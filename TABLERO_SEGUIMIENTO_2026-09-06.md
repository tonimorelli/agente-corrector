# Tablero de seguimiento — 06/09/2026

**Proyecto:** Agente Corrector — MBA UCEMA  
**Branch de seguimiento:** `andreavergara-seguimiento`  
**Corte revisado:** 06/09/2026  
**Base de evaluación:** Guía Operativa V3 + `main` + branches relevantes del repositorio.

## 1. Semáforo ejecutivo

| Frente | Estado | Lectura actual |
|---|---|---|
| Gobierno / estructura | 🟡 | Estructura del repo creada; README aún no refleja roles operativos definidos en la Guía V3. |
| Rúbrica | 🔵 | V2 integrada en `main`; existen iteraciones posteriores en branches pendientes de decisión. |
| Agente corrector | 🔵 | `main` conserva placeholders, pero existe desarrollo sustantivo del system prompt/configuración en branch de trabajo. |
| Casos de prueba | ⬜ | Estructura creada; no hay corridas reales consolidadas en `main`. |
| Calibración | ⬜ | `calibracion.md` continúa como plantilla en `main`. |
| Integración final | ⬜ | Hay componentes todavía fuera de `main`. |
| Riesgo de entrega | 🟡 | Riesgo principal: consolidar agente/rúbrica, ejecutar casos y calibrar antes del 10/09. |

## 2. Seguimiento operativo

| ID | Etapa | Responsable | Estado | Evidencia actual | Próxima acción |
|---|---|---|---|---|---|
| 1.1 | Definir dimensiones, pesos y criterios | Ignacio | 🟢 | `rubrica.md` V2 en `main` | Mantener salvo hallazgos de calibración. |
| 1.2 | Revisar escalas, evidencia y anti-gaming | Andrea | 🔵 | V2 en `main`; branch `claude/rubrica-tipificar-evidencia-pa18h0` con cambios adicionales | Comparar cambios y decidir integración. |
| 1.3 | Consolidar rúbrica final | Andrea + Ignacio | 🔵 | `ignaciomonteserin-prueba` diverge de `main` con cambios sobre `rubrica.md` | Revisar diferencias entre branches y cerrar versión. |
| 2.1 | Traducir rúbrica a reglas del agente | Antonio | 🔵 | Desarrollo en `claude/system-prompt-agente-aollz9` | Revisar contra rúbrica vigente. |
| 2.2 | Diseñar flujo de evaluación | Leo | 🔵 | Parcialmente contenido en system prompt de branch | Validar cobertura completa. |
| 2.3 | Construir V1 del system prompt | Antonio | 🔵 | `agente/system_prompt.md` desarrollado en branch | Revisión cruzada antes de merge. |
| 2.4 | Revisar claridad, redundancias y tokens | Leo | ⬜ | Sin evidencia de revisión específica | Ejecutar revisión antes de testing. |
| 2.5 | Definir formato de salida | Antonio + Leo | 🟡 | Placeholder en `main`; branch del agente elimina archivo separado | Resolver fuente única y formato final. |
| 2.6 | Supervisión, límites y seguridad | Antonio + Leo | 🔵 | Contenido de seguridad presente en system prompt de branch | Validar contra rúbrica y caso tramposo. |
| 3.1 | Caso excelente | Mateo | ⬜ | Carpeta y plantillas en `main` | Completar caso y corridas. |
| 3.2 | Caso flojo | Tomás | ⬜ | Carpeta y plantillas en `main` | Completar caso y corridas. |
| 3.3 | Caso tramposo | Mateo + Tomás | ⬜ | Carpeta y plantillas en `main` | Completar caso adversarial. |
| 3.4 | Ejecutar corridas | Mateo + Tomás | ⬜ | Sin corridas reales consolidadas | Ejecutar 3 casos y guardar evidencia trazable. |
| 4.1 | Comparar nota humana vs. agente | Mateo + Tomás | ⬜ | `calibracion.md` placeholder | Iniciar después de primeras corridas. |
| 4.2 | Identificar discrepancias | Mateo + Tomás | ⬜ | Sin evidencia | Registrar discrepancias y causa. |
| 4.3 | Ajustar rúbrica/prompt | Dueño del componente | ⬜ | Pendiente de testing | Aplicar sólo después de hallazgo verificable. |
| 5.1 | Validar consistencia global | Andrea | ⬜ | Componentes aún no consolidados | Ejecutar después de calibración. |
| 5.2 | Integrar en `main` | Antonio | ⬜ | Branches relevantes pendientes | Mergear sólo versiones validadas. |
| 5.3 | Actualizar README | Antonio | 🟡 | README con integrantes, pero roles vacíos y estado 03/09 | Completar al consolidar componentes. |
| 5.4 | QA final | Andrea | ⬜ | Pendiente | Validar contra consigna antes de entrega. |

## 3. Branches relevantes detectadas

| Branch | Situación | Acción |
|---|---|---|
| `andreavergara-prueba` | Ya integrada; quedó detrás de `main` | No requiere acción. |
| `ignaciomonteserin-prueba` | Divergida; contiene cambios adicionales en `rubrica.md` | Comparar y decidir integración. |
| `claude/rubrica-tipificar-evidencia-pa18h0` | Adelantada respecto de `main`; modifica `rubrica.md` | Revisar como candidata a siguiente iteración. |
| `claude/system-prompt-agente-aollz9` | Adelantada respecto de `main`; desarrolla system prompt y configuración | Revisar e integrar si pasa checkpoint. |
| `andreavergara-seguimiento` | Branch exclusiva de seguimiento | Mantener fuera de `main` por ahora. |

## 4. Prioridades inmediatas

1. **Cerrar versión de rúbrica** comparando las dos iteraciones pendientes.
2. **Revisar el system prompt** contra la rúbrica final y resolver formato de salida/configuración.
3. **Completar y ejecutar los tres casos**.
4. **Calibrar** notas humanas vs. agente y registrar ajustes.
5. **Integrar en `main` y actualizar README**.
6. **QA final** contra consigna antes del 10/09.

## 5. Riesgos

| Riesgo | Nivel | Mitigación |
|---|---|---|
| Trabajo relevante disperso entre branches | Alto | Consolidar por checkpoint, no por antigüedad. |
| Agente aún no probado con casos reales | Alto | Priorizar integración mínima viable + testing. |
| Calibración no iniciada | Alto | Ejecutar apenas exista una versión estable del agente. |
| README no refleja organización real | Medio | Actualizar después de consolidar responsabilidades y componentes. |
