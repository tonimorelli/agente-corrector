# Corrida 3 — corte urgente del 3/9 (pago adelantado a viernes 4/9)

- **Id:** corrida_3
- **Fecha de ejecución:** 2026-09-03, 17:05 (ART)
- **Prompt:** system V3 + user prompt estándar **+ variante de corrida extraordinaria**
  (ver [../prompts/user_prompt.md](../prompts/user_prompt.md)): el pago se adelanta al viernes 4/9
- **Modelo:** `claude-haiku-4-5` · temperatura: `NO_DISPONIBLE`
- **Tokens:** entrada 5.322 · salida 1.190 → costo USD 0,0113
- **Estado:** OK — cumple el criterio de éxito
- **Contexto:** la jefa pidió adelantar pagos por un feriado bancario; sirve además como prueba
  de que el cálculo de días se ajusta a otra fecha de pago.

## Entrada (`facturas_semana.csv`, re-export del contable el 3/9)

```csv
factura_id,proveedor,cuit,emision,vencimiento,monto_ars,descuento_pronto_pago_pct,proveedor_critico
FC-0806,Plasticos del Plata SRL,30-71444444-7,2026-08-14,2026-09-08,415000,0,NO
FC-0807,Seguridad Total SRL,30-71555555-9,2026-08-14,2026-09-11,289900,0,NO
FC-0810,Herrajes Central SA,30-71777777-2,2026-08-18,2026-09-09,512300,0,NO
FC-0808,Logistica Pampa SA,30-71666666-0,2026-08-17,2026-09-18,730000,0,NO
FC-0809,Papelera Norte SA,30-72222222-2,2026-08-20,2026-09-30,89000,0,NO
```

## Salida cruda del agente

```json
{
  "semana": "2026-09-03",
  "generado": "2026-09-03T17:05:52-03:00",
  "modelo": "claude-haiku-4-5",
  "facturas_procesadas": 5,
  "facturas_omitidas": 0,
  "total_pendiente_ars": 2036200,
  "prioridades": [
    {"factura_id": "FC-0806", "proveedor": "Plasticos del Plata SRL", "vencimiento": "2026-09-08", "monto_ars": 415000, "prioridad": "alta", "motivo": "vence en 5 dias (regla 1: <=7 dias)"},
    {"factura_id": "FC-0810", "proveedor": "Herrajes Central SA", "vencimiento": "2026-09-09", "monto_ars": 512300, "prioridad": "alta", "motivo": "vence en 6 dias (regla 1: <=7 dias)"},
    {"factura_id": "FC-0807", "proveedor": "Seguridad Total SRL", "vencimiento": "2026-09-11", "monto_ars": 289900, "prioridad": "media", "motivo": "vence en 8 dias (regla 2: 8-21 dias)"},
    {"factura_id": "FC-0808", "proveedor": "Logistica Pampa SA", "vencimiento": "2026-09-18", "monto_ars": 730000, "prioridad": "media", "motivo": "vence en 15 dias (regla 2: 8-21 dias)"},
    {"factura_id": "FC-0809", "proveedor": "Papelera Norte SA", "vencimiento": "2026-09-30", "monto_ars": 89000, "prioridad": "baja", "motivo": "vence en 27 dias, sin descuento (regla 3)"}
  ],
  "omitidas": [],
  "alertas": [],
  "estado": "OK"
}
```

```
MEMO — Pago adelantado del viernes 4/9
Dos facturas pasan a alta por el corte del calendario: Plásticos del Plata (vence 8/9)
y Herrajes Central (vence 9/9), por ARS 927.300 en total.
Las otras tres pueden esperar al miércoles siguiente. Total pendiente: ARS 2.036.200
en 5 facturas. Sin datos faltantes.
```

## Verificación contra el criterio de éxito (revisión humana del 3/9)

- JSON valida contra el esquema: ✅
- 5 + 0 = 5 filas del CSV: ✅
- `total_pendiente_ars` = 2.036.200 = suma exacta del CSV: ✅
- Interesa el cambio respecto de la corrida 2: FC-0806 y FC-0810 subieron de `media` a `alta`
  porque el horizonte de días cambió — exactamente la conducta esperada de la regla 1.
