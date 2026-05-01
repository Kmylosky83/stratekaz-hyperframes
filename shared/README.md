# Shared

Recursos compartidos entre composiciones. Importar con paths relativos desde `compositions/<dominio>/<archivo>.html`.

| Carpeta | Contenido |
|---|---|
| `styles/` | Design tokens (`tokens.css`), CSS base. |
| `fonts/` | Tipografías locales (cuando no se usa CDN). |
| `images/` | Logos, ilustraciones, fondos reutilizables. |
| `audio/` | Música y efectos de sonido. |
| `components/` | Partials HTML reutilizables (intros, outros, lower-thirds). |

## Brand tokens

Los design tokens viven en `styles/tokens.css` como variables CSS (`--sk-color-*`, `--sk-font-*`, etc.). Ajustar ahí cuando cambien los colores oficiales de StrateKaz.
