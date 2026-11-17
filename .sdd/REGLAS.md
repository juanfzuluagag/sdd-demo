# Instrucciones del proyecto

## Alcance y lenguaje

Trabaja y documenta en español. Lee `.sdd/CONTEXTO.md` y `.sdd/FLUJO.md` antes de iniciar
el desarrollo. El repositorio inicial contiene solo preparación: no generes el producto
ni planes anticipadamente durante tareas de mantenimiento del scaffold.

## Orquestación

El chat principal coordina; no necesita otro agente coordinador. Al ejecutar el
flujo SDD, delega explícitamente en `technical-lead`, `developer`, `qa-engineer` y
`documenter`, usando sus TOML de `.codex/agents/`. Lee la skill local pertinente
antes del trabajo especializado. Si el cliente no ofrece estos perfiles, informa
la limitación; no simules agentes independientes con mensajes del coordinador.

Entrega a cada agente solo la spec, tarea, plan y evidencia necesarios. Incluye
objetivo, archivos que puede editar, revisión de entrada y salida esperada.
Un solo escritor por archivo. QA puede preparar pruebas mientras desarrollo
implementa si sus archivos son distintos; la validación usa código estable.
Espera el resultado antes de ejecutar pasos dependientes.

## Aprobación y responsabilidad

Sigue `.sdd/FLUJO.md`. Manual es el modo predeterminado. Antes de implementar,
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

Usa `implementation-quality` para implementación y `visual-design` si hay interfaz; `acceptance-testing` para
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

Los perfiles configuran Sol con esfuerzo por rol; el documentador usa esfuerzo
medio para síntesis acotada. Verifica acceso a los modelos antes de delegar.
No cambies modelos silenciosamente. Si falta acceso, informa y usa un modelo
disponible acordado con el usuario, registrando la sustitución. No es obligatorio
usar modelos distintos para que los roles sean independientes.

## Adaptación al requerimiento

Esta base no presupone producto, lenguaje, plataforma ni estructura de código.
Si no existe un requerimiento, solicítalo antes de generar specs o planes.
Al recibirlo, el lead captura la intención en `.sdd/CONTEXTO.md`, inspecciona
lo existente y propone tecnologías, estructura y skills especializadas pertinentes.
Reutiliza skills disponibles; no instales dependencias ni crees skills de stack
por anticipado. Justifica las incorporaciones en el plan de la tarea correspondiente.
Guarda artefactos del proceso bajo `.sdd/`; crea carpetas de producto y pruebas
solo cuando una tarea aprobada las necesite. Las reglas SDD son versionadas junto
al producto para que el equipo comparta decisiones y pueda auditar los cambios.

## Definiciones pendientes

Si falta una definición que cambie el comportamiento observable, el alcance,
las restricciones o los criterios de aceptación, pregunta antes de fijarla.
Puedes proponer opciones, pero no seleccionar una por el usuario sin delegación
explícita. Cada pregunta incluye una recomendación y el porqué, con su principal
consecuencia o compromiso. Consulta primero los insumos existentes para no repetir
preguntas ya respondidas.

El silencio y el modo automático no delegan decisiones de producto. Una omisión
no se convierte en exclusión ni en restricción. Las decisiones técnicas internas
pueden proponerse razonadamente, siempre que no introduzcan esas definiciones.
Registra el origen de los requisitos y las decisiones en el contexto; mantiene
pendientes las preguntas sin respuesta. No presentes para aprobación una tarea
que dependa de ellas. Aclarar requisitos no es aprobar la implementación.

La delegación se limita a las decisiones nombradas y sus condiciones; aceptar una
recomendación no delega asuntos distintos. El coordinador muestra las alternativas
relevantes en el chat, no solo en archivos, y revisa vacíos después de cada bloque
según `.sdd/FLUJO.md`. Mantén las aclaraciones centradas en el alcance solicitado.

Para aclarar, el coordinador prefiere preguntas interactivas cuando estén disponibles
y permitidas; en caso contrario pregunta en el chat. Sigue `.sdd/FLUJO.md` y espera
respuesta real antes de avanzar con trabajo dependiente. Ni una preselección ni
la ausencia de respuesta autorizan a elegir por el usuario.

## Dependencias, APIs y compatibilidad

Antes de incorporar una dependencia o usar una API cuya compatibilidad sea
relevante, consulta documentación oficial y versiones estables mantenidas.
Comprueba compatibilidad con runtime, plataforma y dependencias del proyecto.
Registra versión elegida, motivo, fuente y fecha de consulta en el blueprint;
usa la documentación de esa versión, no ejemplos de otra por memoria.
No impongas un año de lanzamiento ni actualices dependencias ajenas a la tarea.
Conserva versiones existentes compatibles salvo necesidad justificada. Si no hay
acceso para verificar un dato necesario, registra la incertidumbre y resuélvela
antes del trabajo dependiente. Usar APIs nativas puede evitar una dependencia.
Usa lockfile o mecanismo equivalente cuando aplique; no generes archivos de otro
ecosistema ni instales herramientas innecesarias.

## Contrato de calidad por proyecto

El blueprint concreta skills del stack y comandos de formato, análisis estático,
pruebas y construcción cuando apliquen, con propósito y condición de éxito.
Justifica brevemente comprobaciones no aplicables. Distingue comandos propuestos
de comandos ejecutados. Las skills especializadas se leen antes de trabajar;
no basta con enumerarlas. El developer valida y QA revisa código y comportamiento
con independencia, considerando riesgos y regresiones relevantes al alcance.

El developer mantiene comentarios útiles, JSDoc/docstrings y contratos junto al
código. El documenter actualiza documentación externa a partir del resultado QA.
Si detecta una contradicción, la devuelve al coordinador; cualquier corrección
de producto o pruebas vuelve a QA antes del cierre. No repitas lo obvio ni añadas
comentarios ceremoniales para aparentar documentación.

QA conserva reporte y evidencia por intento conforme a FLUJO.md. El documenter
resume el estado verificado del proyecto y enlaza esa evidencia; no altera el
veredicto ni reemplaza las pruebas con documentación. Las grabaciones se obtienen
del producto ejecutado y las limitaciones de captura se registran explícitamente.
