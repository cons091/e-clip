# e-clip.cloud — Rediseño del sitio web

Sitio web de una página (single-page) para **e-clip**, empresa chilena de monitoreo y
análisis de prensa. HTML/CSS/JS autocontenido, sin dependencias ni build — listo para
GitHub Pages.

## Estructura

```
index.html    → todo el sitio (estilos y scripts incluidos)
assets/       → logos de la marca e-clip (ícono, versión color y versión blanca)
logos/        → logos de clientes (se cargan automáticamente, ver abajo)
```

## Publicar en GitHub Pages

1. Crear un repositorio en GitHub y subir este contenido:
   ```
   git remote add origin https://github.com/<usuario>/<repo>.git
   git push -u origin main
   ```
2. En GitHub: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / `(root)`** → Save.
3. El sitio queda disponible en `https://<usuario>.github.io/<repo>/`.

## Logos de clientes

Cada tarjeta del carrusel busca automáticamente su logo en
`logos/<slug>.png` (también acepta `.svg`, `.jpg`, `.webp`). Si el archivo no existe,
muestra las iniciales del cliente. **Para agregar un logo basta con copiar el archivo
con el nombre correcto — no hay que tocar el código.**

El slug es el nombre en minúsculas, sin acentos, con guiones:

| Cliente | Archivo esperado | Logo actual |
|---|---|---|
| SQM | `logos/sqm.png` | ✅ |
| BPH | `logos/bph.png` | ⬜ falta |
| TRANSELEC | `logos/transelec.png` | ⬜ falta |
| CONSEJO MINERO | `logos/consejo-minero.png` | ✅ |
| SIERRA GORDA SCM | `logos/sierra-gorda-scm.png` | ✅ |
| SM SAAM | `logos/sm-saam.png` | ⬜ falta |
| FCAB | `logos/fcab.png` | ⬜ falta |
| MANTOS COPPER | `logos/mantos-copper.png` | ⬜ falta |
| COORDINADOR ELÉCTRICO NACIONAL | `logos/coordinador-electrico-nacional.png` | ⬜ falta |
| FUNDACIÓN MINERA ESCONDIDA | `logos/fundacion-minera-escondida.png` | ✅ |
| BHP PERÚ | `logos/bhp-peru.png` | ✅ |
| RIO TINTO | `logos/rio-tinto.png` | ✅ |
| MOLYMET | `logos/molymet.png` | ✅ |
| EMPRESA PORTUARIA DE IQUIQUE | `logos/empresa-portuaria-de-iquique.png` | ✅ |
| MINERA GOLD FIELDS | `logos/minera-gold-fields.png` | ✅ |
| PARTNER S.A. | `logos/partner-s-a.png` | ⬜ falta |
| SURVÍAS | `logos/survias.png` | ✅ |
| H2 CHILE | `logos/h2-chile.png` | ✅ |
| TOYOTA CHILE | `logos/toyota-chile.png` | ✅ |
| MINERA LOMAS BAYAS | `logos/minera-lomas-bayas.png` | ⬜ falta |
| PWC | `logos/pwc.png` | ✅ |
| MC INVERSIONES | `logos/mc-inversiones.png` | ⬜ falta |
| ARAUCO | `logos/arauco.png` | ✅ |
| VOY STGO | `logos/voy-stgo.png` | ✅ |
| SUMMIT NANOTEC | `logos/summit-nanotec.png` | ⬜ falta |
| MINERA CANDELARIA | `logos/minera-candelaria.png` | ✅ |
| CMP | `logos/cmp.png` | ✅ |
| SQM NITRATOS | `logos/sqm-nitratos.png` | ✅ |
| SQM LITIO | `logos/sqm-litio.png` | ✅ |

> Los logos actuales provienen del servicio público de favicons de Google (128 px).
> Para producción se recomienda reemplazarlos por los archivos oficiales de cada
> cliente (idealmente PNG/SVG con fondo transparente, cuadrados o casi cuadrados).

## Datos editables

- **Estadísticas** (sección de contadores): buscar `data-count` en `index.html` y
  cambiar los valores placeholder (`20`, `30`, `500`, `5000`).
- **Colores y tipografía**: variables CSS al inicio del `<style>` (`--teal`, `--lime`,
  `--petrol`, etc.). Hay tema claro y oscuro (el oscuro responde a la preferencia del
  sistema del visitante).
- **Hero**: el mock del "Informe de Prensa Diario" (`.hero-visual`) puede reemplazarse
  por una captura real del producto.
- **Marca**: `assets/e-clip-color.png` (fondo claro) y `assets/e-clip-blanco.png`
  (fondo oscuro) quedan disponibles para usos futuros.

---
Desarrollado por Proyecto Órbita.
