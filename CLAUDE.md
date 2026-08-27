# Mirada Propia — Retrato Fine Art en Central Park

Landing page + página de reserva/pago para un taller presencial de fotografía de
Bernardita Aguirre (3 de octubre 2026, Central Park, Nueva York). Sitio estático,
sin backend, publicado en GitHub Pages con dominio propio.

## URLs

- **Sitio en vivo**: https://cursoretratofineart.bernarditaaguirre.com (dominio propio,
  subdominio de `bernarditaaguirre.com` — el dominio raíz es su sitio principal aparte,
  no tocar).
- **Repo**: https://github.com/beraa56/mirada-propia-central-park (público — necesario
  para GitHub Pages gratis; no hay secretos en el código, ver sección Seguridad).
- El link viejo `beraa56.github.io/mirada-propia-central-park/` redirige automáticamente
  al dominio propio (301), es normal.

## Estructura

```
index.html     → landing principal
reserva.html   → página de reserva/pago (Stripe, PayPal, Zelle, depósito USD 200)
styles.css     → CSS compartido entre ambas páginas
favicon.svg    → ícono de la pestaña (monograma "MP")
CNAME          → dominio propio para GitHub Pages (no borrar)
.nojekyll      → OBLIGATORIO: sin este archivo, GitHub Pages usa Jekyll y esconde
                 cualquier archivo/carpeta que empiece con "_" (varias fotos se llaman
                 así, ej. `_DSC0875-...`) — causa fotos rotas en producción sin avisar
                 en local. Si algún día vuelve a fallar una foto solo en el link
                 publicado (no en local), esto es lo primero a revisar.
images/        → fotos usadas en el sitio, ya optimizadas para web (300-500 KB c/u)
copy-referencia.md → copy de la landing en texto plano
```

## Datos clave del taller

- Fecha: 3 de octubre 2026, 2:00 PM — Central Park, NY — 3 horas — 10 a 12 fotógrafos
- Precio: USD 350 early bird (hasta 20 sept) / USD 435 regular
- Edición Fine Art (upsell, por Zoom): + USD 150
- Depósito para reservar (alternativa al pago completo): USD 200
- Política de cancelación: no reembolsable, transferible a otro alumno que el cliente proponga
- Contacto: WhatsApp +56 9 9238 8751 · hola@bernarditaaguirre.com
- Modelos: personas reales (no se usa la palabra "modelos" ni se asume que sea una familia —
  Bernardita pidió específicamente evitar ambas cosas porque no sabe aún quién modelará)

## Pagos (`reserva.html`)

Todo el `CONFIG` (Stripe, PayPal, Zelle, WhatsApp) está cargado con datos reales al final
del `<script>` de `reserva.html`. El cliente elige paquete (early bird/regular + addon
opcional) y modo de pago (completo o depósito $200); el JS recalcula el total y actualiza
los 3 botones de pago en vivo. No hay backend: Stripe Payment Links y PayPal.Me hacen todo
el cobro fuera del sitio (el sitio nunca toca datos de tarjeta). Zelle es manual — no hay
forma de verificar automáticamente que un pago por Zelle sea real, así que Bernardita debe
confirmar en su banco antes de dar una reserva por confirmada.

Si hay que agregar/cambiar un monto: actualizar `CONFIG.stripeLinks` (crear el Payment Link
nuevo en el Dashboard de Stripe primero) y la lógica de `updateTotal()`.

## Seguridad

Auditado a fondo (ver historial de commits "Revisión de seguridad..."): sitio 100%
estático, sin formularios, sin secretos en el código ni en el historial de git. El riesgo
real no está en el código sino en el acceso a las cuentas que lo controlan — Bernardita
debería tener 2FA activado en GitHub, Stripe, PayPal y Squarespace, y el "Domain Lock"
activado en Squarespace. Detalle completo en el `README.md`, sección Seguridad.

## Diseño

- Colores: `--terracotta:#B23A28` `--gold:#B8945F` `--cream:#FAF6F1` `--ink:#232323`
  `--deep:#E5D5C6` (paleta completa en `README.md`)
- Fuentes: Playfair Display (encabezados + su itálica para acentos tipo script — **no**
  usar una fuente script separada, ya se probó y Bernardita prefirió la itálica de
  Playfair) + Inter (cuerpo), vía Google Fonts
- Logo: `images/logo-mark-white.png` / `logo-mark-ink.png` — el ícono de firma cursiva
  "B" solamente (sin el wordmark "bernarditaaguirre" al lado — en el logo real va abajo,
  no al costado, así que en el nav (espacio horizontal angosto) se dejó solo el ícono)
- Hero: en **desktop** el texto va superpuesto sobre la foto (sin caja, colores
  crema/dorado con sombra + "chips" con fondo oscuro para los datos de fecha/lugar). En
  **mobile** es distinto a propósito: foto corta arriba (solo título) + bloque de info en
  fondo sólido oscuro debajo — se intentó varias veces mantener todo superpuesto en mobile
  y siempre quedaba con texto encima de las caras o ilegible: no volver a esa idea sin
  verificar antes con capturas reales de celular.

## Cosas para tener en cuenta

- **`images/` tiene archivos que aparecen y desaparecen solos** — todo indica un sync de
  iCloud Drive activo en la carpeta `Documents`. Varias veces fotos que el sitio usaba se
  borraron solas del disco (recuperables desde git con `git restore`, ya pasó y se
  resolvió). Los archivos "en bruto" sin editar/optimizar (varios MB cada uno, nombres
  como `_DSC0875-Editar-Editar.jpg`, `niños otoño.jpg`, etc.) están en `images/` pero
  **no están en git a propósito** — son el material fuente del que se sacaron las versiones
  optimizadas que sí usa el sitio (mismas fotos, comprimidas a ~300-500 KB con
  `PIL`/Pillow antes de cada commit). Si una de esas fuentes desaparece del disco, no hay
  respaldo — recomendar a Bernardita que las respalde aparte si le importan.
- Antes de cualquier cambio visual, probar local con `open index.html` /
  `open reserva.html` — recién después de confirmar visualmente hacer commit + push.
- Después de cada `git push`, GitHub Pages tarda ~1-2 min en reconstruir. Verificar con
  `gh api repos/beraa56/mirada-propia-central-park/pages --jq .status` hasta que diga
  `"built"` antes de avisarle a Bernardita que ya está publicado.
- Bernardita es de Chile — usar español neutro/chileno (tú, no "vos"), evitar modismos
  argentinos.
- Pendiente: reemplazar los testimonios de ejemplo (`.testimonials` en `index.html`) el
  día que haya testimonios reales de esta edición del taller.
