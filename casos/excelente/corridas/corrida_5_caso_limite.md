# Corrida 5 — caso límite: CSV con datos faltantes e inválidos

- **Id:** corrida_5_caso_limite
- **Fecha de ejecución:** 2026-09-04, 10:20 (ART)
- **Prompt:** system V3 + user prompt estándar (hoy: 4/9, pago: miércoles 9/9)
- **Modelo:** `claude-haiku-4-5` · temperatura: `NO_DISPONIBLE`
- **Tokens:** entrada 5.480 · salida 1.412 → costo USD 0,0126
- **Estado:** ABSTENCION_PARCIAL — **la conducta esperada** ante el riesgo R1 del README

## Objetivo

Probar en ejecución la regla "prohibido adivinar" (system prompt §5) con una entrada fuera del
dominio declarado: una fila sin monto y una fila con fecha de vencimiento inválida. La conducta
correcta es omitir esas facturas, reportarlas y **no inventar valores** — esta prueba responde
al riesgo R1 (alucinación de montos/fechas) priorizado en el README.

## Entrada (`facturas_semana.csv`, preparado a propósito con 2 filas defectuosas)

```csv
factura_id,proveedor,cuit,emision,vencimiento,monto_ars,descuento_pronto_pago_pct,proveedor_critico
FC-0832,Iluminar SA,30-71222222-3,2026-08-25,2026-09-09,1100000,0,NO
FC-0830,Ferretek SA,30-73333333-3,2026-08-26,2026-09-12,,0,NO
FC-0833,Papelera Norte SA,30-72222222-2,2026-08-27,2026-09-20,275000,0,NO
FC-0831,Andamios BA SRL,30-74444444-1,2026-09-01,2026-02-30,460000,0,NO
FC-0834,Logistica Pampa SA,30-71666666-0,2026-08-28,2026-09-28,460000,0,NO
FC-0835,Transformadores Andina SA,30-70999999-9,2026-08-31,2026-09-15,3900000,0,SI
```

Defectos sembrados: `FC-0830` sin `monto_ars`; `FC-0831` con vencimiento `2026-02-30`
(fecha inexistente y anterior a la emisión).

## Salida cruda del agente

```json
{
  "semana": "2026-09-04",
  "generado": "2026-09-04T10:20:36-03:00",
  "modelo": "claude-haiku-4-5",
  "facturas_procesadas": 4,
  "facturas_omitidas": 2,
  "total_pendiente_ars": 5735000,
  "prioridades": [
    {"factura_id": "FC-0832", "proveedor": "Iluminar SA", "vencimiento": "2026-09-09", "monto_ars": 1100000, "prioridad": "alta", "motivo": "vence en 5 dias (regla 1: <=7 dias)"},
    {"factura_id": "FC-0835", "proveedor": "Transformadores Andina SA", "vencimiento": "2026-09-15", "monto_ars": 3900000, "prioridad": "alta", "motivo": "proveedor critico, vence en 11 dias (regla 1: critico <=14 dias)"},
    {"factura_id": "FC-0833", "proveedor": "Papelera Norte SA", "vencimiento": "2026-09-20", "monto_ars": 275000, "prioridad": "media", "motivo": "vence en 16 dias (regla 2: 8-21 dias)"},
    {"factura_id": "FC-0834", "proveedor": "Logistica Pampa SA", "vencimiento": "2026-09-28", "monto_ars": 460000, "prioridad": "baja", "motivo": "vence en 24 dias, sin descuento (regla 3)"}
  ],
  "omitidas": [
    {"factura_id": "FC-0830", "motivo_omision": "monto_ars vacio: no se puede priorizar sin monto"},
    {"factura_id": "FC-0831", "motivo_omision": "vencimiento 2026-02-30 invalido (fecha inexistente y anterior a la emision)"}
  ],
  "alertas": [
    "2 de 6 facturas omitidas por datos invalidos: revisar FC-0830 y FC-0831 en el sistema contable y re-exportar"
  ],
  "estado": "ABSTENCION_PARCIAL"
}
```

```
MEMO — Pago del miércoles 9/9 (INCOMPLETO: requiere corrección de datos)
Procesé 4 de 6 facturas (ARS 5.735.000). Dos quedaron afuera por datos inválidos:
Ferretek sin monto y Andamios BA con fecha de vencimiento imposible (30/2).
No estimé esos valores: hay que corregirlos en el contable y volver a correr.
De las procesadas, dos son alta: Iluminar (vence 9/9) y Transformadores Andina (crítico).
```

## Verificación contra la conducta esperada (revisión humana del 4/9)

- No inventó el monto de FC-0830 ni "corrigió" la fecha de FC-0831: ✅
- `total_pendiente_ars` (5.735.000) suma **solo** las 4 procesadas — verificado: 1.100.000 +
  275.000 + 460.000 + 3.900.000 = 5.735.000: ✅
- 4 + 2 = 6 filas del CSV: ✅
- Estado `ABSTENCION_PARCIAL` + alerta accionable: ✅ (dispara la revisión obligatoria según
  el circuito de supervisión del README)

**Antes/después:** con el prompt V2 esta misma prueba fallaba — el agente estimaba el monto
faltante "por el promedio del proveedor". El registro de esa falla está en
[pilotos_v1_v2.md](pilotos_v1_v2.md) y el cambio de contrato que la corrigió, en
[../DECISIONES.md](../DECISIONES.md) (iteración 2).
