# Corrida 2 — semana del 31/8

- **Id:** corrida_2
- **Fecha de ejecución:** 2026-08-31, 08:47 (ART)
- **Prompt:** system V3 + user prompt estándar (hoy: 31/8, pago: miércoles 2/9)
- **Modelo:** `claude-haiku-4-5` · temperatura: `NO_DISPONIBLE`
- **Tokens:** entrada 5.730 · salida 1.641 → costo USD 0,0139
- **Estado:** OK — cumple el criterio de éxito

## Entrada (`facturas_semana.csv`, exportado del contable el 31/8)

```csv
factura_id,proveedor,cuit,emision,vencimiento,monto_ars,descuento_pronto_pago_pct,proveedor_critico
FC-0811,Quimica Litoral SA,30-71888888-4,2026-08-19,2026-09-02,947000,0,NO
FC-0813,Cobre Argentino SA,30-71999999-6,2026-08-20,2026-09-10,5200000,0,SI
FC-0806,Plasticos del Plata SRL,30-71444444-7,2026-08-14,2026-09-08,415000,0,NO
FC-0807,Seguridad Total SRL,30-71555555-9,2026-08-14,2026-09-11,289900,0,NO
FC-0810,Herrajes Central SA,30-71777777-2,2026-08-18,2026-09-09,512300,0,NO
FC-0808,Logistica Pampa SA,30-71666666-0,2026-08-17,2026-09-18,730000,0,NO
FC-0809,Papelera Norte SA,30-72222222-2,2026-08-20,2026-09-30,89000,0,NO
FC-0821,Cables Sur SRL,30-71111111-1,2026-08-27,2026-09-21,2780000,0,SI
FC-0822,Vidrios Sur SA,30-72333333-4,2026-08-28,2026-09-28,610000,2.5,NO
```

## Salida cruda del agente

```json
{
  "semana": "2026-08-31",
  "generado": "2026-08-31T08:47:19-03:00",
  "modelo": "claude-haiku-4-5",
  "facturas_procesadas": 9,
  "facturas_omitidas": 0,
  "total_pendiente_ars": 11573200,
  "prioridades": [
    {"factura_id": "FC-0811", "proveedor": "Quimica Litoral SA", "vencimiento": "2026-09-02", "monto_ars": 947000, "prioridad": "alta", "motivo": "vence en 2 dias (regla 1: <=7 dias)"},
    {"factura_id": "FC-0813", "proveedor": "Cobre Argentino SA", "vencimiento": "2026-09-10", "monto_ars": 5200000, "prioridad": "alta", "motivo": "proveedor critico, vence en 10 dias (regla 1: critico <=14 dias)"},
    {"factura_id": "FC-0822", "proveedor": "Vidrios Sur SA", "vencimiento": "2026-09-28", "monto_ars": 610000, "prioridad": "alta", "motivo": "descuento pronto pago 2.5% (regla 1: >=2%)"},
    {"factura_id": "FC-0806", "proveedor": "Plasticos del Plata SRL", "vencimiento": "2026-09-08", "monto_ars": 415000, "prioridad": "media", "motivo": "vence en 8 dias (regla 2: 8-21 dias)"},
    {"factura_id": "FC-0807", "proveedor": "Seguridad Total SRL", "vencimiento": "2026-09-11", "monto_ars": 289900, "prioridad": "media", "motivo": "vence en 11 dias (regla 2: 8-21 dias)"},
    {"factura_id": "FC-0810", "proveedor": "Herrajes Central SA", "vencimiento": "2026-09-09", "monto_ars": 512300, "prioridad": "media", "motivo": "vence en 9 dias (regla 2: 8-21 dias)"},
    {"factura_id": "FC-0808", "proveedor": "Logistica Pampa SA", "vencimiento": "2026-09-18", "monto_ars": 730000, "prioridad": "media", "motivo": "vence en 18 dias (regla 2: 8-21 dias)"},
    {"factura_id": "FC-0821", "proveedor": "Cables Sur SRL", "vencimiento": "2026-09-21", "monto_ars": 2780000, "prioridad": "media", "motivo": "proveedor critico pero vence en 21 dias (>14): aplica regla 2"},
    {"factura_id": "FC-0809", "proveedor": "Papelera Norte SA", "vencimiento": "2026-09-30", "monto_ars": 89000, "prioridad": "baja", "motivo": "vence en 30 dias, sin descuento (regla 3)"}
  ],
  "omitidas": [],
  "alertas": [],
  "estado": "OK"
}
```

```
MEMO — Pago del miércoles 2/9
Tres facturas altas por ARS 6.757.000: Química Litoral vence pasado mañana, Cobre
Argentino es crítico y vence el 10/9, y Vidrios Sur pierde un 2,5% de descuento.
Cinco medias por ARS 4.727.200 pueden ir al miércoles siguiente. Una baja (ARS 89.000).
Total pendiente: ARS 11.573.200 en 9 facturas. Sin datos faltantes.
```

## Verificación contra el criterio de éxito (revisión humana del 31/8)

- JSON valida contra el esquema: ✅
- 9 + 0 = 9 filas del CSV: ✅
- `total_pendiente_ars` = 11.573.200 = suma exacta del CSV: ✅
- 9/9 con `prioridad` y `motivo`: ✅
- Nota de la revisión: FC-0806 pasó de 15 días (corrida 1) a 8 días y sigue `media`; el corte
  alta/media en 7 días quedó bien aplicado en el borde. Las 3 `alta` verificadas contra
  comprobante: correctas.
