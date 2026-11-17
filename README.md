# Demo SDD con agentes

Repositorio inicial para una demostración técnica en español. El juego, la
especificación y el blueprint se generan durante la demo a partir de
[CONTEXTO.md](CONTEXTO.md).

## Arrancar

Abre este directorio en una versión de Codex con agentes personalizados. Revisa y
confía en la configuración local cuando el cliente lo solicite. Comprueba que los
modelos configurados estén disponibles en tu cuenta antes de presentar.

Primer mensaje sugerido:

> Inicia la demo SDD desde CONTEXTO.md en modo manual. Usa los agentes definidos
> en .codex/agents y las skills del proyecto. Genera la especificación, blueprint
> y tareas, pide a QA revisar su verificabilidad y presenta el plan de la primera
> tarea para mi aprobación. No implementes hasta recibirla.

Luego: `Apruebo T01`. Para continuar sin aprobaciones por tarea:
`Activa modo automático para las tareas restantes de esta ejecución`.
Para volver: `Vuelve a modo manual antes de iniciar la próxima tarea`.

La única aprobación ordinaria ocurre antes de implementar cada tarea. Incluye
correcciones dentro del alcance, documentación y commit. Consulta las condiciones
exactas en [docs/FLUJO.md](docs/FLUJO.md).

## Qué contiene

- `AGENTS.md`: reglas comunes y delegación.
- `.codex/`: configuración y cuatro roles.
- `.agents/skills/`: análisis, JavaScript, estilo visual, QA y síntesis documental.
- `specs/`, `plans/`, `tasks/`: vacíos hasta comenzar la demo.
- `src/`, `tests/`, `reviews/`, `history/`: vacíos hasta ejecutar el flujo.

No hay juego, dependencias npm ni controlador de estados implementados. Las
aprobaciones se gestionan conversacionalmente y se registran en archivos.

## Modelos por rol

| Rol | Modelo | Esfuerzo | Motivo |
| --- | --- | --- | --- |
| Coordinador | gpt-6.1-sol | medium | Dependencias y seguimiento |
| Technical lead | gpt-6.1-sol | high | Ambigüedades y diseño |
| Developer | gpt-6.1-sol | medium | Implementación acotada |
| QA engineer | gpt-6.1-sol | high | Casos límite y revisión independiente |
| Documenter | gpt-6-luna | high | Síntesis con alcance estrecho |

Esta asignación es una decisión de la demo, no un benchmark. Si un modelo no está
disponible, acordar una sustitución antes del ensayo. La selección del cliente
puede prevalecer para el coordinador; comprobarla al abrir la sesión.
Configuración contrastada el 17 de noviembre de 2026 con la
[documentación oficial](https://learn.chatgpt.com/docs/agent-configuration/subagents).

## Presentación y Git

Pantalla 1: Codex y agentes. Pantalla 2: editor, diff, pruebas y navegador.
Usa una rama por ejecución, por ejemplo `git switch -c demo/ensayo-01` desde
`demo-start`. Cada tarea completada deja un commit y sus reportes QA.
Para repetir, crea otra rama desde `demo-start`; conserva las ejecuciones previas.
No reinicies una ejecución con cambios sin guardar.

El repositorio remoto se configura cuando se conozca su destino; no hay push
implícito. Antes de presentar, ensaya acceso a modelos, reconocimiento de agentes
y herramientas de navegador. La configuración está preparada; una ejecución real
será la comprobación de integración de los agentes.
