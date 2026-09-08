Estado del proyecto — 08/09/2026

Proyecto: Agente Corrector — MBA UCEMA
Branch de seguimiento: andreavergara-seguimiento
Corte revisado: GitHub remoto al 08/09/2026.
Leyenda: 🟢 Terminado · 🔵 En curso · 🟡 Falta revisar/cerrar · ⬜ Pendiente.

1. Estado actual
Frente	Estado	Explicación simple
Rúbrica	🟡	La V3 está integrada y funcionando. Queda pendiente cerrar H2, una aclaración sobre cómo interpretar cierta evidencia. No bloquea el resto del trabajo.
Agente corrector	🟡	El agente ya existe y está integrado. Falta cerrar una corrección de configuración y hacer la validación final.
Caso Excelente	🟢	Está construido y el agente logró evaluarlo correctamente.
Caso Flojo	🟢	Está construido y el agente logró distinguirlo como trabajo débil.
Caso Tramposo	🟢	Está construido y el agente detectó los intentos de manipulación.
Segunda corrida de los casos	🔵	Falta repetir la evaluación de los tres casos sin modificar los casos, para comprobar que el agente da resultados estables.
Calibración	🔵	Ya existe una primera calibración y varios hallazgos. Falta incorporar las segundas corridas y cerrar los pendientes.
Ruta de las salidas	🟡	Leo ya preparó la corrección. El PR #7 está abierto y espera revisión de Toni.
Integración en main	🔵	Rúbrica, agente, casos y primera calibración ya están integrados. main sigue en 0d54789; la nueva corrección de Leo todavía no entró.
README	🟡	Existe, pero todavía tiene roles vacíos y estado desactualizado al 03/09.
Prueba con un trabajo externo	⬜	Todavía falta probar el agente con un repositorio real que no haya usado durante su construcción.
QA final contra la consigna	⬜	Falta hacer la revisión final de que todo lo pedido para la entrega esté efectivamente presente y funcionando.
Entrega final	🔵	La mayor parte está construida. Ahora estamos en etapa de validación y cierre.
2. Novedades desde el último corte
Leo creó la branch leo/corregir-ruta-corridas y abrió el PR #7.
El PR #7 corrige la ruta de salida del evaluador para que las evaluaciones se guarden en calibracion/ y no dentro de los casos sintéticos.
La branch local andreavergara-h2-ev1-ev3 trabajada el 07/09 no está todavía publicada en GitHub. Por eso H2 sigue pendiente en el estado remoto.
No hay que frenar el resto del proyecto por H2: su resolución afecta principalmente la interpretación EV1/EV3 en S2 y E1 y el cierre metodológico final.
3. Próximos pasos y responsables
Orden	Qué hay que hacer	Responsable	Explicación simple
1	Revisar y mergear PR #7	Toni	Confirmar que el cambio de Leo es correcto y agregarlo a main.
2	Segunda corrida de Excelente, Flojo y Tramposo	Mateo + Tomás	Correr nuevamente el agente sobre los mismos casos, sin cambiarlos, y comprobar que mantiene las notas/criterios.
3	Actualizar calibración con esas corridas	Mateo + Tomás	Dejar escrito qué pasó en las segundas pruebas y si el agente fue estable.
4	Revisar configuración y formato de salida	Leo + Toni	Confirmar que el agente guarda el resultado donde corresponde y entrega la estructura esperada.
5	Revisar conceptualmente H2	Ignacio	Revisar la regla H2 para que luego sólo quede validarla técnicamente.
6	Recuperar y publicar branch H2	Andrea	Desde la computadora donde quedó local, hacer push de la candidata H2.
7	Validar H2 y decidir si se incorpora	Andrea + Ignacio	Probar la candidata. Si funciona mejor y no genera efectos secundarios, pedir revisión a Toni.
8	Probar el agente con un repositorio externo real	Equipo / Dupla 2	Comprobar que funciona con un trabajo que el agente nunca haya visto.
9	Actualizar README	Toni + Andrea	Completar roles, estado, estructura y fecha final.
10	QA final contra la consigna	Andrea + Toni	Revisar punto por punto que no falte nada antes de entregar.
11	Congelar main para entrega	Toni	Una vez validado todo, no hacer más cambios y dejar identificado el commit final.
4. Mensaje simple para el equipo

No estamos en etapa de construir cosas nuevas. Rúbrica, agente y casos ya existen. De acá a la entrega el objetivo es probar que funcionan de forma consistente, cerrar los pocos pendientes, actualizar la documentación y hacer el control final.

5. Pendientes que NO deben bloquear el trabajo de hoy

H2 sigue pendiente, pero no impide avanzar con:

PR #7;
segunda corrida de los tres casos;
actualización de calibración;
revisión de configuración y formato;
prueba externa;
README;
checklist de QA.

Lo que no debe cerrarse definitivamente hasta resolver H2 es la validación metodológica final de la rúbrica, la calibración completa y el congelamiento final de main.
