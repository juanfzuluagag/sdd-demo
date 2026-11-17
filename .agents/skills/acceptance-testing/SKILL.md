---
name: acceptance-testing
description: Validar criterios funcionales y visuales de una tarea con evidencia independiente y reportes QA reproducibles.
---

# acceptance-testing

Deriva escenarios desde la spec antes de confiar en pruebas del developer.
Relaciona cada AC de la tarea con una comprobación y su resultado. Distingue
pruebas de lógica, integración DOM y recorrido real en navegador.

Para pares de cartas prueba selección repetida, tercera selección, pareja acertada,
fallida, último par y reinicio durante callbacks pendientes cuando aplique al
alcance. Controla tiempo/aleatoriedad; no dependas de pausas arbitrarias ni del
orden aleatorio de una partida. Añade regresión para cada defecto corregido.

Usa herramientas de navegador disponibles o pruebas de navegador reproducibles;
si existe una skill instalada adecuada, léela antes de usarla. No presupongas
plugins en otros equipos. Si falta una herramienta, informa el bloqueo y cómo
resolverlo. Revisa interfaz con visual-design.

Registra revisión estable y hashes de archivos según docs/FLUJO.md, comandos,
resultados, evidencia y esperado/observado. No apruebes con comprobaciones
requeridas pendientes. No corrijas producto ni modifiques criterios. Tras una
reparación ejecuta el caso fallido y regresiones pertinentes. Conserva intentos.
