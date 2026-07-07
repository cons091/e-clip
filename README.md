# e-clip.cloud — Rediseño del sitio web

Sitio web de una página (single-page) para **e-clip**, empresa chilena de monitoreo y
análisis de prensa (clipping electrónico) para grandes empresas de minería, energía,
puertos e industria. HTML/CSS/JS autocontenido, **sin dependencias ni build** — listo
para GitHub Pages.

> ℹ️ Es un **mockup estático de presentación**: no tiene backend. El formulario de
> contacto valida y muestra un mensaje de éxito simulado, pero **no envía correos**.

**En vivo:** https://cons091.github.io/e-clip/ · **Repo:** https://github.com/cons091/e-clip

## Estructura

```
index.html    → TODO el sitio (HTML + CSS + JS en un solo archivo)
assets/       → marca e-clip: e-clip-icon.png, e-clip-color.png, e-clip-blanco.png
logos/        → logos de clientes (se cargan automáticamente, ver abajo)
README.md     → este archivo
CLAUDE.md     → contexto para asistentes de IA (Claude Code)
.claude/      → config local del entorno (ignorada por git)
```

Secciones del sitio, en orden: **Hero → Pilares → Nosotros → Estadísticas →
Servicios → Clientes → Contacto**. (No hay footer, se eliminó a pedido.)

## Ver el sitio localmente

Como es estático, cualquier servidor sirve. Por ejemplo:

```bash
npx http-server . -p 8321 -c-1
# luego abrir http://localhost:8321
```

> No basta con abrir `index.html` con doble clic (`file://`): los logos se cargan por
> rutas relativas y necesitan un servidor HTTP para funcionar bien.

## Publicar / actualizar en GitHub Pages

Ya está configurado (Settings → Pages → branch `main` / root). Para publicar cambios:

```bash
git add -A
git commit -m "descripción del cambio"
git push origin main
```

El sitio se actualiza solo ~1 minuto después del push.

> **Autenticación:** el remoto NO tiene token guardado (por seguridad). El `push`
> pedirá credenciales de GitHub; usa un Personal Access Token propio de la cuenta
> `cons091`. Nunca dejes el token escrito en archivos ni en el remoto.

## Logos de clientes (carga automática)

Cada tarjeta del carrusel busca su logo en `logos/<slug>.png` (también acepta
`.svg`, `.jpg`, `.webp`, en ese orden). **Si el archivo no existe, muestra las
iniciales del cliente como respaldo.** Para agregar un logo basta copiar el archivo
con el nombre correcto — **no hay que tocar el código**.

El `slug` = nombre en minúsculas, sin acentos, con guiones (ej: `CONSEJO MINERO`
→ `consejo-minero`). El recuadro del logo es horizontal y escala los wordmarks
anchos sin deformarlos.

### Estado actual (27 de 29 con logo)

**Faltan 2** — al subirlos con este nombre aparecen automáticamente:

- ⬜ **Mantos Copper** → `logos/mantos-copper.png`
- ⬜ **Minera Lomas Bayas** → `logos/minera-lomas-bayas.png`

El resto (SQM, BPH, Transelec, Consejo Minero, Sierra Gorda, SM SAAM, FCAB,
Coordinador Eléctrico, FME, BHP Perú, Rio Tinto, Molymet, EPI, Gold Fields, Partner,
Survías, H2 Chile, Toyota, PwC, MC Inversiones, Arauco, Voy Stgo, Summit Nanotec,
Candelaria, CMP, SQM Nitratos, SQM Litio) ya tienen logo.

> ⚠️ Varios logos actuales provienen del servicio público de favicons de Google
> (128 px) y se ven algo pixelados. Para producción conviene reemplazarlos por los
> archivos oficiales de cada cliente (PNG/SVG con fondo transparente, idealmente
> horizontales o cuadrados).

### Lista completa de clientes (nombre → año → archivo)

Editable en el array `CLIENTES` dentro de `index.html`.

SQM (2004), BPH (2006), TRANSELEC (2008), CONSEJO MINERO (2014), SIERRA GORDA SCM
(2014), SM SAAM (2014), FCAB (2016), MANTOS COPPER (2017), COORDINADOR ELÉCTRICO
NACIONAL (2017), FUNDACIÓN MINERA ESCONDIDA (2018), BHP PERÚ (2018), RIO TINTO
(2018), MOLYMET (2018), EMPRESA PORTUARIA DE IQUIQUE (2019), MINERA GOLD FIELDS
(2019), TOYOTA CHILE (2020), MINERA LOMAS BAYAS (2020), PARTNER S.A. (2021), SURVÍAS
(2021), H2 CHILE (2022), PWC (2022), MC INVERSIONES (2023), ARAUCO (2023), VOY STGO
(2023), SUMMIT NANOTEC (2023), MINERA CANDELARIA (2023), CMP (2024), SQM NITRATOS
(2024), SQM LITIO (2024).

## Datos editables (placeholders)

- **Estadísticas** (contadores): buscar `data-count` en `index.html` y cambiar los
  valores placeholder (`20`, `30`, `500`, `5000`).
- **Detalles de servicios**: el contenido de los acordeones proviene del sitio
  original y es real; ajustar si cambian los servicios.
- **Datos de contacto**: email `contacto@e-clip.cl` y teléfono `+569 8159 0809`,
  en la sección de contacto.
- **Colores y tipografía**: variables CSS al inicio del `<style>` (`--teal`, `--lime`,
  `--petrol`, etc.). Hay tema claro y oscuro (el oscuro responde a la preferencia del
  sistema del visitante).
- **Hero**: el mock del "Informe de Prensa Diario" (`.hero-visual`) puede
  reemplazarse por una captura real del producto.

---
Rediseño de e-clip.cloud.
