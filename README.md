# Mirada Propia — Retrato Fine Art en Central Park

Landing page del taller presencial de 3 horas en Central Park, Nueva York
(Edición Otoño 2026), para fotógrafos profesionales.

## Estructura

```
index.html          → la landing principal (HTML + CSS externo, sin dependencias salvo Google Fonts)
reserva.html         → la página de reserva/pago (Stripe, PayPal, Zelle)
styles.css           → todo el CSS compartido entre las dos páginas
favicon.svg          → ícono de la pestaña (monograma "MP")
images/              → las 12 fotos usadas en la página, en formato normal (jpg/png)
copy-referencia.md   → el copy de la landing en texto plano, por si lo necesitas para otros formatos (email, brochure, redes)
```

## Datos clave ya cargados en la página

- Fecha del taller: 3 de octubre, 2026 — 2:00 PM
- Precio: USD 350 early bird (hasta 20 de septiembre) / USD 435 regular
- Edición Fine Art como upsell: + USD 150
- Cupos: 10–12 fotógrafos
- Modelos: sin costo (gratis)
- Equipo: solo cámaras de mano, sin trípode

Todos los botones de "Reservar mi cupo" / "Quiero mi lugar" de `index.html` llevan a
`reserva.html`, donde el cliente elige su paquete y paga. En `reserva.html` también puede
elegir pagar solo un **depósito de USD 200** para asegurar el cupo (el saldo se paga después),
en vez del pago completo.

Ya cargados y funcionando:
- WhatsApp: +56 9 9238 8751 (botón flotante en ambas páginas y en `reserva.html`).
- Política de cancelación (en `reserva.html`, junto al selector de pago): la reserva no es
  reembolsable, pero se puede transferir a otro alumno que el cliente proponga.
- Pagos: los 5 Payment Links de Stripe (200/350/435/500/585), el usuario de PayPal.Me
  (`bernarditaaguirre`) y el Zelle (`hola@bernarditaaguirre.com`, a nombre de Art & Photo LLC)
  ya están cargados en `CONFIG` dentro de `reserva.html` — los botones de pago funcionan.

## Pendiente antes de publicar

- ~~Confirmar permiso con Central Park Conservancy~~ — ya está resuelto. Se sacó la mención
  del permiso de la sección `.pricing` en `index.html` (ya no hacía falta).
- Reemplazar los testimonios de ejemplo (`.testimonials` en `index.html`) si se suman más alumnas.

## Cómo publicarla (GitHub Pages)

1. `git init` en esta carpeta (si aún no es un repositorio).
2. Crear un repositorio en GitHub (con `gh repo create` o manualmente en github.com) y
   subir el contenido (`git push`).
3. En GitHub → Settings → Pages, activar Pages apuntando a la rama principal, carpeta raíz.
4. El link queda tipo `https://<usuario>.github.io/<repositorio>/` — ese es el que se
   manda a los clientes.

## Fuentes usadas

- Playfair Display (encabezados, y su cursiva/itálica para los acentos tipo script)
- Inter (cuerpo de texto)

Cargadas vía Google Fonts en el `<head>` — si trabajas offline, hay que
descargarlas localmente o el texto caerá a la fuente por defecto del sistema.

## Paleta de marca

```
--terracotta:       #B23A28
--terracotta-light:  #D14E3A
--cream:             #FAF6F1
--cream-dark:        #F4EEE6
--ink:               #232323
--gold:              #B8945F
--deep (secciones claras): #E5D5C6
--deep-dark:                #D6C2AE
```
