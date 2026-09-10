# Ensayo de la prueba de fuego — repo externo real: `mateogp997/eventos-redline`

- **Objetivo:** último pendiente de la calibración — correr el evaluador sobre un repositorio
  **externo real que nunca vio**, con estructura propia (frontend, datos, corridas con otra
  convención de nombres), antes de la prueba de fuego en vivo del jueves 10/9.
- **Repositorio evaluado:** `github.com/mateogp997/eventos-redline` @ commit `02848e9`
  ("Cotizador de eventos — Redline Racing", trabajo final individual de Mateo García).
- **Conflicto de interés, declarado:** el operador de esta corrida es el autor del trabajo
  evaluado. Por eso esto es un **ensayo de funcionamiento sobre estructura externa** y no una
  calibración de notas: el número es informativo; lo que se valida es que el evaluador corra
  bien sobre un repo ajeno a los casos. Invitamos a cualquier integrante a replicar la corrida.
- **Herramienta:** Claude Code (Windows 11) · operador: Mateo García
- **Modelo:** `claude-fable-5` · temperatura: `NO_DISPONIBLE` · **Fecha:** 2026-09-09
- **System prompt:** `agente/system_prompt.md` @ `main` (`0dce76f`) · **Rúbrica:** `rubrica.md`
  @ `main` (`0dce76f`)
- **Restricciones respetadas:** sin ejecución de código (no se corrió `index.html` ni ningún
  server), sin red, solo lectura del repositorio.

## Salida del agente

```
===EVALUACION_INICIO===
dimension: "Sistema completo y funcionando"
subtotal_antes_de_topes: 30
subcriterios:
  - id: "S1"
    puntos: 5
    evidencia:
      - {tipo: "EV2", ruta: "prompts/system_prompt.md", localizador: "v4.3, §1-§6", demuestra: "rol, contexto, tarea con precedencia de modos, restricciones, formato JSON y ejemplos; criterio observable de éxito en README"}
    faltantes: []
  - id: "S2"
    puntos: 8
    evidencia:
      - {tipo: "EV1", ruta: "corridas/corrida_v4_guido_reproducciones.md", localizador: "R4 y R5 (v4.3)", demuestra: "ejecuciones trazables con entrada íntegra, config completa, tokens y 8/8 checks que cumplen el criterio"}
      - {tipo: "EV1", ruta: "corridas/corrida_v4_alejandro.md", localizador: "entrada+salida+checks", demuestra: "segunda entrada representativa (modo acordado) que cumple el criterio"}
    faltantes: ["las corridas de Selene y Alejandro usan el contrato v4.1; los cambios v4.2/v4.3 (bebida no mencionada, sesiones partidas) no tocan sus caminos (paquete/acordado sin esos elementos), pero una re-corrida con v4.3 lo dejaría verificado en vez de argumentado"]
  - id: "S3"
    puntos: 4
    evidencia:
      - {tipo: "EV1", ruta: "corridas/corrida_v4_guido.md", localizador: "encabezado + tokens", demuestra: "invocación real a la API (herramienta externa) con configuración identificable: modelo, temperatura 0, max_tokens, responseMimeType"}
      - {tipo: "EV2", ruta: "datos/precios.json", localizador: "campo version", demuestra: "segunda integración (datos versionados) con eco verificable en precios_version de cada salida"}
    faltantes: []
  - id: "S4"
    puntos: 4
    evidencia:
      - {tipo: "EV1", ruta: "corridas/corrida_v4_selene.md", localizador: "'8/8 checks automáticos en verde'", demuestra: "todas las corridas evaluables cumplen el formato del contrato §5 y pasan la validación mecánica del frontend"}
    faltantes: ["la validación es estructural y aritmética; un JSON Schema formal está declarado como pendiente"]
  - id: "S5"
    puntos: 4
    evidencia:
      - {tipo: "EV1", ruta: "corridas/corrida_v4_caso_limite.md", localizador: "hilo sin datos → estado incompleto, montos 0", demuestra: "caso límite relevante ejecutado: se abstiene, lista los 4 datos faltantes y no inventa nada"}
    faltantes: []
  - id: "S6"
    puntos: 5
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "'Supervisión humana'", demuestra: "L2 con disparador (toda corrida), objeto de verificación, y quién firma; el agente no envía, no reserva, no cobra"}
      - {tipo: "EV1", ruta: "corridas/corrida_v4_alejandro.md", localizador: "alerta de acordado vs lista", demuestra: "las corridas producen los disparadores de revisión previstos"}
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 30
nivel: "Excelente"
justificacion: "Contrato completo, ejecuciones reales trazables vía API con criterio de éxito cumplido, dos integraciones verificables, formato validado mecánicamente, caso límite ejecutado y supervisión definida y consistente con las corridas."
mejora_prioritaria: "Re-correr Selene y Alejandro con el contrato v4.3 vigente para cerrar el faltante de S2 por verificación directa."
---
dimension: "Proceso documentado"
subtotal_antes_de_topes: 25
subcriterios:
  - id: "P1"
    puntos: 5
    evidencia:
      - {tipo: "EV2", ruta: "prompts/", localizador: "system_prompt_v1/v2/v3_final + v4.3 vigente", demuestra: "cuatro versiones del contrato conservadas como artefactos; iteraciones fechadas en DECISIONES.md"}
    faltantes: []
  - id: "P2"
    puntos: 5
    evidencia:
      - {tipo: "EV3", ruta: "corridas/corrida_1_cumple13_output_v1.json", localizador: "citado en DECISIONES iter. 1", demuestra: "falla de atribución de voces con la corrida que la reveló"}
      - {tipo: "EV3", ruta: "corridas/corrida_v4_guido_reproducciones.md", localizador: "R1 y R3", demuestra: "dos fallas más (bebida no pedida; sesión de 120) con sus corridas"}
    faltantes: []
  - id: "P3"
    puntos: 5
    evidencia:
      - {tipo: "EV2", ruta: "DECISIONES.md", localizador: "iteraciones 1-3b, campos Decisión/Cambio", demuestra: "cada problema vinculado a una decisión y a un cambio inspeccionable de contrato (v1→v2→v3→v4→v4.3)"}
    faltantes: []
  - id: "P4"
    puntos: 5
    evidencia:
      - {tipo: "EV3", ruta: "corridas/corrida_v4_guido_reproducciones.md", localizador: "tabla R1-R5", demuestra: "antes/después de dos cambios de contrato con corridas comparadas (R1 falla → R4/R5 reproducen 2/2)"}
      - {tipo: "EV3", ruta: "corridas/corrida_v4_alejandro.md", localizador: "'Con v3 este caso cotizaba $268.560'", demuestra: "antes/después del modo acordado contra la corrida v3 conservada"}
    faltantes: []
  - id: "P5"
    puntos: 5
    evidencia:
      - {tipo: "EV4", ruta: "DECISIONES.md", localizador: "'Alcance, supuestos y pendientes'", demuestra: "alcance con motivo (no responde al cliente, sin credenciales de WhatsApp), supuestos y pendientes diferenciados"}
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 25
nivel: "Excelente"
justificacion: "La historia es reconstruible de punta a punta con versiones conservadas, fallas citando corridas, cambios inspeccionables y verificaciones antes/después; la cronología observable es consistente con la narrativa."
mejora_prioritaria: "Enlazar desde cada iteración de DECISIONES los diffs de contrato (v2→v3, v3→v4) para inspección directa."
---
dimension: "Formato y reproducibilidad"
subtotal_antes_de_topes: 15
subcriterios:
  - id: "R1"
    puntos: 3
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "tabla 'Estructura del repositorio'", demuestra: "cada componente exigido enlazado inequívocamente, incluidas las corridas históricas"}
    faltantes: []
  - id: "R2"
    puntos: 4
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "'Cómo correr una cotización'", demuestra: "pasos ejecutables, dependencias con versión (pdf-lib 1.17.1, fontkit 1.1.1, Chrome 130+), API key como dato no versionado y preparación del hilo"}
    faltantes: []
  - id: "R3"
    puntos: 4
    evidencia:
      - {tipo: "EV3", ruta: "corridas/", localizador: "corrida_v4_guido/selene/alejandro/caso_limite", demuestra: "cuatro corridas independientes con fecha, entrada íntegra, salida cruda, estado y tokens"}
    faltantes: []
  - id: "R4"
    puntos: 2
    evidencia:
      - {tipo: "EV3", ruta: "corridas/corrida_v4_guido.md", localizador: "encabezado", demuestra: "cada corrida registra modelo, temperatura 0, max_tokens, responseMimeType y versión de precios"}
    faltantes: []
  - id: "R5"
    puntos: 2
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "'Criterio de reproducción'", demuestra: "criterio operacionalizado (modo, total, estado, faltantes)"}
      - {tipo: "EV3", ruta: "corridas/corrida_v4_guido_reproducciones.md", localizador: "R4 vs R5", demuestra: "reproducción comparada contra ese criterio: 2/2 con desglose idéntico"}
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 15
nivel: "Excelente"
justificacion: "Estructura navegable con equivalencias mapeadas, instrucciones con versiones, corridas reconstruibles con configuración completa y reproducción comparada contra un criterio explícito."
mejora_prioritaria: "Formalizar el esquema JSON de salida para que la validación de formato sea contra esquema y no solo contra los checks del frontend."
---
dimension: "Análisis económico"
subtotal_antes_de_topes: 15
subcriterios:
  - id: "E1"
    puntos: 3
    evidencia:
      - {tipo: "EV1", ruta: "corridas/corrida_v4_guido.md", localizador: "campo Tokens", demuestra: "unidades de entrada/salida reportadas por la API y registradas en cada corrida"}
    faltantes: []
  - id: "E2"
    puntos: 4
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "'Análisis económico'", demuestra: "fuentes (Anthropic y Google) con fecha 6/9/2026, moneda, tarifas por modelo, fórmula que separa entrada/salida, y distinción free tier / tarifa paga / precio introductorio"}
    faltantes: []
  - id: "E3"
    puntos: 4
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "'Proyección año base' y 'Sensibilidad'", demuestra: "proyección 520 corridas/año con fórmula, más dos escenarios alternativos (doble volumen; fin del precio introductorio en 2027)"}
    faltantes: []
  - id: "E4"
    puntos: 4
    evidencia:
      - {tipo: "EV3", ruta: "corridas/corrida_v4_comparacion_modelos.md", localizador: "tabla de resultados", demuestra: "tres modelos sobre la misma entrada y el mismo criterio, salidas conservadas, elección del más chico que cumple con la falla del escalón inferior documentada"}
    faltantes: ["el nivel pro no pudo evaluarse (cuota 0 en free tier), declarado con causa; no afecta la conclusión porque el elegido ya cumple"]
contradicciones: []
topes_aplicados: []
puntaje_final: 15
nivel: "Excelente"
justificacion: "Medición real por corrida, cálculo unitario con fuentes fechadas, proyección con sensibilidad y comparación controlada con la evidencia de la opción que falla."
mejora_prioritaria: "Cuando el negocio salga del free tier, registrar un mes de costos reales facturados contra la proyección."
---
dimension: "Gobierno y riesgo"
subtotal_antes_de_topes: 15
subcriterios:
  - id: "G1"
    puntos: 3
    evidencia:
      - {tipo: "EV4", ruta: "README.md", localizador: "tabla 'Sistemas, datos y permisos'", demuestra: "inventario con alcance mínimo y mecanismo de credenciales (localStorage, nunca versionada)"}
      - {tipo: "EV2", ruta: "corridas/corrida_v4_guido.md", localizador: "herramienta: fetch directo a la API", demuestra: "la implementación observable coincide: ningún otro sistema tocado"}
    faltantes: []
  - id: "G2"
    puntos: 3
    evidencia:
      - {tipo: "EV4", ruta: "README.md", localizador: "tabla 'Riesgos priorizados'", demuestra: "cuatro escenarios con causa, consecuencia e impacto, incluidos privacidad (R3) e instrucciones maliciosas en el hilo (R4)"}
    faltantes: []
  - id: "G3"
    puntos: 3
    evidencia:
      - {tipo: "EV1", ruta: "corridas/corrida_v4_caso_limite.md", localizador: "estado incompleto sin inventos", demuestra: "control del riesgo R2 visible en ejecución; checks del frontend visibles en cada corrida (R1); cache no-store y reintentos como controles de proveedor (DECISIONES 3b)"}
    faltantes: []
  - id: "G4"
    puntos: 3
    evidencia:
      - {tipo: "EV2", ruta: "README.md", localizador: "'Supervisión' y 'Qué pasa cuando sale mal'", demuestra: "objeto, disparador y rol que firma; un check rojo frena la respuesta; proporcional (sin acciones externas del agente)"}
    faltantes: []
  - id: "G5"
    puntos: 3
    evidencia:
      - {tipo: "EV4", ruta: "README.md", localizador: "'Responsables'", demuestra: "dueño del sistema y de los precios; firma quien envía"}
      - {tipo: "EV3", ruta: "corridas/", localizador: "registros con versión de precios", demuestra: "trazabilidad por corrida; reversibilidad trivial (descartar la corrida)"}
    faltantes: []
contradicciones: []
topes_aplicados: []
puntaje_final: 15
nivel: "Excelente"
justificacion: "Permisos mínimos consistentes con lo observable, riesgos concretos con controles probados en ejecución, supervisión proporcional con freno explícito y responsabilidad asignada con trazabilidad por corrida."
mejora_prioritaria: "Probar en una corrida el riesgo R4 (hilo con instrucciones maliciosas) para que su control quede verificado con EV1, como ya lo está el R2."
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

## Qué probó el ensayo (lo que importa para el jueves)

1. **El evaluador funciona sobre estructura ajena.** El repo tiene convenciones distintas de
   los casos de calibración (corridas con nombres propios `corrida_v4_*` + históricas
   `corrida_N_*`, un `index.html`, `datos/` con JSON y plantillas PDF/TTF): el procedimiento
   de inventariar antes de puntuar (§2 del prompt) lo absorbió sin fricción, y el mapeo del
   README resolvió las equivalencias (R1).
2. **Los límites de ejecución se sostuvieron:** había código ejecutable (`index.html`) e
   instrucciones para correrlo; el evaluador no lo ejecutó y puntuó con los registros.
3. **Registró faltantes sin regalar ni castigar de más:** dos observaciones quedaron
   anotadas sin bajar puntos porque la rúbrica no lo exige (corridas v4.1 vs contrato v4.3
   con argumento de no-afectación; esquema formal pendiente ya declarado por el autor).
4. **Score alto con explicación:** 100/100 es consistente con un repo construido por alguien
   que conoce esta rúbrica al detalle (el autor es de este grupo). No leerlo como predicción
   de la nota real: el evaluador de la materia se elige el jueves y puede ser otro.
