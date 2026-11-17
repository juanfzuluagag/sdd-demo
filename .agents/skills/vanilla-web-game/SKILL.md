---
name: vanilla-web-game
description: Implementar y revisar la lógica y el DOM de un juego con HTML, CSS y JavaScript nativos.
---

# vanilla-web-game

Lee la tarea aprobada. Separa reglas y estado de la manipulación del DOM para
probar transiciones sin navegador. Usa módulos ES, nombres consistentes y una
fuente de estado; evita deducir reglas de clases CSS o textos de la interfaz.

Diseña transiciones explícitas para selección, comparación, victoria y reinicio.
Cancela o invalida callbacks pendientes al reiniciar. Trata clics repetidos y
acciones durante animaciones como entradas normales que deben tener resultado
definido. Permite controlar aleatoriedad y tiempo en pruebas sin alterar producción.

Usa botones y HTML semántico; textContent para texto variable; listeners con un
ciclo de vida claro. No agregues bibliotecas de producción. Justifica herramientas
de desarrollo, fija sus dependencias con lockfile y documenta comandos ejecutables.
Configura formato/lint cuando exista código, sin introducir herramientas ahora.

Prueba comportamiento y límites, no detalles internos. Revisa diff, efectos
secundarios, consola y cleanup. Complementa con visual-design para la interfaz.
