---
name: visual-design
description: Definir y comprobar estilo visual, interacción y accesibilidad del juego web de esta demo.
---

# visual-design

Propón en el blueprint una dirección visual breve: paleta, tipografía de sistema,
escala de espacio y jerarquía. Implementa con variables CSS, sin fuentes o assets
remotos. Prioriza tablero, progreso y reinicio; el producto no muestra jerga SDD.

Distingue cartas ocultas, reveladas, emparejadas y foco sin depender solo del color.
Mantén contraste legible, nombres accesibles y navegación por teclado coherente.
Evita anunciar el contenido de cartas ocultas a lectores de pantalla. Comunica
victoria y cambios relevantes sin anunciar cada render.

Diseña sin scroll horizontal desde 360 px; verifica también escritorio. Mantén
objetivos táctiles de al menos 44 px cuando sea viable y foco claramente visible.
Respeta prefers-reduced-motion. La animación no debe determinar reglas del juego.

Inspecciona el navegador y captura estados representativos en móvil y escritorio.
Comprueba foco, teclado, contraste y ausencia de recortes; una captura aislada no
prueba accesibilidad. Si no puedes inspeccionar, registra lo pendiente.
