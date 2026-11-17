# Flujo de desarrollo SDD

## Preparación

1. El coordinador recibe el requerimiento e inspecciona el proyecto y las decisiones
   existentes. El lead captura solo lo confirmado en `.sdd/CONTEXTO.md`.
2. Antes de fijar la spec, el lead identifica definiciones pendientes según
   `.sdd/REGLAS.md`. Devuelve preguntas al coordinador, quien las presenta al usuario
   en bloques breves identificados como tales. Cuando existan alternativas relevantes,
   mostrar en el chat dos o tres opciones concretas y su diferencia principal;
   «aceptar o ajustar» no reemplaza esa comparación. No inventar alternativas para
   completar un número. Cada pregunta incluye recomendación, motivo y consecuencia.
   No marcar la recomendación como elegida ni responder por el usuario.
3. Registrar respuestas o delegaciones explícitas y su alcance en el contexto:
   qué decisiones permite tomar, con qué límites y de qué respuesta proviene.
   Aceptar un bloque resuelve solo sus preguntas; no delega otras decisiones.
   Después de cada respuesta revisar pendientes y nuevas ambigüedades del alcance.
   No anunciar «solo faltan estas decisiones» sin comprobarlo. Formular el siguiente
   bloque si hace falta; no repetir preguntas resueltas ni ampliar el alcance.
   Si hay pendientes, usar `PENDIENTE_ACLARACION` para el contexto o la tarea afectada.
   Puede continuarse investigación independiente; no generar planes dependientes
   ni presentar esas tareas para aprobación. No crear tareas para hacer que el
   usuario apruebe supuestos de manera indirecta.
4. Con las definiciones necesarias resueltas, el lead crea
   `.sdd/specs/SPEC-001.md`, `.sdd/plans/SPEC-001-blueprint.md` y
   `.sdd/tasks/SPEC-001-tasks.md`. Crea carpetas conforme se necesiten.
   Cada requisito identifica su origen: prompt, respuesta del usuario, regla
   vigente del proyecto o decisión dentro de una delegación explícita. Usar IDs
   y referencias breves; distinguir en el blueprint las propuestas técnicas.
5. QA contrasta prompt y respuestas → spec → blueprint → tareas. Comprueba fidelidad,
   verificabilidad, cobertura y que no haya restricciones o exclusiones inventadas.
   Comprobar que cada decisión delegada esté dentro de los límites autorizados.
   Una propuesta comprobable no equivale a un requisito confirmado. Si encuentra
   decisiones de producto pendientes o sin origen, devuelve la planificación para
   aclaración y no la aprueba.
6. Solo con revisión QA favorable y sin decisiones pendientes para la tarea,
   el coordinador presenta su plan para la única aprobación de implementación.

La preparación no autoriza implementación. No se solicita una aprobación separada
del blueprint general: la aprobación de cada tarea incluye su porción del blueprint.
No convertir todas las tareas en una aprobación global en modo manual.

## Aclaraciones interactivas

El coordinador usa la herramienta de preguntas interactivas disponible cuando
sus condiciones de uso lo permitan. Respeta el esquema y modo del cliente; no
asumas que una herramienta existe ni cambies de modo para forzar su uso. Si no
está disponible para esa pregunta, formula la pregunta en el chat y espera respuesta.

Prefiere una decisión por interacción; agrupa hasta tres preguntas estrechamente
relacionadas si facilita responder. No mezcles decisiones independientes dentro
de una sola opción. Presenta alternativas concretas, marca la recomendada y explica
el motivo y su consecuencia. Permite una respuesta libre o distinta de las opciones.

Si la herramienta es asíncrona, deja la pregunta pendiente y continúa únicamente
trabajo independiente. Si no hay trabajo independiente, cede el turno esperando
respuesta. No generes planes dependientes, no repitas la pregunta mientras esté
pendiente y no uses esperas prolongadas para simular una interacción bloqueante.
Una opción preseleccionada, una respuesta vacía, el silencio o el tiempo transcurrido
no constituyen una elección. Registra únicamente la respuesta efectivamente recibida.

Tras responder, actualiza el contexto y revisa pendientes antes de la siguiente
pregunta. Una aclaración no autoriza implementación. Las aprobaciones de tareas
usan el mecanismo permitido por el cliente; no uses una herramienta de aclaraciones
para pedir permisos si sus instrucciones lo prohíben.

## Contrato de tarea

En `.sdd/tasks/SPEC-001-tasks.md` mantener una tabla: ID, objetivo, AC, dependencias,
estado y enlace al plan. Cada tarea tiene `.sdd/plans/Txx.md` (máximo 350 palabras):
objetivo; alcance y exclusiones; archivos previstos; solución y razón; pruebas;
dependencias; revisión del plan. La revisión referencia el contenido aprobado.
Antes de pedir aprobación, calcular SHA-256 de spec, blueprint y plan de tarea.

Estados: `PENDIENTE → PLANIFICADA → ESPERANDO_APROBACION → EN_IMPLEMENTACION →
EN_QA → VALIDADA → DOCUMENTADA → COMPLETADA`.
Desde preparación o planificación se puede pasar a `PENDIENTE_ACLARACION`;
solo se vuelve a planificar tras registrar las respuestas o delegación aplicable.
QA puede pasar a `RECHAZADA → EN_CORRECCION → EN_QA`. Un impedimento real pasa a
`BLOQUEADA` con causa y siguiente acción; nunca se cierra como éxito.

## Una aprobación por tarea

Manual por defecto. Mostrar plan, AC y comprobaciones, y pedir una respuesta como
«Apruebo T01». Registrar en `.sdd/history/SPEC-001-implementation.md`: tarea, fecha,
modo, referencia a la respuesta y hashes de los tres documentos aprobados.
No inventar la respuesta. Comprobar los hashes antes de delegar implementación.
Si cambian, explicar qué cambió y solicitar aprobación del plan actualizado.

«Activa modo automático para esta ejecución» habilita la alternativa. Registrar
la instrucción y las tareas a las que aplica. Antes de cada tarea, el coordinador
comprueba dependencias completadas, plan verificable, cobertura QA y ausencia de
dudas de producto; registra su autorización automática y los mismos hashes.
Automático no autoriza resolver indefiniciones de producto: también debe preguntar
si no existe una delegación explícita para esa decisión.
El usuario puede volver a manual para tareas futuras. Ningún modo permite ampliar
el alcance automáticamente o saltar QA.

Estas son reglas del coordinador, no un bloqueo técnico del filesystem. Los TOML
no implementan una máquina de estados ni aíslan permisos por rol. Un controlador
programático queda fuera de esta estructura inicial; no anunciarlo como existente.

## Implementación, rechazo y cierre

Developer implementa la tarea aprobada y entrega diff y comprobaciones. QA ejecuta
aceptación sobre una revisión estable: registrar HEAD y SHA-256 de los archivos de
producto y pruebas evaluados, incluyendo archivos nuevos aún sin commit.

Cada revisión `.sdd/reviews/SPEC-001-Txx-qa-NN.md` incluye AC, resultado `APROBADA`, `RECHAZADA`
o `BLOQUEADA`, comandos, esperado/observado y enlaces a evidencia. Para rechazos:
identificador de defecto y pasos mínimos reproducibles. QA contrasta con la spec,
no solamente con las pruebas escritas por el developer.

El lead clasifica: error de código → developer; error de diseño → actualizar plan;
ambigüedad de producto → usuario. Hasta dos ciclos de reparación sin cambio de
alcance están autorizados por la aprobación original. Tras agotarlos, bloquear y
explicar la causa. Revalidar el fallo y las regresiones relevantes en cada ciclo.

Después de QA, documenter consolida y el coordinador verifica cierre, crea un
commit local `feat(Txx): descripción breve` y actualiza la vista de progreso.
Mantener referencias por tarea y usar Git para consultar el commit; no intentar
incluir el hash de un commit dentro de sí mismo. Pasar a la siguiente tarea y
pedir únicamente su aprobación de inicio si el modo es manual.

## Evidencia QA

El reporte es obligatorio; selecciona evidencia según el criterio, no por volumen.
Guarda reportes en `.sdd/reviews/<SPEC>-<TAREA>-qa-NN.md` y archivos en
`.sdd/reviews/evidence/<SPEC>/<TAREA>/intento-NN/`. Para planificación usa
`planificacion` en lugar de TAREA. Crea carpetas al ejecutar la revisión, no vacías
por anticipado. No sobrescribas intentos anteriores.

Cada intento incluye `manifest.json` y evidencia real: `resultados.txt` para salidas,
PNG para estados visuales, video corto WebM/MP4 para interacciones o defectos cuando
sea útil y la grabación esté disponible. También se admite prueba manual documentada
con pasos, esperado y observado. No uses imágenes generadas como evidencia de producto.
Una captura o un video no sustituyen las comprobaciones de lógica o accesibilidad.

El manifiesto registra spec/tarea/intento, fecha con zona horaria, tipo de revisión,
entorno y versiones de herramientas/navegadores, revisión base HEAD y SHA-256 de los
archivos de producto y pruebas evaluados (incluidos nuevos), comandos/acciones y
resultados. Por criterio incluye resultado, evidencia enlazada y pasos de reproducción;
por archivo de evidencia, ruta relativa o URL estable, tamaño y SHA-256. No incluir
el manifiesto en su propio listado de hashes. Distinguir lo ejecutado de lo pendiente.
Planificación conserva los hashes de los documentos evaluados, sin fingir pruebas.

El lead define en el plan qué evidencia requiere cada criterio y QA verifica las
herramientas antes de validar. Si no hay grabación, registra la limitación y usa
otra evidencia suficiente. Si el plan exige video o la alternativa no prueba el
criterio, queda pendiente o bloqueado: no aprobar con evidencia insuficiente.

Versiona reportes, manifiestos y evidencia pequeña útil. Por defecto, no añadas
archivos mayores de 10 MiB al Git normal. Conserva los grandes localmente mientras
se acuerda Git LFS o almacenamiento de artefactos con destino y permisos explícitos.
No publiques ni instales LFS automáticamente. Registra toda evidencia que no esté
compartida; no presentes una ruta local como evidencia disponible para otro equipo.
Antes de cerrar, los archivos requeridos deben estar accesibles al revisor en el
destino acordado. Usa `.txt` para salidas a conservar: `*.log` está ignorado.
No incluyas secretos ni datos privados ajenos al escenario de prueba.

El coordinador mantiene estados documentales consistentes. Si modifica un documento
tras QA, conserva la revisión original y registra la modificación administrativa;
si altera alcance, criterios o solución, devuelve a QA y recalcula los hashes antes
de solicitar aprobación. No atribuyas un hash antiguo al contenido actualizado.

## Documentación acotada

| Artefacto | Presupuesto |
| --- | --- |
| README del producto | Objetivo de 600 palabras; detalle necesario enlazado |
| Spec | 700 palabras |
| Blueprint general | 900 palabras |
| Plan por tarea | 350 palabras |
| Reporte QA por intento | 250 palabras, sin contar evidencia adjunta |
| Historia | 120 palabras por tarea y una línea por rechazo |

Actualizar contenido vigente en vez de agregar narraciones. Conservar reportes QA
previos; no borrarlos al corregir. Enlazar logs y capturas, nunca pegarlos completos.
No transcribir conversaciones ni razonamiento interno. Si un límite omite una
condición esencial, compactar primero; justificar una excepción breve y concreta.
