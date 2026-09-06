# Priorizador semanal de pagos a proveedores

**Trabajo final — Programación de y con Agentes de IA · MBA UCEMA · 2026 2T**
**Autora:** L. Ferreyra (analista de administración en una pyme distribuidora de insumos eléctricos)

> Caso: todas las semanas dedico ~2 horas a decidir qué facturas de proveedores pagar primero,
> cruzando vencimientos, descuentos por pronto pago y criticidad del proveedor. Este agente
> hace ese análisis en minutos y me deja a mí la decisión final.

## Qué hace el sistema

Cada lunes exporto del sistema contable un CSV con las facturas pendientes. El agente:

1. Lee el archivo `facturas_semana.csv` (herramienta: lectura de archivos locales).
2. Valida los datos (montos, fechas, campos obligatorios). **Si un dato crítico falta, no lo
   inventa: omite la factura y lo reporta** (regla "prohibido adivinar" del contrato).
3. Clasifica cada factura en prioridad `alta / media / baja` según las reglas del contrato.
4. Devuelve un JSON con formato fijo (esquema en [prompts/system_prompt.md](prompts/system_prompt.md), §4)
   más un memo de 5 líneas para mi jefa.

**Criterio de éxito observable:** el JSON valida contra el esquema; `facturas_procesadas +
facturas_omitidas` = filas del CSV; `total_pendiente_ars` = suma exacta de los montos del CSV;
ninguna factura sin `prioridad` y `motivo`; cero valores que no estén en el CSV de entrada.

## Estructura del repositorio

| Componente | Ubicación |
|---|---|
| Contrato del agente (system prompt, con las seis piezas) | [prompts/system_prompt.md](prompts/system_prompt.md) |
| User prompt de cada corrida | [prompts/user_prompt.md](prompts/user_prompt.md) |
| Corrida 1 — semana 24/8 (12 facturas) | [corridas/corrida_1.md](corridas/corrida_1.md) |
| Corrida 2 — semana 31/8 (9 facturas) | [corridas/corrida_2.md](corridas/corrida_2.md) |
| Corrida 3 — corte urgente 3/9 (5 facturas) | [corridas/corrida_3.md](corridas/corrida_3.md) |
| Corrida 4 — reproducción de la corrida 1 (criterio de reproducción) | [corridas/corrida_4_reproduccion.md](corridas/corrida_4_reproduccion.md) |
| Corrida 5 — caso límite: CSV con datos faltantes | [corridas/corrida_5_caso_limite.md](corridas/corrida_5_caso_limite.md) |
| Comparación de modelos (frontier vs. liviano, mismas entradas) | [corridas/comparacion_modelos.md](corridas/comparacion_modelos.md) |
| Historia del proceso: iteraciones, fallas, decisiones | [DECISIONES.md](DECISIONES.md) |

## Cómo reproducir una corrida

1. Herramienta usada: **Claude Code** (agente con acceso de lectura a archivos locales).
   Requiere una cuenta activa; la clave de API se configura como variable de entorno
   `ANTHROPIC_API_KEY` (**nunca** se versiona; este repo no contiene credenciales).
2. Modelo: `claude-haiku-4-5` (liviano; elección justificada abajo). Parámetros en cada corrida;
   la plataforma no expone temperatura → se registra `NO_DISPONIBLE`.
3. Cargar [prompts/system_prompt.md](prompts/system_prompt.md) como system prompt.
4. Colocar el CSV de la semana como `facturas_semana.csv` en el directorio de trabajo
   (cada corrida incluye su CSV de entrada completo, por lo que el archivo puede recrearse).
5. Enviar el user prompt de [prompts/user_prompt.md](prompts/user_prompt.md).
6. Verificar la salida contra el **criterio de reproducción** (abajo).

**Criterio de reproducción** (tarea no determinista): dos corridas sobre el mismo CSV se
consideran equivalentes si (a) el JSON valida contra el esquema, (b) `total_pendiente_ars` y
el conteo de facturas son idénticos, y (c) la `prioridad` asignada a cada factura coincide.
Se admite variación en la redacción de `motivo` y del memo. La corrida 4 aplica este criterio
contra la corrida 1: 12/12 prioridades coincidentes.

## Supervisión humana (vocabulario del curso)

Nivel de delegación: **L2 — ejecutar con revisión.**

- **El agente hace solo:** leer el CSV, validar, clasificar, generar JSON y memo.
- **Obliga a revisión (disparador):** toda corrida, antes de cargar cualquier pago; y en
  particular cualquier corrida con `estado != OK` o con `alertas` no vacías.
- **Qué verifica la persona (yo):** que el total coincida con el sistema contable, y las
  facturas marcadas `alta` una por una contra el comprobante.
- **Quién firma:** la jefa de administración aprueba la lista de pagos; el agente no ejecuta
  pagos ni escribe en ningún sistema. La responsabilidad del pago es siempre humana.

## Análisis económico

Medición por corrida (tokens reportados por la plataforma, registrados en cada corrida):

| Concepto | Valor típico |
|---|---|
| Tokens de entrada (system + user + CSV de ~12 filas) | ~6.200 |
| Tokens de salida (JSON + memo) | ~1.900 |

Precios usados: página de precios pública de Anthropic, consultada el **2/9/2026**, en USD por
millón de tokens: `claude-haiku-4-5` entrada 1,00 / salida 5,00; `claude-fable-5` (frontier)
entrada 5,00 / salida 25,00.

- **Costo por corrida (liviano):** 6.200/10⁶ × 1,00 + 1.900/10⁶ × 5,00 = 0,0062 + 0,0095 =
  **USD 0,0157**
- **Costo por corrida (frontier):** 6.200/10⁶ × 5,00 + 1.900/10⁶ × 25,00 = **USD 0,0785** (5×)
- **Proyección año base:** 52 corridas semanales + ~10 cortes urgentes = 62 corridas →
  62 × 0,0157 = **USD 0,97/año** con el liviano (vs. USD 4,87 con el frontier).
- **Sensibilidad:** si la empresa duplica proveedores (≈24 facturas/semana), la entrada sube a
  ~9.800 tokens y la salida a ~3.400 → 9.800/10⁶ × 1,00 + 3.400/10⁶ × 5,00 = USD 0,0268 por
  corrida → **USD 1,66/año**. El costo de inferencia es despreciable frente a las ~100 horas/año
  de análisis manual que reemplaza; el costo operativo relevante es el tiempo de revisión humana
  (~15 min/semana), que se mantiene por diseño y no se busca optimizar.

**Elección de modelo (el más chico que hace bien la tarea):** ambos modelos se corrieron sobre
el mismo CSV de la semana 24/8 con el mismo system prompt y el mismo criterio de éxito
([corridas/comparacion_modelos.md](corridas/comparacion_modelos.md)). Los dos cumplen el
criterio (mismas 12 prioridades, mismos totales). Se elige el liviano: misma calidad medida,
20% del costo. Registrado como iteración 3 en [DECISIONES.md](DECISIONES.md).

## Gobierno y riesgo

**Sistemas, datos y permisos.**

| Sistema/dato | Acceso del agente | Alcance |
|---|---|---|
| CSV exportado del sistema contable | Lectura | Solo el archivo `facturas_semana.csv` del directorio de trabajo |
| Sistema contable | **Ninguno** | El agente nunca se conecta; el export es manual |
| Sistema de pagos / home banking | **Ninguno** | Los pagos los carga una persona |
| Credenciales | `ANTHROPIC_API_KEY` como variable de entorno | No versionada; no aparece en corridas |

Los datos son razón social, CUIT, montos y vencimientos de proveedores: información comercial
sensible pero sin datos personales de individuos. Para este repo público los nombres y CUIT
fueron **reemplazados por valores sintéticos** (decisión registrada en DECISIONES.md, alcance).

**Riesgos priorizados y controles.**

| Riesgo | Causa → consecuencia | Impacto | Control (dónde se ve) |
|---|---|---|---|
| R1: el agente inventa un monto o una fecha | Alucinación ante dato faltante → se paga mal o fuera de término | Alto | Regla "prohibido adivinar" + estado `ABSTENCION_PARCIAL` (system prompt §5); probado en [corrida 5](corridas/corrida_5_caso_limite.md) |
| R2: prioridad mal asignada pasa inadvertida | Regla ambigua → factura crítica paga tarde, corte de suministro | Alto | Revisión humana obligatoria de todas las `alta` + control de totales contra el contable (ver Supervisión); el JSON expone `motivo` por factura para auditar |
| R3: filtración de datos comerciales | Repo público con datos reales | Medio | Datos sintetizados antes de publicar; el CSV real nunca sale de la máquina local |

**Qué pasa cuando sale mal:** si el estado no es `OK` o los totales no cuadran, la corrida se
descarta y se repite con el CSV corregido; no existe camino por el cual una salida del agente
llegue al sistema de pagos sin pasar por las dos personas. **Escalamiento:** ante desacuerdo
entre mi revisión y la salida del agente, decide la jefa de administración con el comprobante
a la vista.

**Responsables:** dueña del sistema y de las corridas: yo (L. Ferreyra). Aprueba y firma los
pagos: jefa de administración. **Trazabilidad:** cada corrida queda archivada en `corridas/`
con entrada, salida cruda, fecha y configuración. **Reversibilidad:** el agente no ejecuta
acciones externas; deshacer una corrida es descartar un archivo.

## Límites conocidos

Ver [DECISIONES.md](DECISIONES.md), sección "Alcance, supuestos y pendientes".
