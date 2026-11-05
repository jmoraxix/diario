---
name: dia
description: Corre todos los módulos diarios activos del plugin diario en orden (ejercicio, clientes, contenido...) y entrega un resumen del día. Usar cuando el usuario diga "/diario:dia", "arranquemos el día", "qué tengo hoy", "corre todo lo diario" o "mi día".
---

# diario:dia

1. Lee `~/.claude/diario/config.json`. Si no existe, explícale al usuario que el bundle se configura módulo por módulo y corre el primer módulo instalado (`diario:ejercicio`), que hace la configuración inicial.
2. Para cada nombre en `orden` cuyo módulo tenga `activo: true`, invoca la skill `diario:<nombre>` con la herramienta Skill. Si la skill no existe en el plugin, sáltala y anótala como "no instalada".
3. Cada módulo entrega su propio cuadro resumen. No los repitas: al final agrega solo un cuadro de una línea por módulo:

| Módulo | Hoy | Pendiente del usuario |
|---|---|---|

4. Si un módulo necesita una respuesta del usuario para seguir, termina ese módulo con la pregunta y pasa al siguiente; no bloquees el día por uno.
