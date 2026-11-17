# Protocolo de la demo

## Preparación

1. El coordinador lee el contexto y delega análisis al lead.
2. El lead crea spec con criterios `AC-xx`, blueprint y listado de tareas `Txx`.
3. QA revisa que los criterios sean verificables y que el plan los cubra.
4. El coordinador muestra el panorama y presenta el plan de la primera tarea.

La preparación no autoriza implementación. No se solicita una aprobación separada
del blueprint general: la aprobación de cada tarea incluye su porción del blueprint.
No convertir todas las tareas en una aprobación global en modo manual.

## Contrato de tarea

En `tasks/SPEC-001-tasks.md` mantener una tabla: ID, objetivo, AC, dependencias,
estado y enlace al plan. Cada tarea tiene `plans/Txx.md` (máximo 350 palabras):
objetivo; alcance y exclusiones; archivos previstos; solución y razón; pruebas;
dependencias; revisión del plan. La revisión referencia el contenido aprobado.
Antes de pedir aprobación, calcular SHA-256 de spec, blueprint y plan de tarea.

Estados: `PENDIENTE → PLANIFICADA → ESPERANDO_APROBACION → EN_IMPLEMENTACION →
EN_QA → VALIDADA → DOCUMENTADA → COMPLETADA`.
QA puede pasar a `RECHAZADA → EN_CORRECCION → EN_QA`. Un impedimento real pasa a
`BLOQUEADA` con causa y siguiente acción; nunca se cierra como éxito.

## Una aprobación por tarea

Manual por defecto. Mostrar plan, AC y comprobaciones, y pedir una respuesta como
«Apruebo T01». Registrar en `history/SPEC-001-implementation.md`: tarea, fecha,
modo, referencia a la respuesta y hashes de los tres documentos aprobados.
No inventar la respuesta. Comprobar los hashes antes de delegar implementación.
Si cambian, explicar qué cambió y solicitar aprobación del plan actualizado.

«Activa modo automático para esta ejecución» habilita la alternativa. Registrar
la instrucción y las tareas a las que aplica. Antes de cada tarea, el coordinador
comprueba dependencias completadas, plan verificable, cobertura QA y ausencia de
dudas de producto; registra su autorización automática y los mismos hashes.
El usuario puede volver a manual para tareas futuras. Ningún modo permite ampliar
el alcance automáticamente o saltar QA.

Estas son reglas del coordinador, no un bloqueo técnico del filesystem. Los TOML
no implementan una máquina de estados ni aíslan permisos por rol. Un controlador
programático queda fuera de esta estructura inicial; no anunciarlo como existente.

## Implementación, rechazo y cierre

Developer implementa la tarea aprobada y entrega diff y comprobaciones. QA ejecuta
aceptación sobre una revisión estable: registrar HEAD y SHA-256 de los archivos de
producto y pruebas evaluados, incluyendo archivos nuevos aún sin commit.

Cada revisión `reviews/Txx-qa-NN.md` incluye AC, resultado `APROBADA`, `RECHAZADA`
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

## Documentación acotada

| Artefacto | Presupuesto |
| --- | --- |
| Spec | 700 palabras |
| Blueprint general | 900 palabras |
| Plan por tarea | 350 palabras |
| Reporte QA por intento | 250 palabras, sin contar evidencia adjunta |
| Historia | 120 palabras por tarea y una línea por rechazo |

Actualizar contenido vigente en vez de agregar narraciones. Conservar reportes QA
previos; no borrarlos al corregir. Enlazar logs y capturas, nunca pegarlos completos.
No transcribir conversaciones ni razonamiento interno. Si un límite omite una
condición esencial, compactar primero; justificar una excepción breve y concreta.
