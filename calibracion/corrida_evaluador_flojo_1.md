# Corrida del evaluador — caso FLOJO — corrida 1

- **Herramienta:** Claude Code (Windows 11) · operador: Mateo García
- **Modelo:** `claude-fable-5` · temperatura: `NO_DISPONIBLE`
- **Fecha:** 2026-09-06
- **System prompt:** `agente/system_prompt.md` de la rama `claude/system-prompt-agente-aollz9` (commit `06a1414`)
- **Rúbrica:** `rubrica.md` V3 de la rama `claude/rubrica-tipificar-evidencia-pa18h0` (commit `e768ea6`)
- **Repositorio evaluado:** `casos/flojo/` @ commit `125e7db`
- **Restricciones respetadas:** sin ejecución de código, sin red, solo lectura

## Salida del agente

```
===EVALUACION_INICIO===
dimension: "Sistema completo y funcionando"
subtotal_antes_de_topes: 8
subcriterios:
  - id: "S1"
    puntos: 3
    evidencia:
      - tipo: "EV2"
        ruta: "prompts/system_prompt.md"
        localizador: "bloque de prompt"
        demuestra: "rol, tarea y entrada reconstruibles (comentarios pegados a mano)"
    faltantes: ["sin límites/restricciones", "sin criterio observable de éxito", "la salida declarada en README (JSON) contradice la pedida en el prompt (prosa)"]
  - id: "S2"
    puntos: 3
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/corrida_2.md"
        localizador: "entrada de 5 comentarios + salida + fecha"
        demuestra: "hay salida registrada con entrada asociada, pero sin configuración (el propio registro dice 'no anoté qué modelo')"
    faltantes: ["trazabilidad completa entrada-configuración-ejecución-resultado", "criterio de éxito contra el cual verificar"]
  - id: "S3"
    puntos: 0
    evidencia: []
    faltantes: ["la 'Integración con Google Reviews' del README no tiene configuración ni invocación trazable; DECISIONES.md admite que los comentarios se pegan a mano: la integración sólo se afirma"]
  - id: "S4"
    puntos: 0
    evidencia: []
    faltantes: ["el README promete 'informe en formato JSON estructurado' y ambas corridas devuelven prosa markdown: la salida contradice el contrato declarado"]
  - id: "S5"
    puntos: 0
    evidencia: []
    faltantes: ["sin conducta definida ni ejecutada ante fallas o entradas inválidas"]
  - id: "S6"
    puntos: 2
    evidencia:
      - tipo: "EV4"
        ruta: "README.md"
        localizador: "sección 'Supervisión y riesgos'"
        demuestra: "se requiere revisión humana ('siempre revisamos los informes')"
    faltantes: ["objeto de la revisión", "disparador", "rol responsable"]
contradicciones:
  - "README ('informe en formato JSON estructurado', 'conectado a las reseñas de Google') vs. corridas y DECISIONES.md (salida en prosa; comentarios pegados a mano). Patrón (a) y (b) de §1.2: prevalece la evidencia de corridas (EV3) sobre la declaración (EV4)."
topes_aplicados: []
puntaje_final: 8
nivel: "Insuficiente"
justificacion: "El contrato es parcial y la única ejecución con entrada carece de configuración; la integración y el formato declarados en el README no tienen respaldo y contradicen la evidencia observable."
mejora_prioritaria: "Definir el formato de salida real (esquema) y registrar una corrida completa con modelo y configuración."
---
dimension: "Proceso documentado"
subtotal_antes_de_topes: 12
subcriterios:
  - id: "P1"
    puntos: 3
    evidencia:
      - tipo: "EV2"
        ruta: "prompts/prompt_v1.md"
        localizador: "archivo completo"
        demuestra: "dos iteraciones ordenadas y vinculadas a artefactos (prompt v1 en inglés → prompt actual en español)"
    faltantes: ["tercera iteración distinguible ('fui iterando hasta que quedó perfecto' no identifica versiones)"]
  - id: "P2"
    puntos: 2
    evidencia:
      - tipo: "EV2"
        ruta: "prompts/prompt_v1.md"
        localizador: "prompt en inglés"
        demuestra: "un problema concreto (salida en inglés) con artefacto vinculado que lo corrobora"
    faltantes: ["la corrida que reveló el problema no se conservó", "no hay segundo problema con evidencia"]
  - id: "P3"
    puntos: 3
    evidencia:
      - tipo: "EV2"
        ruta: "prompts/system_prompt.md"
        localizador: "cambio v1→v2 (idioma y rol)"
        demuestra: "una relación completa problema → decisión → cambio inspeccionable"
    faltantes: ["segunda relación completa"]
  - id: "P4"
    puntos: 2
    evidencia:
      - tipo: "EV3"
        ruta: "corridas/corrida_1.md"
        localizador: "salida en español del 29/8"
        demuestra: "verificación posterior identificable de un cambio (la salida ya no está en inglés)"
    faltantes: ["comparación antes/después explícita", "verificación de un segundo cambio"]
  - id: "P5"
    puntos: 2
    evidencia:
      - tipo: "EV4"
        ruta: "DECISIONES.md"
        localizador: "párrafo 'Límites'"
        demuestra: "documenta parte de los límites (pegado manual, volumen no probado)"
    faltantes: ["motivo/impacto de cada límite", "supuestos"]
contradicciones: []
topes_aplicados: []
puntaje_final: 12
nivel: "Básico"
justificacion: "Existe una iteración real y trazable (idioma del prompt) con verificación débil; el resto del proceso se afirma sin versiones ni evidencia."
mejora_prioritaria: "Registrar cada iteración con su corrida: qué falló, qué se cambió y el antes/después."
---
dimension: "Formato y reproducibilidad"
subtotal_antes_de_topes: 1
subcriterios:
  - id: "R1"
    puntos: 1
    evidencia:
      - tipo: "EV2"
        ruta: "."
        localizador: "estructura de carpetas"
        demuestra: "los componentes existen pero el README no explica ni enlaza su ubicación"
    faltantes: ["mapeo inequívoco desde el README"]
  - id: "R2"
    puntos: 0
    evidencia: []
    faltantes: ["sin pasos de reproducción, herramienta/versión, ni preparación de datos ('ChatGPT la versión paga' no es reconstruible)"]
  - id: "R3"
    puntos: 0
    evidencia: []
    faltantes: ["corrida_1 no tiene entrada asociada (no prueba ejecución); corrida_2 no tiene configuración: menos de dos corridas reconstruibles"]
  - id: "R4"
    puntos: 0
    evidencia: []
    faltantes: ["'no anoté qué modelo' (corrida_2): no puede saberse con qué configuración se generaron las salidas"]
  - id: "R5"
    puntos: 0
    evidencia: []
    faltantes: ["sin criterio de reproducción operacionalizado"]
contradicciones: []
topes_aplicados:
  - "R3=0: menos de dos corridas reconstruibles → máximo 4/15"
  - "R2=0: sin instrucciones indispensables → máximo 6/15"
puntaje_final: 1
nivel: "Insuficiente"
justificacion: "Sólo la estructura de carpetas es verificable; sin instrucciones, sin corridas reconstruibles y sin configuración, la reproducibilidad es nominal."
mejora_prioritaria: "Guardar para cada corrida la entrada, la salida, la fecha y el modelo usado, y escribir los pasos de reproducción."
---
dimension: "Análisis económico"
subtotal_antes_de_topes: 0
subcriterios:
  - id: "E1"
    puntos: 0
    evidencia: []
    faltantes: ["sin medición ni método de estimación ('sale menos que un café por día')"]
  - id: "E2"
    puntos: 0
    evidencia: []
    faltantes: ["sólo se declara un costo final (USD 20/mes de suscripción) sin fuente, fecha ni fórmula"]
  - id: "E3"
    puntos: 0
    evidencia: []
    faltantes: ["sin proyección reconstruible"]
  - id: "E4"
    puntos: 0
    evidencia: []
    faltantes: ["sin comparación de opciones; la elección de herramienta no está evaluada"]
contradicciones: []
topes_aplicados:
  - "E2=0: sin cálculo unitario reconstruible → máximo 4/15"
puntaje_final: 0
nivel: "Ausente"
justificacion: "No hay medición, cálculo, proyección ni comparación: sólo afirmaciones de bajo costo."
mejora_prioritaria: "Medir tokens de una corrida real y construir el cálculo unitario con fuente y fecha de precios."
---
dimension: "Gobierno y riesgo"
subtotal_antes_de_topes: 2
subcriterios:
  - id: "G1"
    puntos: 1
    evidencia:
      - tipo: "EV4"
        ruta: "README.md"
        localizador: "'Cómo funciona' y 'Tecnología'"
        demuestra: "inventario parcial de fuentes de datos (reviews, encuestas) descrito genéricamente"
    faltantes: ["permisos, alcance y mecanismo de credenciales", "qué datos de clientes contienen los comentarios y cómo se tratan"]
  - id: "G2"
    puntos: 0
    evidencia: []
    faltantes: ["'como toda IA puede equivocarse' no constituye un escenario con causa, consecuencia e impacto"]
  - id: "G3"
    puntos: 0
    evidencia: []
    faltantes: ["sin mitigaciones accionables ni controles visibles en prompt, configuración o corridas"]
  - id: "G4"
    puntos: 1
    evidencia:
      - tipo: "EV4"
        ruta: "README.md"
        localizador: "'Supervisión y riesgos'"
        demuestra: "menciona revisión humana"
    faltantes: ["objeto, disparador, rol y escalamiento"]
  - id: "G5"
    puntos: 0
    evidencia: []
    faltantes: ["sin dueño ni responsable del resultado; sin trazabilidad mínima"]
contradicciones: []
topes_aplicados: []
puntaje_final: 2
nivel: "Insuficiente"
justificacion: "La supervisión y el riesgo se mencionan como fórmulas genéricas, sin inventario de accesos, escenarios, controles ni responsables."
mejora_prioritaria: "Definir dos riesgos concretos con causa y consecuencia, y un circuito de revisión con objeto, disparador y responsable."
---
tipo: "cierre"
puntaje_total: 23
control_aritmetico:
  - dimension: "Sistema completo y funcionando"
    puntaje_final: 8
    maximo: 30
  - dimension: "Proceso documentado"
    puntaje_final: 12
    maximo: 25
  - dimension: "Formato y reproducibilidad"
    puntaje_final: 1
    maximo: 15
  - dimension: "Análisis económico"
    puntaje_final: 0
    maximo: 15
  - dimension: "Gobierno y riesgo"
    puntaje_final: 2
    maximo: 15
banderas_transversales:
  - "Capacidades declaradas en README sin EV1-EV3 compatible (integración Google Reviews, resultados 'excelentes'): no premiadas (§7)"
observaciones_de_seguridad: []
===EVALUACION_FIN===
```
