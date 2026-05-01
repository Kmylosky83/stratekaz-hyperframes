# Dominios de compliance

Las composiciones de `compositions/compliance/<norma>/` cubren explicativos de la normativa colombiana que StrateKaz ayuda a implementar.

## Normas cubiertas

| Carpeta destino | Norma | Marco legal | Skill experta |
|---|---|---|---|
| `compliance/sg-sst/` | Sistema de Gestión de SST | Decreto 1072/2015, Resolución 0312/2019, ISO 45001:2018 | `anthropic-skills:sgsst-colombia-experto` |
| `compliance/iso-9001/` | Sistema de Gestión de Calidad | ISO 9001:2015 | `anthropic-skills:sgc-iso9001-experto` |
| `compliance/iso-14001/` | Sistema de Gestión Ambiental | ISO 14001:2015, Decreto 1076/2015 | `anthropic-skills:sga-iso14001-experto` |
| `compliance/iso-45001/` | Sistema de Gestión de SST | ISO 45001:2018 | (cubierto en `sgsst-colombia-experto`) |
| `compliance/pesv/` | Plan Estratégico de Seguridad Vial | Resolución 40595/2022, Ley 1503/2011 | `anthropic-skills:pesv-colombia-experto` |
| `compliance/sig/` | Sistema Integrado de Gestión | Anexo SL/HLS — orquesta las anteriores | `anthropic-skills:sig-integrado-colombia` |

## Tipos de video por norma

Cada norma puede tener múltiples composiciones, sugeridas por orden de prioridad:

1. **`intro.html`** — qué es la norma, a quién aplica, beneficios (15-30s).
2. **`requisitos.html`** — los requisitos clave o cláusulas principales (30-60s).
3. **`phva.html`** — ciclo Planificar/Hacer/Verificar/Actuar aplicado a la norma (45-60s).
4. **`niveles.html`** — para PESV (Básico/Estándar/Avanzado) o SG-SST (estándares mínimos por número de trabajadores).
5. **`casos.html`** — casos prácticos o ejemplos de aplicación.

## Source of truth normativo

Para que el contenido de los videos sea **legalmente preciso**, apoyarse SIEMPRE en las skills correspondientes antes de redactar texto en pantalla, voiceover o subtítulos. Las skills tienen los textos exactos de los artículos, decretos y resoluciones vigentes en Colombia.

Ejemplo de invocación al pedir contenido:
> "Genera el guion de un video de 30s explicando los 3 niveles del PESV según la Resolución 40595/2022, usando la skill `pesv-colombia-experto`."
