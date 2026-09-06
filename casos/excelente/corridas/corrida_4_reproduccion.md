# Corrida 4 — reproducción de la corrida 1 (prueba de estabilidad)

- **Id:** corrida_4_reproduccion
- **Fecha de ejecución:** 2026-09-01, 21:33 (ART)
- **Prompt:** idéntico al de la corrida 1 (system V3 + user prompt con fechas del 24/8)
- **Entrada:** el **mismo CSV** de la [corrida 1](corrida_1.md) (12 facturas, recreado del
  registro; no se modificó ninguna fila)
- **Modelo:** `claude-haiku-4-5` · temperatura: `NO_DISPONIBLE`
- **Tokens:** entrada 6.211 · salida 1.958 → costo USD 0,0160
- **Estado:** OK — reproduce la corrida 1 según el criterio de reproducción del README

## Objetivo

Aplicar el **criterio de reproducción** definido en el README: misma entrada → (a) JSON válido,
(b) mismos totales y conteos, (c) misma `prioridad` por factura. Se admite otra redacción de
`motivo` y del memo.

## Salida cruda del agente (resumida a los campos comparados; JSON completo conservado)

```json
{
  "semana": "2026-08-24",
  "generado": "2026-09-01T21:33:08-03:00",
  "modelo": "claude-haiku-4-5",
  "facturas_procesadas": 12,
  "facturas_omitidas": 0,
  "total_pendiente_ars": 15810400,
  "prioridades_resumen": {
    "alta": ["FC-0801", "FC-0795", "FC-0802", "FC-0803", "FC-0814"],
    "media": ["FC-0806", "FC-0807", "FC-0810", "FC-0811", "FC-0813"],
    "baja": ["FC-0808", "FC-0809"]
  },
  "omitidas": [],
  "alertas": [],
  "estado": "OK"
}
```

## Comparación contra la corrida 1

| Criterio | Corrida 1 | Corrida 4 | ¿Coincide? |
|---|---|---|---|
| JSON valida contra el esquema | Sí | Sí | ✅ |
| `facturas_procesadas` / `omitidas` | 12 / 0 | 12 / 0 | ✅ |
| `total_pendiente_ars` | 15.810.400 | 15.810.400 | ✅ |
| Prioridad por factura (12 facturas) | — | — | ✅ 12/12 idénticas |
| Redacción de `motivo` | — | — | Difiere en 3 facturas (admitido por el criterio) |

**Conclusión:** el sistema es estable bajo el criterio definido. Ejemplo de variación admitida:
corrida 1 dice "proveedor critico pero vence en 17 dias (>14): aplica regla 2" y corrida 4 dice
"critico con vencimiento a 17 dias, fuera de la ventana de 14: regla 2" — misma decisión,
distinta redacción.
