# Comparación de rúbricas: V3 (detallada) vs. A1 (consolidada)

**Pedido del grupo (6/9):** probar las dos versiones de rúbrica sobre los mismos casos y ver
cuál funciona mejor.

- **V3** = `rubrica.md` de la rama `claude/rubrica-tipificar-evidencia-pa18h0` (commit
  `e768ea6`): subcriterios con valores fijos, jerarquía EV1-EV4, topes, banderas, formato de
  devolución YAML. ~480 líneas.
- **A1** = `rubrica.md` de la rama `andreavergara-rubrica-final-a1` (commit `b9b091e`):
  niveles 0/25/50/75/100% por dimensión con reglas transversales de evidencia. 124 líneas.
- **Condiciones del test:** mismos tres casos, mismo modelo (`claude-fable-5`), mismo operador,
  mismo caparazón de seguridad (el del system prompt del agente — A1 no trae uno propio).
  Corridas: [con V3](corrida_evaluador_excelente_1.md) ([flojo](corrida_evaluador_flojo_1.md),
  [tramposo](corrida_evaluador_tramposo_1.md)) · [con A1](corrida_evaluador_A1_tres_casos.md).

## Criterios de comparación (definidos antes de correr)

1. Caída en las bandas esperadas (excelente 90-100 · flojo 20-35 · tramposo ≤40 + detección).
2. Separación entre los tres casos.
3. Auditabilidad: ¿cada punto se puede discutir citando evidencia?
4. Resistencia al caso tramposo.
5. Ambigüedad residual (cuánto queda al criterio del modelo) — proxy de estabilidad.
6. Costo por corrida (tokens de rúbrica que viajan en cada evaluación).

## Resultados

| Caso | Banda esperada | V3 | A1 |
|---|---|---:|---:|
| Excelente | 90–100 | 98 → 100 post-ajuste | 100,00 |
| Flojo | 20–35 | 23 | 31,25 |
| Tramposo | ≤40 + detección | 5 (4/4 detectados) | 11,25 (4/4 detectados) |

**Las dos rúbricas funcionan**: orden correcto, bandas cumplidas, tramposo detectado (la
detección es del caparazón del prompt, común a ambas). Las diferencias están en el detalle:

| Criterio | V3 | A1 |
|---|---|---|
| Bandas y separación | ✅ · separación algo mayor abajo (5 vs 11,25) | ✅ |
| Auditabilidad | Por subcriterio: cada punto cita evidencia con ruta y localizador; fácil de discutir y de apelar | Un nivel por dimensión: menos anclas; la discusión es "¿75 o 100?" sobre frases como "limitación menor" |
| Sensibilidad fina | Detectó el faltante real del caso excelente (R2: versión de herramienta → hallazgo H1) | Invisible para A1: dio 100 con y sin el faltante |
| Ambigüedad residual | Baja: checks binarios, valores permitidos, regla de desempate | Media: "cumplimiento sustantivo", "limitación menor" quedan a criterio del modelo; sin regla de desempate entre niveles |
| Anti-gaming | Reglas explícitas (corridas duplicadas, cronología, banderas `EVIDENCIA_INCONSISTENTE`) | Reglas generales de evidencia; sin banderas formales — el gaming queda solo narrado |
| Formato de devolución | Definido en la rúbrica (§9) — el agente lo referencia | No definido: lo tiene que aportar el system prompt |
| Puntajes | Enteros | Fraccionarios (31,25 / 11,25) — raro para una nota, habría que definir redondeo |
| Legibilidad humana / costo | ~480 líneas; más tokens por corrida | 124 líneas; ~4× más barata por corrida y mucho más fácil de leer |
| Estado de integración | El system prompt del agente ya está escrito contra ella; calibración completa hecha | Requiere reescribir el núcleo del system prompt y recalibrar |

## Lectura de la Dupla 3 (propuesta, decide el grupo)

Para el **parcial que cierra el jueves**, recomendamos **V3 como rúbrica ejecutable**: es el
único stack probado de punta a punta (rúbrica + agente + calibración + esta comparación), su
granularidad detecta diferencias que A1 no ve, y su formato de salida ya está cableado al
agente. El costo de adoptar A1 hoy no es la rúbrica en sí (es buena) sino la reescritura del
agente y la recalibración completa en 4 días.

La A1 tiene virtudes que no habría que tirar: propuesta concreta — usarla como **resumen
legible de la rúbrica** (por ejemplo referenciada desde el README para el lector humano),
manteniendo V3 como la fuente que ejecuta el agente. Si el grupo prefiere A1 como ejecutable,
lo mínimo indispensable antes del jueves: definir formato de devolución y redondeo, portar la
sección de seguridad del prompt, reescribir el núcleo de puntuación del agente y re-correr
los tres casos (~1 día de trabajo).

**Límites de este test:** un solo operador y modelo (el mismo que corrió V3), una corrida por
rúbrica, y los casos fueron construidos por nosotros conociendo V3 — sesgo posible a favor de
V3 en el caso excelente. La verificación ideal es que otro integrante repita ambas corridas
(instrucciones en `calibracion.md`, pendiente 1).
