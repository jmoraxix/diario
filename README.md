# diario

Marketplace de Claude Code con el plugin **diario**: skills para el día a día, una por área de tu vida o trabajo, y una que las corre todas.

| Skill | Qué hace |
|---|---|
| `/diario:ejercicio` | Coach sobre tu propio plan de entrenamiento: cuadro del día, ajustes por días perdidos, registro de resultados y videos de YouTube |
| `/diario:dia` | Corre en orden todos los módulos activos y cierra con un resumen |

Próximos módulos: `clientes` (outreach del día), `contenido` (el video del día).

## Instalar

```
/plugin marketplace add jmoraxix/diario
/plugin install diario@jmoraxix
```

Para desarrollarlo desde una copia local: `/plugin marketplace add /ruta/a/diario`.

## Configurar

Cada persona usa sus propias carpetas. La configuración vive fuera del repo, en `~/.claude/diario/config.json`, y la arma la primera corrida de cada módulo con preguntas y ejemplos. Ejemplo completo: [`examples/config.example.json`](examples/config.example.json).

```json
{
  "orden": ["ejercicio", "clientes", "contenido"],
  "modulos": {
    "ejercicio": {
      "activo": true,
      "carpetas": ["~/Notas/Entrenamiento"],
      "registro": "~/Documents/Entrenamiento/registro.xlsx",
      "videos": true,
      "notas": "Equipo y lesiones"
    }
  }
}
```

## Agregar un módulo

1. Crea `plugins/diario/skills/<modulo>/SKILL.md`. Que lea su bloque `modulos.<modulo>` del config y, si no existe, haga la configuración inicial con preguntas y ejemplos (copia la sección 1 de `ejercicio`).
2. Agrega el nombre a `orden` en el ejemplo.
3. Sube `version` en `plugins/diario/.claude-plugin/plugin.json`.

Requisitos de `ejercicio`: `uv` (para leer Excel con openpyxl) y `yt-dlp` para los videos.
