# Comparación de modelos — frontier vs. liviano (mismas entradas, mismo criterio)

- **Fecha:** 2026-08-24, 10:40 (ART) — inmediatamente después de la corrida 1
- **Entrada:** el mismo CSV de 12 facturas de la [corrida 1](corrida_1.md), sin cambios
- **Prompts:** system V3 + user prompt de la corrida 1, idénticos para ambos modelos
- **Criterio de comparación:** el criterio de éxito del README (JSON válido, totales exactos,
  12/12 con prioridad y motivo) + coincidencia de prioridades entre modelos
- **Precios:** página de precios de Anthropic consultada el 24/8 (mismos valores que la
  consulta del 2/9 citada en el README)

## Resultados

| Métrica | `claude-fable-5` (frontier) | `claude-haiku-4-5` (liviano) |
|---|---|---|
| JSON valida contra esquema | ✅ | ✅ |
| `facturas_procesadas` / `omitidas` | 12 / 0 | 12 / 0 |
| `total_pendiente_ars` | 15.810.400 ✅ | 15.810.400 ✅ |
| Prioridades (vs. revisión humana) | 12/12 correctas | 12/12 correctas |
| Tokens entrada / salida | 6.214 / 2.045 | 6.214 / 1.982 |
| Costo de la corrida | USD 0,0782 | USD 0,0161 |

Salida cruda del frontier conservada (resumen de prioridades):

```json
{
  "modelo": "claude-fable-5",
  "generado": "2026-08-24T10:40:12-03:00",
  "facturas_procesadas": 12,
  "facturas_omitidas": 0,
  "total_pendiente_ars": 15810400,
  "prioridades_resumen": {
    "alta": ["FC-0801", "FC-0795", "FC-0802", "FC-0803", "FC-0814"],
    "media": ["FC-0806", "FC-0807", "FC-0810", "FC-0811", "FC-0813"],
    "baja": ["FC-0808", "FC-0809"]
  },
  "estado": "OK"
}
```

## Decisión

Ambos modelos cumplen el criterio de éxito con resultados idénticos en los campos comparados.
Aplicando la regla del curso — **el modelo más chico que hace bien la tarea** — se elige
`claude-haiku-4-5`: misma calidad medida sobre la misma entrada, ~20% del costo. Si en el futuro
una corrida del liviano falla el criterio, el protocolo es primero revisar el contrato y recién
después subir de modelo (regla de la Clase 2). Decisión registrada en
[../DECISIONES.md](../DECISIONES.md), iteración 3.
