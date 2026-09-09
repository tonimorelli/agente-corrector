# Corrida del evaluador — caso FLOJO — corrida 2 (estabilidad)

- **Objetivo:** verificación de estabilidad (8/9): mismos casos, sin cambios.
- **Herramienta:** Claude Code (Windows 11) · operador: Mateo García
- **Modelo:** `claude-fable-5` · temperatura: `NO_DISPONIBLE` · **Fecha:** 2026-09-08
- **System prompt:** `agente/system_prompt.md` @ `main` (`9c3414d`)
- **Rúbrica:** `rubrica.md` @ `main` (`9c3414d`) — **incluye el ajuste `4552ff2` a G3**,
  posterior a la corrida 1 (ver nota al pie: explica la única diferencia de puntaje)
- **Repositorio evaluado:** `casos/flojo/` @ `main` (`9c3414d`) — contenido idéntico al de la
  corrida 1 (subido por Tomás)
- **Comparación de referencia:** [corrida 1, 23/100](corrida_evaluador_flojo_1.md)

## Salida del agente

```
===EVALUACION_INICIO===
dimension: "Sistema completo y funcionando"
subtotal_antes_de_topes: 8
subcriterios:
  - id: "S1"
    puntos: 3
    evidencia:
      - {tipo: "EV2", ruta: "prompts/system_prompt.md", localizador: "bloque de prompt", demuestra: "rol, tarea y entrada reconstruibles"}
    faltantes: ["límites", "criterio de éxito", "salida declarada (JSON) contradice la pedida (prosa)"]
  - id: "S2"
    puntos: 3
    evidencia:
      - {tipo: "EV3", ruta: "corridas/corrida_2.md", localizador: "entrada + salida + fecha", demuestra: "salida registrada con entrada, sin configuración ('no anoté qué modelo')"}
    faltantes: ["trazabilidad completa", "criterio de éxito contra el cual verificar"]
  - id: "S3"
    puntos: 0
    evidencia: []
    faltantes: ["integración con Google Reviews solo afirmada; DECISIONES admite pegado manual"]
  - id: "S4"
    puntos: 0
    evidencia: []
    faltantes: ["README promete JSON; ambas corridas devuelven prosa"]
  - id: "S5"
    puntos: 0
    evidencia: []
    faltantes: ["sin conducta ante fallas definida ni ejecutada"]
  - id: "S6"
    puntos: 2
    evidencia:
      - {tipo: "EV4", ruta: "README.md", localizador: "'Supervisión y riesgos'", demuestra: "se requiere revisión humana"}
    faltantes: ["objeto", "disparador", "rol responsable"]
contradicciones:
  - "README (JSON, integración con Google) vs. corridas y DECISIONES (prosa, pegado manual): patrones (a) y (b) de §1.2; prevalece EV3."
topes_aplicados: []
puntaje_final: 8
nivel: "Insuficiente"
justificacion: "Idéntico a la corrida 1: contrato parcial, una ejecución sin configuración, integración y formato declarados sin respaldo."
mejora_prioritaria: "Definir esquema de salida real y registrar una corrida con modelo y configuración."
---
dimension: "Proceso documentado"
subtotal_antes_de_topes: 12
subcriterios:
  - id: "P1"
    puntos: 3
    evidencia:
      - {tipo: "EV2", ruta: "prompts/prompt_v1.md", localizador: "archivo completo", demuestra: "dos iteraciones ordenadas vinculadas a artefactos"}
    faltantes: ["tercera iteración distinguible"]
  - id: "P2"
    puntos: 2
    evidencia:
      - {tipo: "EV2", ruta: "prompts/prompt_v1.md", localizador: "prompt en inglés", demuestra: "un problema concreto con artefacto que lo corrobora"}
    faltantes: ["la corrida que reveló el problema no se conservó", "segundo problema con evidencia"]
  - id: "P3"
    puntos: 3
    evidencia:
      - {tipo: "EV2", ruta: "prompts/system_prompt.md", localizador: "cambio v1→v2", demuestra: "una relación completa problema→decisión→cambio"}
    faltantes: ["segunda relación completa"]
  - id: "P4"
    puntos: 2
    evidencia:
      - {tipo: "EV3", ruta: "corridas/corrida_1.md", localizador: "salida en español del 29/8", demuestra: "verificación posterior identificable de un cambio"}
    faltantes: ["comparación antes/después explícita", "verificación de un segundo cambio"]
  - id: "P5"
    puntos: 2
    evidencia:
      - {tipo: "EV4", ruta: "DECISIONES.md", localizador: "'Límites'", demuestra: "límites parciales documentados"}
    faltantes: ["motivo/impacto", "supuestos"]
contradicciones: []
topes_aplicados: []
puntaje_final: 12
nivel: "Básico"
justificacion: "Idéntico a la corrida 1: una iteración real trazable, el resto afirmado sin versiones."
mejora_prioritaria: "Registrar cada iteración con su corrida y su antes/después."
---
dimension: "Formato y reproducibilidad"
subtotal_antes_de_topes: 1
subcriterios:
  - id: "R1"
    puntos: 1
    evidencia:
      - {tipo: "EV2", ruta: ".", localizador: "estructura de carpetas", demuestra: "componentes existentes sin mapeo desde el README"}
    faltantes: ["enlace inequívoco a cada componente"]
  - id: "R2"
    puntos: 0
    evidencia: []
    faltantes: ["sin pasos de reproducción ni herramienta/versión reconstruible"]
  - id: "R3"
    puntos: 0
    evidencia: []
    faltantes: ["corrida_1 sin entrada; corrida_2 sin configuración: menos de dos reconstruibles"]
  - id: "R4"
    puntos: 0
    evidencia: []
    faltantes: ["'no anoté qué modelo'"]
  - id: "R5"
    puntos: 0
    evidencia: []
    faltantes: ["sin criterio de reproducción"]
contradicciones: []
topes_aplicados:
  - "R3=0 → máximo 4/15"
  - "R2=0 → máximo 6/15"
puntaje_final: 1
nivel: "Insuficiente"
justificacion: "Idéntico a la corrida 1."
mejora_prioritaria: "Guardar entrada, salida, fecha y modelo de cada corrida."
---
dimension: "Análisis económico"
subtotal_antes_de_topes: 0
subcriterios:
  - id: "E1"
    puntos: 0
    evidencia: []
    faltantes: ["sin medición ni método"]
  - id: "E2"
    puntos: 0
    evidencia: []
    faltantes: ["solo un costo declarado (USD 20/mes) sin fuente ni fórmula"]
  - id: "E3"
    puntos: 0
    evidencia: []
    faltantes: ["sin proyección"]
  - id: "E4"
    puntos: 0
    evidencia: []
    faltantes: ["sin comparación de opciones"]
contradicciones: []
topes_aplicados:
  - "E2=0 → máximo 4/15"
puntaje_final: 0
nivel: "Ausente"
justificacion: "Idéntico a la corrida 1."
mejora_prioritaria: "Medir tokens de una corrida real y construir el cálculo unitario."
---
dimension: "Gobierno y riesgo"
subtotal_antes_de_topes: 3
subcriterios:
  - id: "G1"
    puntos: 1
    evidencia:
      - {tipo: "EV4", ruta: "README.md", localizador: "'Cómo funciona' y 'Tecnología'", demuestra: "inventario parcial de fuentes de datos, genérico"}
    faltantes: ["permisos, alcance y credenciales"]
  - id: "G2"
    puntos: 0
    evidencia: []
    faltantes: ["'como toda IA puede equivocarse' no es un escenario con causa/consecuencia/impacto"]
  - id: "G3"
    puntos: 1
    evidencia:
      - {tipo: "EV4", ruta: "README.md", localizador: "'siempre revisamos los informes antes de usarlos'", demuestra: "mitigación documentada sin comprobar — por regla 4552ff2, EV4 sola alcanza máximo 1"}
    faltantes: ["control visible en prompt, configuración o corridas", "respuesta para riesgos prioritarios"]
  - id: "G4"
    puntos: 1
    evidencia:
      - {tipo: "EV4", ruta: "README.md", localizador: "'Supervisión y riesgos'", demuestra: "mención de revisión humana"}
    faltantes: ["objeto, disparador, rol y escalamiento"]
  - id: "G5"
    puntos: 0
    evidencia: []
    faltantes: ["sin responsable ni trazabilidad"]
contradicciones: []
topes_aplicados: []
puntaje_final: 3
nivel: "Insuficiente"
justificacion: "Única diferencia con la corrida 1: G3 pasa de 0 a 1 por el ajuste 4552ff2 de la rúbrica (mitigación documentada sin comprobar), no por variación del agente."
mejora_prioritaria: "Comprobar al menos una mitigación en prompt, configuración o corrida."
---
tipo: "cierre"
puntaje_total: 24
control_aritmetico:
  - {dimension: "Sistema completo y funcionando", puntaje_final: 8, maximo: 30}
  - {dimension: "Proceso documentado", puntaje_final: 12, maximo: 25}
  - {dimension: "Formato y reproducibilidad", puntaje_final: 1, maximo: 15}
  - {dimension: "Análisis económico", puntaje_final: 0, maximo: 15}
  - {dimension: "Gobierno y riesgo", puntaje_final: 3, maximo: 15}
banderas_transversales:
  - "Capacidades declaradas sin EV1-EV3 compatible no premiadas (§7)"
observaciones_de_seguridad: []
===EVALUACION_FIN===
```

## Comparación contra la corrida 1

| Dimensión | Corrida 1 | Corrida 2 | ¿Mismo nivel? |
|---|---:|---:|---|
| Sistema completo | 8 | 8 | ✅ Insuficiente |
| Proceso | 12 | 12 | ✅ Básico |
| Formato y reproducibilidad | 1 | 1 | ✅ Insuficiente |
| Análisis económico | 0 | 0 | ✅ Ausente |
| Gobierno y riesgo | 2 | 3 | ✅ Insuficiente (ver nota) |
| **Total** | **23** | **24** | ✅ |

**Nota — la única diferencia es de rúbrica, no del agente:** entre las corridas 1 y 2 se
modificó G3 (`4552ff2`, mergeado con el PR #3): una mitigación documentada sin comprobar
(EV4 sola) ahora alcanza 1 en vez de 0. El caso flojo tiene exactamente eso ("siempre
revisamos los informes"). Con la rúbrica congelada, ambas corridas puntúan idéntico; el
nivel de la dimensión no cambia (Insuficiente). **Estable.**
