# Contexto inicial

Queremos demostrar desarrollo guiado por especificaciones (SDD) con agentes de
Codex ante una audiencia técnica. Usaremos dos pantallas: conversación y actividad
de agentes en una; código, pruebas y juego en la otra.

## Producto que queremos explorar

Un juego de memoria de parejas, construido con HTML, CSS y JavaScript nativos,
en español y sin framework de aplicación. Debe ser atractivo, fácil de entender,
usable con teclado y adaptable a móvil y escritorio.

Como punto de partida proponemos ocho parejas, contador de intentos, estado de
victoria y reinicio. Deben estudiarse dobles clics, selección de una tercera carta
y reinicios mientras hay operaciones pendientes. Estos son insumos para la
especificación, no criterios de aceptación completos ni decisiones ya aprobadas.

## Qué debe enseñar la demo

- Cómo la IA transforma una intención en criterios comprobables y un blueprint.
- Cómo propone tareas pequeñas y explica qué cambiará, cómo y por qué.
- Una aprobación humana antes de implementar cada tarea, con modo automático opcional.
- QA independiente, rechazo reproducible, diagnóstico, corrección y revalidación.
- Trazabilidad entre requisito, tarea, cambios, pruebas y documentación breve.
- Evolución visible en Git, con un commit por tarea completada.

## Límites iniciales

Sin backend, cuentas, servicios externos, recursos remotos ni dependencias de
producción. Herramientas de desarrollo y pruebas son admisibles si el blueprint
justifica su uso. No construir un panel de orquestación salvo nueva decisión:
para la primera demo bastan Codex, el listado de tareas y Git.

Un defecto controlado es una opción para un ensayo posterior. No introducirlo
por defecto ni presentarlo como un error espontáneo. No fabricar rechazos de QA.

## Cómo evolucionar este contexto

El lead deriva `specs/SPEC-001.md`, `plans/SPEC-001-blueprint.md` y
`tasks/SPEC-001-tasks.md`. Distingue requisitos, propuestas y dudas. Pregunta solo
por ambigüedades que cambien el producto; propone valores razonables para el resto.
Conserva este archivo como intención de origen. Las decisiones posteriores viven
en la spec y el blueprint, sin copiar aquí su contenido.

La estructura inicial debe permanecer sin juego, spec, blueprint ni tareas
resueltas. El desarrollo comienza cuando el presentador inicia la demo.
