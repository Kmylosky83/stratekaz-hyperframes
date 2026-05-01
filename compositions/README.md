# Compositions

Cada subcarpeta agrupa videos por dominio.

| Carpeta | Propósito | Ejemplo |
|---|---|---|
| `marketing/` | Landing, redes sociales, campañas, lanzamientos. | `intro.html` |
| `compliance/` | Explicativos de normativa colombiana. | `compliance/sg-sst/`, `compliance/pesv/` |
| `tutorials/` | Guías y onboarding del producto StrateKaz. | — |
| `reports/` | Reportes en video con datos del backend. | — |

## Estructura mínima de una composición

```html
<div id="root"
     data-composition-id="<id-único>"
     data-start="0"
     data-width="1920"
     data-height="1080">

  <h1 class="clip" data-start="0" data-duration="5" data-track-index="0">…</h1>

  <script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js"></script>
  <script>
    const tl = gsap.timeline({ paused: true });
    tl.from("h1", { opacity: 0, duration: 1 }, 0);
    window.__timelines = window.__timelines || {};
    window.__timelines["<id-único>"] = tl;
  </script>
</div>
```

Reglas:
1. El elemento raíz necesita `data-composition-id`, `data-width`, `data-height`.
2. Cada elemento animado lleva `class="clip"` y `data-start`, `data-duration`, `data-track-index`.
3. El timeline GSAP se crea con `paused: true` y se registra en `window.__timelines`.
4. Reutilizar tokens y assets desde `../shared/`.
