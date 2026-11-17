# Instrucciones del proyecto

## Alcance y lenguaje

Trabaja y documenta en español. Lee `CONTEXTO.md` y `docs/FLUJO.md` antes de iniciar
la demo. El repositorio inicial contiene solo preparación: no generes el producto
ni planes anticipadamente durante tareas de mantenimiento del scaffold.

## Orquestación

El chat principal coordina; no necesita otro agente coordinador. Al ejecutar la
demo, delega explícitamente en `technical-lead`, `developer`, `qa-engineer` y
`documenter`, usando sus TOML de `.codex/agents/`. Lee la skill local pertinente
antes del trabajo especializado. Si el cliente no ofrece estos perfiles, informa
la limitación; no simules agentes independientes con mensajes del coordinador.

Entrega a cada agente solo la spec, tarea, plan y evidencia necesarios. Incluye
objetivo, archivos que puede editar, revisión de entrada y salida esperada.
Un solo escritor por archivo. QA puede preparar pruebas mientras desarrollo
implementa si sus archivos son distintos; la validación usa código estable.
Espera el resultado antes de ejecutar pasos dependientes.

## Aprobación y responsabilidad

Sigue `docs/FLUJO.md`. Manual es el modo predeterminado. Antes de implementar,
presenta la tarea y su plan concreto y espera una aprobación explícita del usuario.
No infieras aprobación del silencio. No apruebes en nombre del usuario.
La aprobación cubre implementación, pruebas, hasta dos ciclos de corrección dentro
del alcance, documentación y commit local. No se pide otra aprobación de cierre.
El modo automático requiere una instrucción explícita y queda registrado.

El developer no cambia criterios para hacer pasar pruebas ni emite aprobación QA.
QA no corrige código del producto. El documentador no decide cumplimiento.
Cambiar el alcance o plan aprobado invalida su aprobación; pide una nueva decisión.
Publicar repositorios o hacer push requiere un destino e instrucción del usuario.

## Calidad y control del cambio

Usa `vanilla-web-game` y `visual-design` para producto; `acceptance-testing` para
QA; `spec-analysis` para planificación; `technical-documentation` para documentación.
No agregues frameworks, abstracciones o dependencias sin necesidad justificada.
Revisa el diff completo de la tarea; no mezcles refactors o archivos ajenos.
Ejecuta comprobaciones pertinentes y registra comandos, resultados y limitaciones.
Una prueba no ejecutada nunca cuenta como aprobada. No uses sleeps arbitrarios
para ocultar condiciones de carrera. No desactives pruebas para lograr verde.

Antes del commit, QA debe validar la revisión exacta del producto. Si cambia código
o pruebas después, vuelve a QA. El coordinador comprueba diff, evidencia y estado,
selecciona rutas explícitas para el commit y no incluye cambios ajenos del usuario.
No hagas push automático, resets destructivos ni reescribas historia.

## Modelos

Los perfiles configuran Sol para razonamiento técnico y Luna para síntesis breve.
No cambies modelos silenciosamente. Si falta acceso, informa y usa un modelo
disponible acordado con el usuario, registrando la sustitución. No es obligatorio
usar modelos distintos para que los roles sean independientes.
