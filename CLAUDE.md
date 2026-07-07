# CLAUDE.md — Contexto del proyecto e-clip

Guía para trabajar este repo. Léela antes de hacer cambios. Para detalle orientado a
personas ver también `README.md`.

## Qué es

Sitio web **single-page estático** para **e-clip**, empresa chilena de monitoreo y
análisis de prensa (clipping electrónico) para grandes empresas de minería, energía,
puertos e industria. Símbolo de marca: el **camaleón** (adaptabilidad).

- **Es un mockup de presentación, sin backend.** El formulario valida y muestra un
  éxito **simulado**; no envía correos. No hay CMS ni base de datos.
- Público objetivo: corporativo/serio. Tono profesional tipo SaaS/consultora de datos.
- En vivo: https://cons091.github.io/e-clip/ · Repo: https://github.com/cons091/e-clip

## Stack y estructura

- **HTML + CSS + JS puro, sin build, sin dependencias, sin frameworks.**
- **`index.html` es el sitio completo**: el CSS va en un `<style>` al inicio y el JS en
  un `<script>` al final del mismo archivo. No hay archivos .css ni .js separados.
- `assets/` → marca e-clip (`e-clip-icon.png`, `e-clip-color.png`, `e-clip-blanco.png`).
- `logos/` → logos de clientes (ver sección Logos).
- `.claude/` → config local del entorno; está en `.gitignore`, no la subas.

> No introduzcas Tailwind por CDN, React, ni ningún recurso externo. El sitio debe
> seguir siendo 100% autocontenido y offline-capable. Si el usuario pide Tailwind,
> recuerda que el diseño ya está implementado como tokens CSS (variables) equivalentes.

## Secciones (orden fijo)

Hero → Pilares (4 diferenciadores) → Nosotros (Quiénes somos, Filosofía, Misión,
Visión) → Estadísticas (contadores animados) → Servicios (4 tarjetas con acordeón
"Detalles") → Clientes (carrusel infinito) → Contacto (formulario + datos directos).
**No hay footer** (se eliminó a pedido del cliente — no lo vuelvas a agregar salvo
que lo pidan explícitamente).

## Convenciones clave

- **Diseño por tokens CSS**: todos los colores/tipografías son variables en `:root`
  (`--teal`, `--lime`, `--petrol`, `--ink`, etc.). Cambia el token, no valores sueltos.
- **Tema claro y oscuro**: definidos vía `@media (prefers-color-scheme)` y overrides
  `:root[data-theme="light"|"dark"]`. Si tocas colores, actualiza AMBOS temas.
- **Paleta = marca camaleón**: verde lima `--lime` (#CDD62B, del logo real) + teal
  `--teal` + fondo petróleo oscuro `--petrol`. No la cambies sin pedirlo.
- **Animaciones**: clase `.reveal` (fade/slide al hacer scroll vía IntersectionObserver)
  y contadores `[data-count]`. Respeta `prefers-reduced-motion` (ya implementado).
- **Accesibilidad**: navbar con `aria-*`, focus visible, alt en imágenes. Mantenlo.

## Logos de clientes (importante)

- Se generan por JS desde el array `CLIENTES` en `index.html` (pares `[nombre, año]`).
- Cada logo se busca en `logos/<slug>.<ext>` probando `png, svg, jpg, webp` en orden.
  Si ninguno carga, se muestran las **iniciales** del nombre (fallback automático).
- **slug** = `nombre.normalize("NFD")` sin diacríticos, minúsculas, no-alfanumérico → `-`.
  Ej: `CONSEJO MINERO` → `consejo-minero`; `SURVÍAS` → `survias`; `PARTNER S.A.` →
  `partner-s-a`. Para agregar un logo NO se toca código: se sube el archivo con ese nombre.
- El recuadro del logo es **horizontal** (ancho de tarjeta, alto tope 46px) para que
  los wordmarks anchos (Transelec, BPH…) se lean sin deformarse. Los cuadrados quedan
  centrados. No vuelvas al recuadro cuadrado de 56px.
- **Faltan por subir**: `logos/mantos-copper.png` y `logos/minera-lomas-bayas.png`
  (hoy muestran iniciales). Muchos logos actuales son favicons de Google 128px, de baja
  resolución; lo ideal es reemplazarlos por oficiales.

## Placeholders editables

- **Estadísticas**: valores en `data-count` (`20`, `30`, `500`, `5000`) — son inventados,
  el sitio original no muestra cifras. Cambiar cuando el cliente entregue las reales.
- **Contacto**: `contacto@e-clip.cl` / `+569 8159 0809`.
- **Servicios**: el texto de los acordeones "Detalles" es real (extraído del sitio
  original). Las 4 tarjetas: Clipping Electrónico, Informes de Prensa, Monitoreo de
  Redes Sociales, Otros Servicios.

## Flujo de trabajo

1. Editar `index.html` (o `logos/`, `assets/`).
2. Probar local con un servidor HTTP (`npx http-server . -p 8321 -c-1`), no con `file://`.
   Verificar en tema claro y oscuro. La sección Clientes usa `loading="lazy"`: hay que
   scrollear hasta ella para que carguen los logos.
3. Commit + push a `main`. GitHub Pages redepliega solo en ~1 min.

### Git / push

- El remoto `origin` NO guarda token (a propósito). El `push` pide credenciales:
  usar un Personal Access Token de la cuenta **`cons091`**.
- **Nunca** escribas un token en archivos, commits, ni en la URL del remoto guardado.
  Si necesitas usarlo para un push puntual, hazlo en una URL efímera y no la persistas.
- Mensajes de commit en español, concisos, describiendo el cambio.

## Cosas que NO hacer

- No agregar dependencias externas / CDNs / build tools.
- No re-agregar el footer sin que lo pidan.
- No cambiar la paleta ni la estructura de secciones sin instrucción.
- No guardar secretos/tokens en el repo.
- No convertir el mockup en app con backend salvo que se pida (sería nuevo alcance).
