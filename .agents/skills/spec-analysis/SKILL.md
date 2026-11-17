---
name: spec-analysis
description: Convertir una intención de producto en criterios de aceptación, blueprint y tareas pequeñas para esta demo SDD.
---

# spec-analysis

Lee CONTEXTO.md y las decisiones explícitas del usuario. Separa obligaciones,
propuestas y dudas. Produce AC numerados, observables y sin imponer implementación.
Incluye casos límite, accesibilidad y exclusiones relevantes. No asumas que una
propuesta del contexto ya fue aprobada.

El blueprint explica módulos, estado, flujo de eventos, decisiones, alternativas
que realmente importan y estrategia de pruebas. No escribas el juego como parte
del plan. Divide por incrementos demostrables; cada tarea enlaza AC y define su
propia validación. No dividas en capas que solo funcionan al terminar todo.

Usa el contrato y los presupuestos de docs/FLUJO.md. Pide revisión temprana de QA
por medio del coordinador. Reporta dudas que afecten alcance antes de aprobar.
