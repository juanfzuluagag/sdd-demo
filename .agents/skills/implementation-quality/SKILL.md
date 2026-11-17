---
name: implementation-quality
description: Implementar una tarea aprobada con cambios acotados, convenciones del stack y comprobaciones reproducibles.
---

# implementation-quality

Lee la tarea aprobada, el blueprint y las convenciones del proyecto. Selecciona
skills técnicas disponibles que correspondan al lenguaje y herramientas elegidos;
no presupongas stack. Informa si falta una capacidad necesaria.

Separa responsabilidades según la complejidad real. Mantén contratos y estado
explícitos, valida entradas en los límites y gestiona errores y recursos. Evita
abstracciones anticipadas y cambios ajenos. Reutiliza patrones existentes.

Aplica la política de dependencias, APIs y compatibilidad de .sdd/REGLAS.md.
Justifica nuevas dependencias; usa mecanismos reproducibles propios del ecosistema.
Configura formato, análisis estático y pruebas pertinentes cuando se adopte el
stack. No añadas herramientas que no aporten una comprobación concreta.

Prueba comportamiento observable y casos límite del alcance. Revisa el diff y
regresiones posibles, ejecuta comprobaciones y registra limitaciones. Si hay
interfaz, usa visual-design. No cambies criterios ni emitas tu propio veredicto QA.

Mantén comentarios que expliquen decisiones no evidentes y contratos públicos
cuando aporten información. Usa el formato documental del lenguaje. Actualízalos
con el comportamiento; no dejes ejemplos contradictorios ni copies el código en prosa.
Entrega una relación criterio/comprobación y señala cambios que afecten documentación
externa para el documenter. Nunca atribuyas evidencia a comandos no ejecutados.
