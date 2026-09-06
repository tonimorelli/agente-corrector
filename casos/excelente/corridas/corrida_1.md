# Corrida 1 — semana del 24/8

- **Id:** corrida_1
- **Fecha de ejecución:** 2026-08-24, 09:12 (ART)
- **Prompt:** system V3 + user prompt estándar (hoy: 24/8, pago: miércoles 26/8)
- **Modelo:** `claude-haiku-4-5` · temperatura: `NO_DISPONIBLE` (la plataforma no la expone)
- **Tokens (reportados por la plataforma):** entrada 6.214 · salida 1.982 → costo USD 0,0161
- **Estado:** OK — cumple el criterio de éxito (ver verificación al pie)

## Entrada (`facturas_semana.csv`, exportado del contable el 24/8)

```csv
factura_id,proveedor,cuit,emision,vencimiento,monto_ars,descuento_pronto_pago_pct,proveedor_critico
FC-0801,Cables Sur SRL,30-71111111-1,2026-08-10,2026-08-27,1250000,0,SI
FC-0795,Transformadores Andina SA,30-70999999-9,2026-08-05,2026-09-04,3480000,0,SI
FC-0802,Iluminar SA,30-71222222-3,2026-08-11,2026-08-25,640500,0,NO
FC-0803,Electro Mayorista SA,30-71333333-5,2026-08-12,2026-09-15,2100000,3,NO
FC-0806,Plasticos del Plata SRL,30-71444444-7,2026-08-14,2026-09-08,415000,0,NO
FC-0807,Seguridad Total SRL,30-71555555-9,2026-08-14,2026-09-11,289900,0,NO
FC-0808,Logistica Pampa SA,30-71666666-0,2026-08-17,2026-09-18,730000,0,NO
FC-0809,Papelera Norte SA,30-72222222-2,2026-08-20,2026-09-30,89000,0,NO
FC-0810,Herrajes Central SA,30-71777777-2,2026-08-18,2026-09-09,512300,0,NO
FC-0811,Quimica Litoral SA,30-71888888-4,2026-08-19,2026-09-02,947000,0,NO
FC-0813,Cobre Argentino SA,30-71999999-6,2026-08-20,2026-09-10,5200000,0,SI
FC-0814,Embalajes Rio SRL,30-72111111-8,2026-08-21,2026-08-26,156700,0,NO
```

## Salida cruda del agente

```json
{
  "semana": "2026-08-24",
  "generado": "2026-08-24T09:12:41-03:00",
  "modelo": "claude-haiku-4-5",
  "facturas_procesadas": 12,
  "facturas_omitidas": 0,
  "total_pendiente_ars": 15810400,
  "prioridades": [
    {"factura_id": "FC-0801", "proveedor": "Cables Sur SRL", "vencimiento": "2026-08-27", "monto_ars": 1250000, "prioridad": "alta", "motivo": "vence en 3 dias (regla 1: <=7 dias)"},
    {"factura_id": "FC-0795", "proveedor": "Transformadores Andina SA", "vencimiento": "2026-09-04", "monto_ars": 3480000, "prioridad": "alta", "motivo": "proveedor critico, vence en 11 dias (regla 1: critico <=14 dias)"},
    {"factura_id": "FC-0802", "proveedor": "Iluminar SA", "vencimiento": "2026-08-25", "monto_ars": 640500, "prioridad": "alta", "motivo": "vence en 1 dia (regla 1: <=7 dias)"},
    {"factura_id": "FC-0803", "proveedor": "Electro Mayorista SA", "vencimiento": "2026-09-15", "monto_ars": 2100000, "prioridad": "alta", "motivo": "descuento pronto pago 3% (regla 1: >=2%)"},
    {"factura_id": "FC-0814", "proveedor": "Embalajes Rio SRL", "vencimiento": "2026-08-26", "monto_ars": 156700, "prioridad": "alta", "motivo": "vence en 2 dias (regla 1: <=7 dias)"},
    {"factura_id": "FC-0806", "proveedor": "Plasticos del Plata SRL", "vencimiento": "2026-09-08", "monto_ars": 415000, "prioridad": "media", "motivo": "vence en 15 dias (regla 2: 8-21 dias)"},
    {"factura_id": "FC-0807", "proveedor": "Seguridad Total SRL", "vencimiento": "2026-09-11", "monto_ars": 289900, "prioridad": "media", "motivo": "vence en 18 dias (regla 2: 8-21 dias)"},
    {"factura_id": "FC-0810", "proveedor": "Herrajes Central SA", "vencimiento": "2026-09-09", "monto_ars": 512300, "prioridad": "media", "motivo": "vence en 16 dias (regla 2: 8-21 dias)"},
    {"factura_id": "FC-0811", "proveedor": "Quimica Litoral SA", "vencimiento": "2026-09-02", "monto_ars": 947000, "prioridad": "media", "motivo": "vence en 9 dias (regla 2: 8-21 dias)"},
    {"factura_id": "FC-0813", "proveedor": "Cobre Argentino SA", "vencimiento": "2026-09-10", "monto_ars": 5200000, "prioridad": "media", "motivo": "proveedor critico pero vence en 17 dias (>14): aplica regla 2"},
    {"factura_id": "FC-0808", "proveedor": "Logistica Pampa SA", "vencimiento": "2026-09-18", "monto_ars": 730000, "prioridad": "baja", "motivo": "vence en 25 dias, sin descuento (regla 3)"},
    {"factura_id": "FC-0809", "proveedor": "Papelera Norte SA", "vencimiento": "2026-09-30", "monto_ars": 89000, "prioridad": "baja", "motivo": "vence en 37 dias, sin descuento (regla 3)"}
  ],
  "omitidas": [],
  "alertas": [],
  "estado": "OK"
}
```

```
MEMO — Pago del miércoles 26/8
Recomiendo priorizar 5 facturas (ARS 7.627.200): dos vencen esta semana, dos son de
proveedores críticos o con vencimiento inmediato y una pierde un descuento del 3%.
Las 5 medias (ARS 7.364.200) pueden esperar al próximo miércoles sin riesgo.
Total pendiente de la semana: ARS 15.810.400 en 12 facturas. Sin datos faltantes.
```

## Verificación contra el criterio de éxito (revisión humana del 24/8)

- JSON valida contra el esquema del contrato: ✅
- `facturas_procesadas (12) + facturas_omitidas (0)` = 12 filas del CSV: ✅
- `total_pendiente_ars` = 15.810.400 = suma exacta de los montos del CSV (verificado en
  planilla): ✅
- 12/12 facturas con `prioridad` y `motivo` citando regla: ✅
- Revisión de las 5 `alta` contra comprobantes: las 5 correctas. Suma de altas del memo
  (7.627.200) verificada: 1.250.000 + 3.480.000 + 640.500 + 2.100.000 + 156.700 = 7.627.200 ✅
