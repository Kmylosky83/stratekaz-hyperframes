# Guía de composiciones

## Convención de carpetas

Las composiciones se organizan por dominio dentro de `compositions/`. Cada carpeta de dominio se crea **solo cuando hay un HTML adentro** — no dejamos carpetas vacías porque el HyperFrames Studio las lista como entradas.

| Dominio | Cuándo crear la carpeta | Convención de nombre |
|---|---|---|
| `marketing/` | Videos para landing, redes, campañas. | `intro.html`, `feature-tour.html`, `launch-2026.html` |
| `compliance/<norma>/` | Explicativos por norma. Crear `<norma>/` solo cuando se vaya a hacer el primer video. | `intro.html`, `phva.html`, `requisitos.html` |
| `tutorials/` | Guías del producto. | `onboarding.html`, `crear-modulo.html` |
| `reports/` | Reportes en video. | `monthly-template.html`, `client-snapshot.html` |

## Estructura mínima de una composición

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <link rel="stylesheet" href="../../shared/styles/tokens.css" />
  <style>
    html, body { margin: 0; width: 1920px; height: 1080px; overflow: hidden; }
  </style>
</head>
<body>
  <div id="root"
       data-composition-id="<id-único>"
       data-start="0"
       data-width="1920"
       data-height="1080">

    <h1 class="clip"
        data-start="0"
        data-duration="5"
        data-track-index="0">…</h1>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js"></script>
  <script>
    const tl = gsap.timeline({ paused: true });
    tl.from("h1", { opacity: 0, duration: 1 }, 0);
    window.__timelines = window.__timelines || {};
    window.__timelines["<id-único>"] = tl;
  </script>
</body>
</html>
```

## Reglas obligatorias

1. **Elemento raíz** (`#root` o cualquier div con `data-composition-id`) debe tener `data-composition-id`, `data-width`, `data-height`, `data-start`.
2. **Elementos animados** llevan `class="clip"` y `data-start`, `data-duration`, `data-track-index`.
3. **Timeline GSAP** se crea con `paused: true` y se registra en `window.__timelines[<composition-id>]`. HyperFrames hace el seek manual frame por frame.
4. **Reutilizar tokens** desde `../../shared/styles/tokens.css` para consistencia de marca.
5. **Nada en `compositions/` que no sea HTML** — ni `.gitkeep`, ni `README.md`, ni assets. La docs va en `docs/`, los assets en `shared/`.

## Workflow

```bash
npm run preview       # studio en http://localhost:3090 con live-reload
npm run lint          # validar todas las composiciones
npm run render        # exportar a MP4 (requiere FFmpeg)
```

Para ver una composición específica en el studio: abre la URL y haz click en su entrada en la sidebar izquierda. La timeline se muestra abajo, el canvas en el centro.
