---
name: acceptance-testing
description: Validar criterios de aceptación con evidencia independiente y reportes QA reproducibles para el stack del proyecto.
---

# acceptance-testing

En planificación compara primero el requerimiento original y las respuestas del
usuario con la spec. Verifica el origen de cada requisito y detecta exclusiones,
restricciones o comportamientos añadidos sin confirmación ni delegación explícita.
Comprueba que las decisiones delegadas no excedan las materias y límites aceptados.
No apruebes un plan dependiente de decisiones pendientes aunque todos sus criterios
sean comprobables; devuelve los vacíos al coordinador para aclaración.

Deriva escenarios desde la spec antes de confiar en pruebas del developer.
Relaciona cada AC de la tarea con una comprobación y resultado. Selecciona pruebas
unitarias, integración o extremo a extremo según el riesgo y los límites reales.

Incluye casos normales, entradas inválidas, límites y recuperación cuando sean
pertinentes. Controla dependencias externas, tiempo y aleatoriedad si intervienen.
Añade una regresión para cada defecto corregido sin acoplarla a detalles internos.

Usa herramientas y skills disponibles adecuadas al stack; no presupongas plugins.
Si falta una herramienta necesaria, informa el bloqueo y cómo resolverlo. Usa
visual-design solo si hay interfaz que revisar.

Registra revisión estable y hashes según .sdd/FLUJO.md, comandos, resultados,
evidencia y esperado/observado. No apruebes con comprobaciones requeridas pendientes.
No corrijas producto ni modifiques criterios. Tras reparar, ejecuta el caso fallido
y regresiones pertinentes. Conserva reportes previos.

Revisa el diff y los riesgos introducidos: contratos, entradas, errores, recursos,
seguridad y rendimiento cuando sean pertinentes. Prioriza impacto reproducible.
Verifica que la evidencia de formato/análisis/pruebas corresponda a los comandos
acordados y a la revisión actual. Pruebas verdes no demuestran por sí solas cobertura.

Aplica la sección Evidencia QA de .sdd/FLUJO.md. Relaciona cada criterio con prueba,
resultado y archivo de evidencia; crea reporte y manifiesto por intento. Usa
capturas o video de ejecución real cuando aporten evidencia, con herramientas
verificadas. Documenta pasos manuales y limitaciones. Conserva rechazos y su
revalidación; verifica rutas, hashes y accesibilidad de evidencia antes de cerrar.
