---
name: spec-analysis
description: Convertir una intención de producto en criterios de aceptación, blueprint y tareas pequeñas para un flujo SDD.
---

# spec-analysis

Lee .sdd/CONTEXTO.md y las decisiones explícitas del usuario. Separa obligaciones,
propuestas y dudas. Produce AC numerados, observables y sin imponer implementación.
Incluye casos límite, accesibilidad y exclusiones relevantes. No asumas que una
propuesta del contexto ya fue aprobada.

Antes de redactar planes dependientes, detecta definiciones pendientes de producto.
Aplica la etapa de aclaración de .sdd/FLUJO.md: devuelve al coordinador preguntas
con alternativas concretas cuando haya diferencias relevantes, recomendación y
porqué, incluyendo la consecuencia principal. Indica que es un bloque de preguntas,
no una lista necesariamente exhaustiva. Tras recibir respuestas vuelve a comprobar
vacíos sin reabrir lo resuelto. Respeta los límites de cada delegación.
Prepara preguntas de una decisión cada una para que el coordinador use el mecanismo
interactivo de .sdd/FLUJO.md; este puede recurrir al chat si la herramienta no está
disponible. No interpretes preselecciones ni ausencia de respuesta como elecciones.
Espera respuestas o una delegación explícita. No conviertas omisiones en exclusiones,
ni recomendaciones en criterios confirmados. No declares ausencia de bloqueos si
una tarea depende de esas decisiones. Identifica el origen de cada requisito;
las elecciones técnicas internas se justifican en el blueprint.

El blueprint explica módulos, estado, flujo de eventos, decisiones, alternativas
que realmente importan y estrategia de pruebas. No implementes el producto como parte
del plan. Divide por incrementos demostrables; cada tarea enlaza AC y define su
propia validación. No dividas en capas que solo funcionan al terminar todo.

Usa el contrato y los presupuestos de .sdd/FLUJO.md. Pide revisión temprana de QA
por medio del coordinador. Reporta dudas que afecten alcance antes de aprobar.

Para adaptar el proyecto inspecciona versiones, arquitectura y convenciones existentes.
Aplica la política técnica de .sdd/REGLAS.md y concreta en el blueprint skills del
stack, fuentes/versiones relevantes y comandos de calidad con condiciones de éxito.
Justifica lo no aplicable; no instales herramientas durante la planificación.

Define en cada plan qué evidencia demuestra sus criterios y las herramientas
necesarias según FLUJO.md. No exijas grabar todos los escenarios; reserva video
para interacciones donde ayude y declara si es indispensable o complementario.
