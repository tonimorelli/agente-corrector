# Corrida del evaluador — caso EXCELENTE — corrida 1b (post-ajuste H1)

- **Motivo:** verificar el efecto del ajuste H1 (versión de herramienta consignada en el
  README del caso). Rúbrica confirmada por el grupo: **V3**.
- **Herramienta:** Claude Code (Windows 11) · operador: Mateo García
- **Modelo:** `claude-fable-5` · temperatura: `NO_DISPONIBLE` · **Fecha:** 2026-09-06
- **System prompt:** `agente/system_prompt.md` de la rama `claude/system-prompt-agente-aollz9` (commit `06a1414`)
- **Rúbrica:** `rubrica.md` V3 (commit `e768ea6`)
- **Repositorio evaluado:** `casos/excelente/` @ commit `82599eb` (rama `mateo/caso-excelente`, post-ajuste H1)
- **Restricciones respetadas:** sin ejecución de código, sin red, solo lectura
- **Resultado:** D3 pasa de 13 a 15 (R2: 2→4); el resto sin cambios de nivel ni de puntos.

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
        localizador: "'Qué hace el sistema'"
        demuestra: "criterio observable de éxito definido"
    faltantes: []
  - id: "S2"
    puntos: 8
    evidencia:
      - tipo: "EV1"
        ruta: "corridas/corrida_1.md"
        localizador: "entrada CSV + salida JSON + verificación"
        demuestra: "ejecución trazable que satisface el criterio de éxito"
      - tipo: "EV1"
        ruta: "corridas/corrida_2.md"
        localizador: "entrada CSV + salida JSON + verificación"
        demuestra: "segunda ejecución independiente que satisface el criterio"
    faltantes: ["reejecución por el evaluador no realizada (prohibida por límites de ejecución)"]
  - id: "S3"
    puntos: 4
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Cómo reproducir', pasos 1-4"
        demuestra: "configuración identificable de la herramienta de lectura de archivos"
      - tipo: "EV1"
        ruta: "corridas/corrida_3.md"
        localizador: "entrada + salida"
        demuestra: "invocación trazable con resultado"
    faltantes: []
  - id: "S4"
    puntos: 4
    evidencia:
      - tipo: "EV1"
        ruta: "corridas/corrida_1.md"
        localizador: "salida JSON + verificación de esquema"
        demuestra: "las 5 corridas cumplen el esquema declarado"
    faltantes: []
  - id: "S5"
    puntos: 4
    evidencia:
      - tipo: "EV1"
        ruta: "corridas/corrida_5_caso_limite.md"
        localizador: "CSV con datos faltantes e inválidos"
        demuestra: "caso límite relevante ejecutado con abstención correcta"
    faltantes: []
  - id: "S6"
    puntos: 5
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Supervisión humana'"
        demuestra: "L2 con disparador, objeto de verificación y rol que firma"
      - tipo: "EV1"
        ruta: "corridas/corrida_5_caso_limite.md"
        localizador: "alertas + estado"
        demuestra: "las corridas no contradicen el circuito"
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 30
nivel: "Excelente"
justificacion: "Sin cambios respecto de la corrida 1: contrato completo, ejecuciones trazables, herramienta registrada, formato validado, caso límite ejecutado y supervisión consistente."
mejora_prioritaria: "Agregar un artefacto de reejecución directa por un tercero (script de validación mecánica)."
---
dimension: "Proceso documentado"
subtotal_antes_de_topes: 25
subcriterios:
  - id: "P1"
    puntos: 5
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/pilotos_v1_v2.md"
        localizador: "pilotos A y B"
        demuestra: "versiones V1 y V2 identificables; V3 vigente con fecha"
    faltantes: []
  - id: "P2"
    puntos: 5
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/pilotos_v1_v2.md"
        localizador: "A1/A2 del 18/8 y piloto B del 20/8"
        demuestra: "dos fallas registradas citando la corrida que las reveló"
    faltantes: []
  - id: "P3"
    puntos: 5
    evidencia:
      - tipo: "EV2"
        ruta: "DECISIONES.md"
        localizador: "iteraciones 1 y 2, campo 'Cambio'"
        demuestra: "dos problemas vinculados a decisiones y cambios inspeccionables"
    faltantes: []
  - id: "P4"
    puntos: 5
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/corrida_4_reproduccion.md"
        localizador: "tabla de comparación"
        demuestra: "antes/después del cambio de formato"
      - tipo: "EV3"
        ruta: "corridas/corrida_5_caso_limite.md"
        localizador: "'Antes/después'"
        demuestra: "antes/después de la regla anti-invención"
    faltantes: []
  - id: "P5"
    puntos: 5
    evidencia:
      - tipo: "EV4"
        ruta: "DECISIONES.md"
        localizador: "'Alcance, supuestos y pendientes'"
        demuestra: "alcance con motivo, supuestos y pendientes diferenciados"
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 25
nivel: "Excelente"
justificacion: "Sin cambios respecto de la corrida 1."
mejora_prioritaria: "Versionar los prompts como archivos separados para diff directo."
---
dimension: "Formato y reproducibilidad"
subtotal_antes_de_topes: 15
subcriterios:
  - id: "R1"
    puntos: 3
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "tabla 'Estructura del repositorio'"
        demuestra: "README enlaza inequívocamente cada componente"
    faltantes: []
  - id: "R2"
    puntos: 4
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Cómo reproducir', paso 1 (post-ajuste H1)"
        demuestra: "herramienta con versión (Claude Code v2.1, Windows 11), sin otras dependencias, variable de entorno sin secretos y preparación de datos: los cuatro elementos del valor 4"
    faltantes: ["la validación del esquema sigue siendo manual (validador online), aunque R2 no la exige"]
  - id: "R3"
    puntos: 4
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/"
        localizador: "corridas 1, 2 y 3"
        demuestra: "tres corridas independientes con todos los campos exigidos"
    faltantes: []
  - id: "R4"
    puntos: 2
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/corrida_1.md"
        localizador: "encabezado"
        demuestra: "modelo identificado y temperatura como NO_DISPONIBLE en todas las corridas"
    faltantes: []
  - id: "R5"
    puntos: 2
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Criterio de reproducción'"
        demuestra: "criterio operacionalizado"
      - tipo: "EV3"
        ruta: "corridas/corrida_4_reproduccion.md"
        localizador: "tabla"
        demuestra: "reproducción comparada contra el criterio"
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 15
nivel: "Excelente"
justificacion: "El faltante de la corrida 1 (versión de la herramienta) está resuelto: R2 alcanza el valor 4 con evidencia explícita de sus cuatro requisitos."
mejora_prioritaria: "Automatizar la validación del esquema para eliminar el paso manual."
---
dimension: "Análisis económico"
subtotal_antes_de_topes: 15
subcriterios:
  - id: "E1"
    puntos: 3
    evidencia:
      - tipo: "EV1"
        ruta: "corridas/corrida_1.md"
        localizador: "'Tokens'"
        demuestra: "unidades por corrida registradas junto a cada ejecución"
    faltantes: []
  - id: "E2"
    puntos: 4
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Análisis económico'"
        demuestra: "fuente fechada, moneda, precios y fórmula que separa componentes"
    faltantes: []
  - id: "E3"
    puntos: 4
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Proyección' y 'Sensibilidad'"
        demuestra: "proyección con fórmula más escenario alternativo"
    faltantes: []
  - id: "E4"
    puntos: 4
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/comparacion_modelos.md"
        localizador: "tabla de resultados"
        demuestra: "comparación controlada con evidencia conservada y elección justificada"
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 15
nivel: "Excelente"
justificacion: "Sin cambios respecto de la corrida 1."
mejora_prioritaria: "Automatizar el registro de tokens."
---
dimension: "Gobierno y riesgo"
subtotal_antes_de_topes: 15
subcriterios:
  - id: "G1"
    puntos: 3
    evidencia:
      - tipo: "EV4"
        ruta: "README.md"
        localizador: "tabla de permisos"
        demuestra: "inventario con alcance y credenciales sin secretos"
      - tipo: "EV2"
        ruta: "corridas/corrida_1.md"
        localizador: "entrada"
        demuestra: "implementación observable coincidente"
    faltantes: []
  - id: "G2"
    puntos: 3
    evidencia:
      - tipo: "EV4"
        ruta: "README.md"
        localizador: "tabla de riesgos"
        demuestra: "tres escenarios con causa, consecuencia e impacto"
    faltantes: []
  - id: "G3"
    puntos: 3
    evidencia:
      - tipo: "EV1"
        ruta: "corridas/corrida_5_caso_limite.md"
        localizador: "estado ABSTENCION_PARCIAL"
        demuestra: "control del riesgo R1 visible en ejecución"
    faltantes: []
  - id: "G4"
    puntos: 3
    evidencia:
      - tipo: "EV2"
        ruta: "README.md"
        localizador: "'Supervisión humana' y 'Qué pasa cuando sale mal'"
        demuestra: "revisión con objeto, disparador, rol y escalamiento proporcional"
    faltantes: []
  - id: "G5"
    puntos: 3
    evidencia:
      - tipo: "EV4"
        ruta: "README.md"
        localizador: "'Responsables'"
        demuestra: "dueña y rol que firma"
      - tipo: "EV3"
        ruta: "corridas/"
        localizador: "corridas 1-5"
        demuestra: "trazabilidad conservada; reversibilidad trivial"
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 15
nivel: "Excelente"
justificacion: "Sin cambios respecto de la corrida 1."
mejora_prioritaria: "Documentar la política de retención de los CSV reales fuera del repo."
---
tipo: "cierre"
puntaje_total: 100
control_aritmetico:
  - dimension: "Sistema completo y funcionando"
    puntaje_final: 30
    maximo: 30
  - dimension: "Proceso documentado"
    puntaje_final: 25
    maximo: 25
  - dimension: "Formato y reproducibilidad"
    puntaje_final: 15
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
