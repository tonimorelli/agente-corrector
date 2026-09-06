# Corrida del evaluador — caso EXCELENTE — corrida 1

- **Herramienta:** Claude Code (Windows 11) · operador: Mateo García
- **Modelo:** `claude-fable-5` · temperatura: `NO_DISPONIBLE`
- **Fecha:** 2026-09-06
- **System prompt:** `agente/system_prompt.md` de la rama `claude/system-prompt-agente-aollz9` (commit `06a1414`)
- **Rúbrica:** `rubrica.md` V3 de la rama `claude/rubrica-tipificar-evidencia-pa18h0` (commit `e768ea6`)
- **Repositorio evaluado:** `casos/excelente/` @ commit `a11ce86`
- **Restricciones respetadas:** sin ejecución de código, sin red, solo lectura

## Salida del agente

```
===EVALUACION_INICIO===
dimension: "Sistema completo y funcionando"
subtotal_antes_de_topes: 30
subcriterios:
  - id: "S1"
    puntos: 5
    evidencia:
      - tipo: "EV2"
        ruta: "prompts/system_prompt.md"
        localizador: "§1-§6"
        demuestra: "rol, contexto, tarea, formato, restricciones y ejemplos sin contradicción"
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "sección 'Qué hace el sistema'"
        demuestra: "criterio observable de éxito definido (validación de esquema, totales exactos, cero valores inventados)"
    faltantes: []
  - id: "S2"
    puntos: 8
    evidencia:
      - tipo: "EV1"
        ruta: "corridas/corrida_1.md"
        localizador: "entrada CSV completa + salida JSON + verificación"
        demuestra: "ejecución trazable que satisface el criterio de éxito (12/12, total 15.810.400 verificado)"
      - tipo: "EV1"
        ruta: "corridas/corrida_2.md"
        localizador: "entrada CSV completa + salida JSON + verificación"
        demuestra: "segunda ejecución independiente que satisface el criterio (9/9, total 11.573.200)"
    faltantes: ["reejecución por el evaluador no realizada (prohibida por límites de ejecución); se puntúa con el registro completo entrada→salida→config"]
  - id: "S3"
    puntos: 4
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Cómo reproducir', pasos 1-4"
        demuestra: "configuración identificable de la herramienta de lectura de archivos (facturas_semana.csv)"
      - tipo: "EV1"
        ruta: "corridas/corrida_3.md"
        localizador: "entrada + salida"
        demuestra: "invocación trazable de la lectura del archivo con resultado"
    faltantes: []
  - id: "S4"
    puntos: 4
    evidencia:
      - tipo: "EV1"
        ruta: "corridas/corrida_1.md"
        localizador: "salida JSON + verificación 'JSON valida contra el esquema'"
        demuestra: "las 5 corridas cumplen el esquema declarado en prompts/system_prompt.md §4"
    faltantes: []
  - id: "S5"
    puntos: 4
    evidencia:
      - tipo: "EV1"
        ruta: "corridas/corrida_5_caso_limite.md"
        localizador: "CSV con FC-0830 sin monto y FC-0831 con fecha inválida"
        demuestra: "caso límite relevante ejecutado: el sistema se abstiene (ABSTENCION_PARCIAL) sin inventar éxito, según riesgo R1 de G2"
    faltantes: []
  - id: "S6"
    puntos: 5
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "sección 'Supervisión humana'"
        demuestra: "define qué hace solo, disparador de revisión, objeto de verificación y rol que firma (L2)"
      - tipo: "EV1"
        ruta: "corridas/corrida_5_caso_limite.md"
        localizador: "alertas + estado"
        demuestra: "las corridas no contradicen el circuito: el estado degradado dispara la revisión"
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 30
nivel: "Excelente"
justificacion: "Contrato completo, dos o más ejecuciones trazables que cumplen el criterio de éxito, herramienta con invocación registrada, formato validado, caso límite ejecutado y supervisión definida y consistente."
mejora_prioritaria: "Agregar un artefacto que permita reejecución directa por un tercero (script o instrucción de validación mecánica del esquema)."
---
dimension: "Proceso documentado"
subtotal_antes_de_topes: 25
subcriterios:
  - id: "P1"
    puntos: 5
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/pilotos_v1_v2.md"
        localizador: "piloto A (V1) y piloto B (V2)"
        demuestra: "versiones V1 y V2 con registros identificables"
      - tipo: "EV2"
        ruta: "prompts/system_prompt.md"
        localizador: "encabezado 'Versión 3 — 21/8/2026'"
        demuestra: "tercera versión identificable; tres iteraciones ordenadas en DECISIONES.md"
    faltantes: []
  - id: "P2"
    puntos: 5
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/pilotos_v1_v2.md"
        localizador: "ejecuciones A1/A2 del 18/8 y piloto B del 20/8"
        demuestra: "dos iteraciones registran la falla citando la corrida que la reveló (inconsistencia estructural; monto inventado)"
    faltantes: []
  - id: "P3"
    puntos: 5
    evidencia:
      - tipo: "EV2"
        ruta: "DECISIONES.md"
        localizador: "iteraciones 1 y 2, campo 'Cambio'"
        demuestra: "dos problemas vinculados explícitamente a decisiones y a cambios inspeccionables en el prompt (§4 y §5)"
    faltantes: []
  - id: "P4"
    puntos: 5
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/corrida_4_reproduccion.md"
        localizador: "tabla de comparación"
        demuestra: "antes/después del cambio de formato: de pilotos inconsistentes a 12/12 prioridades idénticas"
      - tipo: "EV3"
        ruta: "corridas/corrida_5_caso_limite.md"
        localizador: "sección 'Antes/después'"
        demuestra: "antes/después de la regla anti-invención: piloto B inventaba, V3 se abstiene"
    faltantes: []
  - id: "P5"
    puntos: 5
    evidencia:
      - tipo: "EV4"
        ruta: "DECISIONES.md"
        localizador: "sección 'Alcance, supuestos y pendientes'"
        demuestra: "alcance con motivo e impacto, supuestos vigentes y pendientes diferenciados"
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 25
nivel: "Excelente"
justificacion: "Tres iteraciones ordenadas con artefactos, fallas citando la corrida que las reveló, decisiones ligadas a cambios inspeccionables, dos verificaciones antes/después y límites documentados."
mejora_prioritaria: "Versionar los prompts como archivos separados (v1, v2, v3) para que el diff entre versiones sea directamente inspeccionable."
---
dimension: "Formato y reproducibilidad"
subtotal_antes_de_topes: 13
subcriterios:
  - id: "R1"
    puntos: 3
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "tabla 'Estructura del repositorio'"
        demuestra: "README enlaza inequívocamente cada componente exigido"
    faltantes: []
  - id: "R2"
    puntos: 2
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Cómo reproducir una corrida', pasos 1-6"
        demuestra: "pasos ejecutables, variable de entorno sin secreto y preparación de datos"
    faltantes: ["no se consigna la versión de la herramienta (Claude Code) usada en las corridas; la rúbrica exige dependencias/versiones para el valor 4"]
  - id: "R3"
    puntos: 4
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/"
        localizador: "corridas 1, 2 y 3"
        demuestra: "tres corridas independientes con id, fecha, entrada completa, salida cruda y estado"
    faltantes: []
  - id: "R4"
    puntos: 2
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/corrida_1.md"
        localizador: "encabezado"
        demuestra: "modelo identificado y temperatura registrada como NO_DISPONIBLE en todas las corridas"
    faltantes: []
  - id: "R5"
    puntos: 2
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Criterio de reproducción'"
        demuestra: "criterio operacionalizado (campos y tolerancia)"
      - tipo: "EV3"
        ruta: "corridas/corrida_4_reproduccion.md"
        localizador: "tabla de comparación"
        demuestra: "una reproducción comparada contra ese criterio (12/12)"
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 13
nivel: "Bueno"
justificacion: "Estructura navegable, tres corridas reconstruibles, configuración registrada y criterio de reproducción aplicado; el valor máximo de R2 exige versiones de dependencias que no están consignadas."
mejora_prioritaria: "Consignar en el README la versión de la herramienta usada (R2) para alcanzar el valor 4."
---
dimension: "Análisis económico"
subtotal_antes_de_topes: 15
subcriterios:
  - id: "E1"
    puntos: 3
    evidencia:
      - tipo: "EV1"
        ruta: "corridas/corrida_1.md"
        localizador: "encabezado 'Tokens'"
        demuestra: "unidades consumidas por corrida reportadas por la plataforma y registradas junto a cada ejecución"
    faltantes: []
  - id: "E2"
    puntos: 4
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Análisis económico'"
        demuestra: "fuente y fecha (Anthropic, 2/9/2026), moneda, precios por unidad y fórmula que separa entrada y salida"
    faltantes: []
  - id: "E3"
    puntos: 4
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Proyección año base' y 'Sensibilidad'"
        demuestra: "proyección con fórmula y supuestos más un escenario alternativo de volumen"
    faltantes: []
  - id: "E4"
    puntos: 4
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/comparacion_modelos.md"
        localizador: "tabla de resultados"
        demuestra: "dos modelos comparados con la misma entrada y el mismo criterio, resultados conservados y elección justificada por costo y calidad"
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 15
nivel: "Excelente"
justificacion: "Medición por corrida, cálculo unitario con fuente fechada, proyección con sensibilidad y comparación controlada de modelos con evidencia conservada."
mejora_prioritaria: "Automatizar el registro de tokens para eliminar la transcripción manual del dato."
---
dimension: "Gobierno y riesgo"
subtotal_antes_de_topes: 15
subcriterios:
  - id: "G1"
    puntos: 3
    evidencia:
      - tipo: "EV4"
        ruta: "README.md"
        localizador: "tabla 'Sistemas, datos y permisos'"
        demuestra: "inventario con lectura/escritura, alcance mínimo y mecanismo de credenciales sin secretos"
      - tipo: "EV2"
        ruta: "corridas/corrida_1.md"
        localizador: "entrada"
        demuestra: "la implementación observable (solo lectura de un CSV) coincide con el inventario"
    faltantes: []
  - id: "G2"
    puntos: 3
    evidencia:
      - tipo: "EV4"
        ruta: "README.md"
        localizador: "tabla 'Riesgos priorizados y controles'"
        demuestra: "tres escenarios con causa, consecuencia e impacto, incluida la privacidad (R3)"
    faltantes: []
  - id: "G3"
    puntos: 3
    evidencia:
      - tipo: "EV1"
        ruta: "corridas/corrida_5_caso_limite.md"
        localizador: "salida con estado ABSTENCION_PARCIAL"
        demuestra: "el control del riesgo R1 es visible en ejecución; los demás riesgos tienen prevención y respuesta definidas"
    faltantes: []
  - id: "G4"
    puntos: 3
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Supervisión humana' y 'Qué pasa cuando sale mal'"
        demuestra: "objeto de revisión, disparador, rol que aprueba y escalamiento ante desacuerdo, proporcional al impacto (sin acciones externas del agente)"
    faltantes: []
  - id: "G5"
    puntos: 3
    evidencia:
      - tipo: "EV4"
        ruta: "README.md"
        localizador: "'Responsables'"
        demuestra: "dueña del sistema y rol que firma asignados"
      - tipo: "EV3"
        ruta: "corridas/"
        localizador: "corridas 1-5"
        demuestra: "trazabilidad conservada; reversibilidad trivial por ausencia de acciones externas"
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 15
nivel: "Excelente"
justificacion: "Inventario consistente con la implementación, riesgos priorizados con controles visibles en ejecución, supervisión proporcional y responsabilidad asignada con trazabilidad."
mejora_prioritaria: "Documentar la política de retención de los CSV reales fuera del repo (dónde viven, quién accede)."
---
tipo: "cierre"
puntaje_total: 98
control_aritmetico:
  - dimension: "Sistema completo y funcionando"
    puntaje_final: 30
    maximo: 30
  - dimension: "Proceso documentado"
    puntaje_final: 25
    maximo: 25
  - dimension: "Formato y reproducibilidad"
    puntaje_final: 13
    maximo: 15
  - dimension: "Análisis económico"
    puntaje_final: 15
    maximo: 15
  - dimension: "Gobierno y riesgo"
    puntaje_final: 15
    maximo: 15
banderas_transversales: []
observaciones_de_seguridad: []
===EVALUACION_FIN===
```
