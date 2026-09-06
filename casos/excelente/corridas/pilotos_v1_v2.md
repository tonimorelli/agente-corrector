# Corridas piloto (V1 y V2) — el "antes" de las iteraciones

Registro de las corridas de prueba que motivaron los cambios de contrato documentados en
[../DECISIONES.md](../DECISIONES.md). Se conservan como evidencia del antes/después.
La entrada de ambos pilotos fue un CSV de ensayo de 8 filas (subconjunto de facturas reales
sintetizadas), archivado abajo.

## Entrada de los pilotos (`facturas_prueba.csv`)

```csv
factura_id,proveedor,cuit,emision,vencimiento,monto_ars,descuento_pronto_pago_pct,proveedor_critico
FC-0781,Cables Sur SRL,30-71111111-1,2026-08-03,2026-08-21,980000,0,SI
FC-0782,Iluminar SA,30-71222222-3,2026-08-04,2026-08-19,310500,0,NO
FC-0783,Electro Mayorista SA,30-71333333-5,2026-08-05,2026-09-04,1450000,3,NO
FC-0784,Plasticos del Plata SRL,30-71444444-7,2026-08-06,2026-08-30,220000,0,NO
FC-0785,Papelera Norte SA,30-72222222-2,2026-08-07,2026-09-20,64000,0,NO
FC-0786,Herrajes Central SA,30-71777777-2,2026-08-08,2026-09-01,410800,0,NO
FC-0787,Ferretek SA,30-73333333-3,2026-08-08,2026-08-28,,0,NO
FC-0788,Cobre Argentino SA,30-71999999-6,2026-08-10,2026-08-27,2900000,0,SI
```

(La fila FC-0787 sin monto quedó en el CSV de ensayo por accidente — y terminó siendo el
hallazgo más valioso del proceso.)

## Piloto A — prompt V1, dos ejecuciones (18/8, 15:10 y 15:24 ART)

- **Prompt:** V1 (salida pedida como "tabla con las prioridades", sin esquema)
- **Modelo:** `claude-haiku-4-5` · temperatura: `NO_DISPONIBLE`

Ejecución A1 (extracto textual de la salida):

```
| Factura | Proveedor | Prioridad |
|---|---|---|
| FC-0788 | Cobre Argentino SA | URGENTE |
| FC-0781 | Cables Sur SRL | URGENTE |
| FC-0782 | Iluminar SA | Alta |
...
Además, sugiero renegociar el plazo con Cables Sur para aliviar la caja de agosto.
```

Ejecución A2, misma entrada (extracto):

```
Prioridad 1 - Pagar esta semana: FC-0781, FC-0782, FC-0788 y FC-0783 (por el descuento).
Prioridad 2 - Puede esperar: FC-0784, FC-0786.
Prioridad 3: FC-0785. No incluyo total general porque hay una factura sin monto.
```

**Problemas observados (citados en DECISIONES, iteración 1):** las dos salidas usan escalas
distintas ("URGENTE/Alta" vs. "Prioridad 1/2/3"), una trae total y la otra no, una agrega un
consejo financiero fuera de rol. Imposible comparar corridas o automatizar la lectura.

## Piloto B — prompt V2, una ejecución (20/8, 11:02 ART)

- **Prompt:** V2 (ya con esquema JSON, sin regla de datos faltantes)
- **Modelo:** `claude-haiku-4-5` · temperatura: `NO_DISPONIBLE`

Extracto textual de la salida:

```json
{
  "facturas_procesadas": 8,
  "facturas_omitidas": 0,
  "total_pendiente_ars": 6685300,
  "prioridades": [
    {"factura_id": "FC-0787", "proveedor": "Ferretek SA", "monto_ars": 350000,
     "prioridad": "alta", "motivo": "vence en 8 dias; monto estimado por promedio del proveedor"}
  ]
}
```

**Problema observado (citado en DECISIONES, iteración 2):** FC-0787 no tiene monto en el CSV y
el agente **inventó** `350000` ("estimado por promedio del proveedor") y lo sumó al total. Un
monto inventado en un flujo de pagos es el peor error posible del sistema (riesgo R1).

**Después:** la misma situación con el prompt V3 produce omisión + `ABSTENCION_PARCIAL`
— ver [corrida_5_caso_limite.md](corrida_5_caso_limite.md).
