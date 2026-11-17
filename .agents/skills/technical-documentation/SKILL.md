---
name: technical-documentation
description: Resumir decisiones y resultados de una tarea SDD con trazabilidad y presupuesto documental acotado.
---

# technical-documentation

Lee el diff, el plan y el reporte QA. Documenta solo hechos respaldados. Si falta
evidencia, devuelve la carencia al coordinador; no completes huecos con supuestos.

Respeta los presupuestos de .sdd/FLUJO.md. La historia por tarea contiene resultado,
una decisión relevante si existe, referencia QA, pruebas y limitaciones. Enlaza
spec, plan y evidencia en lugar de repetirlos. Registra rechazos en una línea con
ID y referencia; preserva sus reportes.

Actualiza instrucciones de uso solo cuando cambien. Evita crear un documento por
cada conversación, resúmenes duplicados y narración cronológica de herramientas.
Usa frases directas y tablas solo para datos comparables. No documentes razonamiento
interno. Antes de entregar cuenta palabras, elimina repetición y verifica enlaces.

Mantén README, requisitos de entorno, instalación, ejecución, configuración y
comprobaciones solo cuando el cambio los afecte. Contrasta comandos y ejemplos con
archivos y evidencia; distingue inspección de ejecución. Actualiza instrucciones
obsoletas dentro del alcance. La documentación del código corresponde al developer:
no edites fuentes ni configuración ejecutable. Reporta contradicciones al coordinador
para corrección y nueva QA cuando corresponda, en vez de justificarlas en el texto.

El README del producto debe permitir entender y ejecutar el resultado sin leer
los chats: propósito y estado real, requisitos/versiones necesarias, comandos de
instalación y ejecución, uso principal, configuración relevante sin secretos,
cómo probar, limitaciones conocidas y enlaces a decisiones/evidencia QA.
Incluye solo secciones aplicables y hechos verificados. Objetivo: 600 palabras;
si necesita detalle, enlaza una guía existente o una específica con propósito claro.
Evita manuales genéricos, secciones vacías y reproducir toda la arquitectura.

La historia de cada tarea resume qué cambió, por qué importa, qué validó QA y qué
queda pendiente. Enlaza reporte y manifiesto, sin copiar resultados ni videos.
Distingue implementado, validado y previsto; no anuncies funcionalidades futuras
como disponibles. Mantén un resumen vigente, no una acumulación de resúmenes.
