# Corrida del evaluador — caso EXCELENTE — corrida 2 (estabilidad)

- **Objetivo:** verificación de estabilidad pedida por el grupo (8/9): re-correr el agente
  sobre los mismos casos, sin cambios, y comprobar que mantiene notas y criterios.
- **Herramienta:** Claude Code (Windows 11) · operador: Mateo García
- **Modelo:** `claude-fable-5` · temperatura: `NO_DISPONIBLE` · **Fecha:** 2026-09-08
- **System prompt:** `agente/system_prompt.md` @ `main` (`9c3414d`)
- **Rúbrica:** `rubrica.md` @ `main` (`9c3414d`) — incluye el ajuste `4552ff2` (G3), posterior
  a las corridas 1
- **Repositorio evaluado:** `casos/excelente/` @ `main` (`9c3414d`) — contenido idéntico al de
  la corrida 1b
- **Comparación de referencia:** [corrida 1b, 100/100](corrida_evaluador_excelente_1b_postajuste.md)

## Salida del agente

```
===EVALUACION_INICIO===
dimension: "Sistema completo y funcionando"
subtotal_antes_de_topes: 30
subcriterios:
  - id: "S1"
    puntos: 5
    evidencia:
      - {tipo: "EV2", ruta: "prompts/system_prompt.md", localizador: "§1-§6", demuestra: "contrato completo sin contradicción; criterio de éxito en README"}
    faltantes: []
  - id: "S2"
    puntos: 8
    evidencia:
      - {tipo: "EV1", ruta: "corridas/corrida_1.md", localizador: "entrada+salida+verificación", demuestra: "ejecución trazable que cumple el criterio"}
      - {tipo: "EV1", ruta: "corridas/corrida_2.md", localizador: "entrada+salida+verificación", demuestra: "segunda ejecución independiente que cumple el criterio"}
    faltantes: ["reejecución por el evaluador vedada por límites de ejecución"]
  - id: "S3"
    puntos: 4
    evidencia:
      - {tipo: "EV1", ruta: "corridas/corrida_3.md", localizador: "entrada+salida", demuestra: "invocación trazable de la lectura de archivo; configuración en README pasos 1-4"}
    faltantes: []
  - id: "S4"
    puntos: 4
    evidencia:
      - {tipo: "EV1", ruta: "corridas/corrida_1.md", localizador: "salida JSON + verificación", demuestra: "las 5 corridas cumplen el esquema declarado"}
    faltantes: []
  - id: "S5"
    puntos: 4
    evidencia:
      - {tipo: "EV1", ruta: "corridas/corrida_5_caso_limite.md", localizador: "CSV defectuoso → ABSTENCION_PARCIAL", demuestra: "caso límite relevante ejecutado con abstención correcta"}
    faltantes: []
  - id: "S6"
    puntos: 5
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "'Supervisión humana'", demuestra: "L2 con disparador, objeto y rol que firma; corridas consistentes"}
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 30
nivel: "Excelente"
justificacion: "Mismos hallazgos que la corrida 1b; sin variación de puntos ni de nivel."
mejora_prioritaria: "Artefacto de reejecución directa por un tercero (script de validación)."
---
dimension: "Proceso documentado"
subtotal_antes_de_topes: 25
subcriterios:
  - id: "P1"
    puntos: 5
    evidencia:
      - {tipo: "EV3", ruta: "corridas/pilotos_v1_v2.md", localizador: "pilotos A y B", demuestra: "tres versiones identificables (V1, V2, V3 fechada)"}
    faltantes: []
  - id: "P2"
    puntos: 5
    evidencia:
      - {tipo: "EV3", ruta: "corridas/pilotos_v1_v2.md", localizador: "A1/A2 18/8; piloto B 20/8", demuestra: "dos fallas citando la corrida que las reveló"}
    faltantes: []
  - id: "P3"
    puntos: 5
    evidencia:
      - {tipo: "EV2", ruta: "DECISIONES.md", localizador: "iteraciones 1-2, 'Cambio'", demuestra: "dos relaciones problema→decisión→cambio inspeccionable"}
    faltantes: []
  - id: "P4"
    puntos: 5
    evidencia:
      - {tipo: "EV3", ruta: "corridas/corrida_4_reproduccion.md", localizador: "tabla", demuestra: "antes/después del formato"}
      - {tipo: "EV3", ruta: "corridas/corrida_5_caso_limite.md", localizador: "'Antes/después'", demuestra: "antes/después de la regla anti-invención"}
    faltantes: []
  - id: "P5"
    puntos: 5
    evidencia:
      - {tipo: "EV4", ruta: "DECISIONES.md", localizador: "'Alcance, supuestos y pendientes'", demuestra: "alcance con motivo, supuestos y pendientes"}
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 25
nivel: "Excelente"
justificacion: "Sin variación respecto de la corrida 1b."
mejora_prioritaria: "Prompts versionados como archivos separados."
---
dimension: "Formato y reproducibilidad"
subtotal_antes_de_topes: 15
subcriterios:
  - id: "R1"
    puntos: 3
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "tabla de estructura", demuestra: "cada componente enlazado inequívocamente"}
    faltantes: []
  - id: "R2"
    puntos: 4
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "'Cómo reproducir', paso 1", demuestra: "herramienta con versión, sin otras dependencias, variable de entorno, preparación de datos"}
    faltantes: []
  - id: "R3"
    puntos: 4
    evidencia:
      - {tipo: "EV3", ruta: "corridas/", localizador: "corridas 1-3", demuestra: "tres corridas independientes con todos los campos"}
    faltantes: []
  - id: "R4"
    puntos: 2
    evidencia:
      - {tipo: "EV3", ruta: "corridas/corrida_1.md", localizador: "encabezado", demuestra: "modelo y NO_DISPONIBLE registrados en todas"}
    faltantes: []
  - id: "R5"
    puntos: 2
    evidencia:
      - {tipo: "EV3", ruta: "corridas/corrida_4_reproduccion.md", localizador: "tabla", demuestra: "reproducción comparada contra el criterio del README"}
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 15
nivel: "Excelente"
justificacion: "Sin variación respecto de la corrida 1b."
mejora_prioritaria: "Automatizar la validación del esquema."
---
dimension: "Análisis económico"
subtotal_antes_de_topes: 15
subcriterios:
  - id: "E1"
    puntos: 3
    evidencia:
      - {tipo: "EV1", ruta: "corridas/corrida_1.md", localizador: "'Tokens'", demuestra: "unidades por corrida junto a cada ejecución"}
    faltantes: []
  - id: "E2"
    puntos: 4
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "'Análisis económico'", demuestra: "fuente fechada, moneda, precios, fórmula por componente"}
    faltantes: []
  - id: "E3"
    puntos: 4
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "'Proyección' y 'Sensibilidad'", demuestra: "proyección con fórmula y escenario alternativo"}
    faltantes: []
  - id: "E4"
    puntos: 4
    evidencia:
      - {tipo: "EV3", ruta: "corridas/comparacion_modelos.md", localizador: "tabla", demuestra: "comparación controlada con evidencia conservada"}
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 15
nivel: "Excelente"
justificacion: "Sin variación respecto de la corrida 1b."
mejora_prioritaria: "Registro automático de tokens."
---
dimension: "Gobierno y riesgo"
subtotal_antes_de_topes: 15
subcriterios:
  - id: "G1"
    puntos: 3
    evidencia:
      - {tipo: "EV4", ruta: "README.md", localizador: "tabla de permisos", demuestra: "inventario con alcance; coincide con la implementación observable (EV2 en corridas)"}
    faltantes: []
  - id: "G2"
    puntos: 3
    evidencia:
      - {tipo: "EV4", ruta: "README.md", localizador: "tabla de riesgos", demuestra: "tres escenarios con causa, consecuencia e impacto"}
    faltantes: []
  - id: "G3"
    puntos: 3
    evidencia:
      - {tipo: "EV1", ruta: "corridas/corrida_5_caso_limite.md", localizador: "ABSTENCION_PARCIAL", demuestra: "control del riesgo R1 visible en ejecución (el ajuste 4552ff2 no afecta: hay EV1)"}
    faltantes: []
  - id: "G4"
    puntos: 3
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "'Supervisión' y 'Qué pasa cuando sale mal'", demuestra: "objeto, disparador, rol y escalamiento proporcional"}
    faltantes: []
  - id: "G5"
    puntos: 3
    evidencia:
      - {tipo: "EV4", ruta: "README.md", localizador: "'Responsables'", demuestra: "dueña y rol que firma; trazabilidad EV3 en corridas/"}
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 15
nivel: "Excelente"
justificacion: "Sin variación respecto de la corrida 1b; el ajuste de G3 no aplica porque el control está probado con EV1."
mejora_prioritaria: "Política de retención de los CSV reales fuera del repo."
---
tipo: "cierre"
puntaje_total: 100
control_aritmetico:
  - {dimension: "Sistema completo y funcionando", puntaje_final: 30, maximo: 30}
  - {dimension: "Proceso documentado", puntaje_final: 25, maximo: 25}
  - {dimension: "Formato y reproducibilidad", puntaje_final: 15, maximo: 15}
  - {dimension: "Análisis económico", puntaje_final: 15, maximo: 15}
  - {dimension: "Gobierno y riesgo", puntaje_final: 15, maximo: 15}
banderas_transversales: []
observaciones_de_seguridad: []
===EVALUACION_FIN===
```

## Comparación contra la corrida 1b

| Dimensión | Corrida 1b | Corrida 2 | ¿Mismo nivel? |
|---|---:|---:|---|
| Sistema completo | 30 | 30 | ✅ Excelente |
| Proceso | 25 | 25 | ✅ Excelente |
| Formato y reproducibilidad | 15 | 15 | ✅ Excelente |
| Análisis económico | 15 | 15 | ✅ Excelente |
| Gobierno y riesgo | 15 | 15 | ✅ Excelente |
| **Total** | **100** | **100** | ✅ |

**Estable**: mismos puntos por subcriterio y mismo nivel por dimensión; varía solo la
redacción de justificaciones (admitido por el criterio de estabilidad del método).
