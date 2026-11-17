# Base SDD con agentes

Plantilla genérica en español para desarrollo guiado por especificaciones.
El producto, stack y estructura del código se definen al recibir un requerimiento.

## Organización

```text
.
├── AGENTS.md                 # Entrada de instrucciones para Codex
├── .codex/
│   ├── config.toml           # Configuración de modelos y concurrencia
│   └── agents/               # Lead, developer, QA y documentador
├── .agents/skills/           # Procedimientos reutilizables
└── .sdd/
    ├── CONTEXTO.md           # Intención del producto, aún sin definir
    ├── REGLAS.md             # Responsabilidades y calidad
    └── FLUJO.md              # Aprobaciones, QA y cierre
```

`.sdd/specs/`, `.sdd/plans/`, `.sdd/tasks/`, `.sdd/reviews/` y `.sdd/history/`
se crean durante el trabajo. Las carpetas de código y pruebas se deciden según
el stack. `.sdd/` es una convención propia, enlazada explícitamente desde AGENTS.md;
no es una carpeta que Codex descubra automáticamente.

## Por qué estas ubicaciones

- `.codex/agents/` contiene perfiles específicos de Codex.
- `.agents/skills/` es la ubicación documentada para descubrir skills del repositorio.
- `AGENTS.md` en la raíz aplica instrucciones a todo el proyecto; mantiene una
  entrada breve y deriva el detalle a `.sdd/`.
- El contexto es un documento propio, sin nombre o ubicación obligatorios.

Estos archivos son herramientas y documentación de desarrollo versionadas junto
al proyecto, como la configuración de pruebas o CI. No son código del producto
ni deben incluirse en sus artefactos de distribución.

Referencias oficiales: [skills](https://learn.chatgpt.com/docs/build-skills),
[AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md) y
[subagentes](https://learn.chatgpt.com/docs/agent-configuration/subagents).

## Iniciar un proyecto

Abre la carpeta en Codex, comprueba acceso a los modelos configurados y proporciona
el requerimiento. Mensaje sugerido:

> Quiero desarrollar: [requerimiento]. Adapta esta base SDD al proyecto en modo
> manual. Usa los agentes y skills locales. Captura el contexto, propone stack y
> skills pertinentes, genera spec, blueprint y tareas. Pide revisión temprana a QA
> y presenta el plan de la primera tarea. Espera mi aprobación para implementar.

Si faltan definiciones de producto, Codex pregunta antes de fijarlas: presenta
alternativas concretas, su recomendación y por qué, en bloques breves. Tras cada
bloque revisa los pendientes. Registra tus respuestas o una delegación explícita
limitada a las decisiones que hayas indicado. QA revisa tanto fidelidad al requerimiento como verificabilidad.
Las aclaraciones usan preguntas interactivas cuando el cliente lo permite, o
preguntas en el chat como alternativa. Codex espera tu respuesta antes de avanzar
con lo que dependa de ella; una opción preseleccionada no cuenta como respuesta.
El modo automático no permite decidir por ti sobre indefiniciones pendientes.

Responde `Apruebo T01` para autorizar esa tarea y sus correcciones dentro del
alcance, documentación y commit. No hay segunda aprobación ordinaria de cierre.
Puedes indicar `Activa modo automático para las tareas restantes` o
`Vuelve a modo manual antes de iniciar la próxima tarea`.

El flujo se gestiona mediante instrucciones y registros; no incluye un controlador
programático que impida técnicamente transiciones inválidas.

## Modelos y calidad

| Rol | Modelo | Esfuerzo |
| --- | --- | --- |
| Coordinador | gpt-6.1-sol | medium |
| Technical lead | gpt-6.1-sol | high |
| Developer | gpt-6.1-sol | medium |
| QA engineer | gpt-6.1-sol | high |
| Documenter | gpt-6.1-sol | medium |

Se prioriza razonamiento técnico para diseño y validación, y síntesis acotada para
documentación. Son valores iniciales ajustables al proyecto y acceso de la cuenta;
no se sustituyen silenciosamente. Las skills generales cubren análisis, calidad,
QA, documentación breve y diseño visual cuando aplique. Las skills de stack se
seleccionan al conocer el requerimiento.

## Git

La etiqueta `plantilla-inicial` identifica la base genérica. Crea una rama de
trabajo desde ella. Cada tarea completada deja un commit y evidencia QA.
No hay push automático; el destino remoto se configura cuando se indique.

## Contratos de los agentes

Los TOML definen entradas, responsabilidades, límites y condiciones de cierre;
las skills contienen procedimientos compartidos. El lead concreta arquitectura,
skills y comprobaciones del stack. Developer implementa y documenta contratos en
el código; QA revisa diff, comportamiento y regresiones; documenter mantiene la
documentación externa de lo validado. El coordinador gestiona aprobaciones y commits.

Las dependencias se eligen por necesidad, mantenimiento y compatibilidad verificados
en fuentes oficiales, no por un año de lanzamiento. Versiones, justificación y
comandos de calidad se registran en el blueprint conforme a `.sdd/REGLAS.md`.

## Evidencia y documentación

QA guarda un reporte por intento y archivos bajo
`.sdd/reviews/evidence/<SPEC>/<TAREA>/intento-NN/`: `manifest.json`, resultados,
capturas y videos reales cuando aporten evidencia. Cada criterio enlaza prueba,
resultado y evidencia. La política de herramientas, conservación y archivos grandes
está en `.sdd/FLUJO.md`; no se publica evidencia externa automáticamente.

El documentador mantiene un resumen vigente: qué hace el producto, estado real,
requisitos, cómo ejecutarlo/usarlo/probarlo y limitaciones. Enlaza decisiones y QA
sin duplicarlos. El README del producto tiene un objetivo de 600 palabras; solo
el detalle necesario se deriva a guías específicas.
