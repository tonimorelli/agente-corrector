# User prompt — corrida semanal

Este es el user prompt que se envía en cada corrida (solo cambia la fecha de la semana):

```
Corrida semanal de prioridades de pago.

Semana del pago: miércoles [FECHA_MIERCOLES].
Fecha de hoy: [FECHA_HOY].

Leé el archivo facturas_semana.csv del directorio de trabajo y devolvé el JSON y el memo
según tu contrato. Recordá: si un dato crítico falta, omitís y reportás; no adivinás.
```

## Variantes usadas

- **Corridas 1, 2 y 4:** el prompt de arriba, con las fechas de cada semana.
- **Corrida 3 (corte urgente):** se agrega la línea
  `Corrida extraordinaria: el pago se adelanta al viernes [FECHA]. Ajustá el cálculo de días al viernes.`
- **Corrida 5 (caso límite):** mismo prompt que las corridas normales; lo que cambia es la
  entrada (CSV con datos faltantes), no el pedido. La conducta ante el dato faltante la define
  el system prompt, no el user prompt.
