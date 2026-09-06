# DECISIONES — historia del proceso

Registro de cómo se construyó el sistema: qué falló, qué se decidió, qué se cambió y cómo se
verificó. Las versiones del contrato se identifican como V1, V2 y V3 (V3 es la vigente, en
[prompts/system_prompt.md](prompts/system_prompt.md)).

## Iteración 1 — de prosa libre a esquema JSON (18–19/8)

- **Problema observado:** con el prompt V1, dos ejecuciones sobre el mismo CSV de ensayo
  devolvieron estructuras distintas: una tabla con escala "URGENTE/Alta", una lista con
  "Prioridad 1/2/3", total presente en una y ausente en la otra, y hasta un consejo financiero
  no pedido. Evidencia: [corridas/pilotos_v1_v2.md](corridas/pilotos_v1_v2.md), piloto A
  (ejecuciones A1 y A2 del 18/8).
- **Decisión:** la salida no puede ser prosa; tiene que ser un dato. Se define un esquema JSON
  fijo con campos obligatorios, escala cerrada `alta|media|baja`, totales y estados, más un
  memo acotado a 5 líneas. Se agrega la restricción "no des consejos financieros".
- **Cambio:** system prompt V1 → V2 (nace el §4 "Formato de salida" con el esquema completo, y
  la restricción de rol en §5).
- **Verificación del efecto:** con V3 (que conserva el esquema de V2), la corrida 1 y su
  reproducción (corrida 4) devuelven el mismo JSON válido con 12/12 prioridades coincidentes:
  [corridas/corrida_4_reproduccion.md](corridas/corrida_4_reproduccion.md). El problema de
  inconsistencia estructural no volvió a aparecer en ninguna corrida oficial.

## Iteración 2 — prohibido adivinar (20–21/8)

- **Problema observado:** con V2, el piloto B procesó una fila sin monto (`FC-0787`) inventando
  el valor: `"monto estimado por promedio del proveedor": 350000`, y lo sumó al total. En un
  flujo de cuentas a pagar, un monto alucinado es el error más caro posible. Evidencia:
  [corridas/pilotos_v1_v2.md](corridas/pilotos_v1_v2.md), piloto B (20/8, 11:02).
- **Decisión:** el agente no completa datos faltantes bajo ninguna circunstancia. Ante dato
  crítico ausente o inválido: omite la factura, la lista en `omitidas` con motivo, agrega una
  alerta accionable y degrada el estado a `ABSTENCION_PARCIAL`. Ante CSV inutilizable:
  `ERROR_DATOS` sin procesar nada.
- **Cambio:** system prompt V2 → V3 (nace el §5 "Restricciones" con la regla dura "prohibido
  adivinar", los campos `omitidas`/`alertas`/`estado` se agregan al esquema del §4, y se añade
  el tercer ejemplo del §6 con una fila sin monto).
- **Verificación del efecto:** la corrida 5 reproduce el escenario del piloto B (fila sin monto
  + fecha inválida) con V3: el agente omite ambas facturas, no inventa valores, y el total suma
  solo las procesadas. Antes/después documentado en
  [corridas/corrida_5_caso_limite.md](corridas/corrida_5_caso_limite.md).

## Iteración 3 — elección de modelo por costo-desempeño (24/8)

- **Problema/hipótesis:** el sistema se diseñó corriendo un modelo frontier; la hipótesis
  (regla de la Clase 2: "se diseña con el grande y se opera con el más chico que pase la
  prueba") era que un modelo liviano alcanzaba para una tarea tan especificada.
- **Decisión:** correr ambos modelos sobre la misma entrada (CSV de la corrida 1) con el mismo
  contrato y comparar contra el mismo criterio de éxito.
- **Cambio:** la configuración de operación pasa del frontier al liviano `claude-haiku-4-5`.
  El contrato no se tocó.
- **Verificación del efecto:** ambos modelos cumplen el criterio con prioridades idénticas
  (12/12) y mismos totales; el liviano cuesta ~20% del frontier. Evidencia y cálculo:
  [corridas/comparacion_modelos.md](corridas/comparacion_modelos.md). Las corridas oficiales
  posteriores (2, 3, 4 y 5) corrieron todas con el liviano y ninguna falló el criterio.

## Alcance, supuestos y pendientes

**Decisiones de alcance (con motivo):**

- Solo facturas en ARS. Las (pocas) facturas en USD quedan fuera porque priorizar en dos
  monedas exige un tipo de cambio de referencia, y no quiero que el agente "elija" un valor:
  ese dato lo maneja la jefa. Impacto: ~2 facturas/mes se priorizan a mano.
- Sin conexión directa al sistema contable: el export manual del CSV es deliberado — mantiene
  al agente sin credenciales de ningún sistema de la empresa (ver Gobierno y riesgo en el
  README). Impacto: 5 minutos de trabajo manual por semana, aceptado.
- Los datos del repo público son sintéticos (proveedores y CUIT reemplazados). Motivo:
  confidencialidad comercial. Las corridas reproducen fielmente la estructura y los resultados
  de las corridas reales.

**Supuestos vigentes:**

- El layout de columnas del export del contable es estable (si cambia, aplica `ERROR_DATOS` y
  se ajusta el contrato).
- La regla de negocio "crítico = single source" la mantiene actualizada la jefa en el sistema
  contable; el agente no la infiere.

**Pendientes (no bloquean el uso actual):**

- Script de validación automática del JSON contra el esquema (hoy la validación la hago yo
  con un validador online; conviene automatizarla para eliminar el paso manual).
- Probar un mes completo con doble corrida (lunes y miércoles) para medir si conviene
  institucionalizar la corrida previa al pago.
- Evaluar registrar las corridas reales (con datos verdaderos) en un repo privado de la
  empresa, manteniendo este público solo como plantilla.
