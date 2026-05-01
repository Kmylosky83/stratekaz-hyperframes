# StrateKaz HyperFrames

Workspace multipropósito de videos generados con [HyperFrames](https://github.com/heygen-com/hyperframes) (HeyGen) para el ecosistema [StrateKaz](https://github.com/Kmylosky83/stratekaz).

> **Tagline HyperFrames**: *Write HTML. Render video. Built for agents.*

Este repo es **independiente** del repo principal `stratekaz` y **se complementa con él**: aquí se generan los videos (marketing, normativos, tutoriales, reportes) que se consumen desde la plataforma o los canales de comunicación.

## Dominios soportados

| Carpeta | Propósito |
|---|---|
| `compositions/marketing/` | Videos para landing, redes sociales, campañas. |
| `compositions/compliance/` | Explicativos de normativa colombiana: `sg-sst/`, `iso-9001/`, `iso-14001/`, `iso-45001/`, `pesv/`. |
| `compositions/tutorials/` | Guías del producto StrateKaz. |
| `compositions/reports/` | Reportes en video generados desde datos del backend Django. |

## Estructura

```
stratekaz-hyperframes/
├── compositions/         # Composiciones HTML por dominio
│   ├── marketing/
│   ├── compliance/
│   ├── tutorials/
│   └── reports/
├── shared/               # Recursos compartidos
│   ├── styles/           # CSS base, design tokens StrateKaz
│   ├── fonts/
│   ├── images/
│   ├── audio/
│   └── components/       # Partials HTML reutilizables
├── data/                 # JSON de prueba para inyectar en plantillas
├── outputs/              # Videos renderizados (gitignored)
├── docs/                 # Documentación interna
├── tests/                # Pruebas de composiciones
├── meta.json             # Metadata del workspace
├── index.html            # Composición demo raíz
└── package.json
```

## Setup

Requiere **Node.js ≥ 22**.

```bash
nvm use            # usa la versión declarada en .nvmrc
npm install        # instala hyperframes y dependencias
```

## Comandos

```bash
npm run preview                       # preview live-reload de la composición raíz
npm run render                        # renderiza la composición raíz a MP4
npm run lint                          # valida composiciones

npm run render:marketing              # renderiza videos de marketing
npm run render:compliance:sg-sst      # renderiza explicativo SG-SST
npm run render:compliance:iso-9001    # renderiza explicativo ISO 9001
npm run render:compliance:pesv        # renderiza explicativo PESV
npm run render:tutorials              # renderiza tutoriales
npm run render:reports                # renderiza reportes
```

## Crear una composición nueva

1. Elegir el dominio: `marketing/`, `compliance/<norma>/`, `tutorials/` o `reports/`.
2. Crear el archivo `<nombre>.html` con la estructura mínima de HyperFrames:
   - Elemento raíz con `data-composition-id`, `data-width`, `data-height`, `data-start`.
   - Elementos animados con `class="clip"` y `data-start`, `data-duration`, `data-track-index`.
   - Timeline GSAP (u otro adapter) en `window.__timelines`.
3. Reutilizar tokens y assets desde `shared/`.
4. Probar con `npm run preview`.

Ver `index.html` y `compositions/marketing/intro.html` como referencia.

## Stack

- **HyperFrames** (Apache 2.0) — motor HTML→MP4 vía Puppeteer + FFmpeg.
- **Animation runtimes**: GSAP, Lottie, CSS keyframes, Three.js, anime.js, WebGL shaders.
- **Output determinista**: el mismo HTML produce siempre el mismo video.

## Relación con el ecosistema StrateKaz

- Los **videos de compliance** consumen los conceptos normativos de las skills `*-colombia-experto`.
- Los **reportes en video** pueden consumirse desde el backend Django de [stratekaz](https://github.com/Kmylosky83/stratekaz) inyectando datos por `data/`.
- Los **tutoriales** se publican junto a la documentación del producto.
