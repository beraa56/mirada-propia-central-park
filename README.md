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
`reserva.html`, donde el cliente elige su paquete y paga.

## ⚠️ Pendiente antes de publicar (obligatorio)

`reserva.html` tiene un bloque `CONFIG` al final del archivo (dentro del `<script>`) con
placeholders que **hay que reemplazar** antes de mandar el link a clientes, o los botones
de pago no van a funcionar:

- `CONFIG.stripeLinks` — necesitas crear 4 Payment Links en tu Dashboard de Stripe
  (Stripe → Payment Links → Crear), uno por cada monto posible: **350, 435, 500 y 585**
  (los dos últimos son con la edición Fine Art incluida). Pega cada URL en su campo.
- `CONFIG.paypalUser` — tu usuario de PayPal.Me (si no lo tienes, se crea gratis en
  [paypal.me](https://www.paypal.me)). El monto se agrega automáticamente al link según
  el paquete que elija el cliente.
- `CONFIG.zelle.contact` — el email o teléfono asociado a tu cuenta de Zelle (el mismo
  que usarías para recibir una transferencia).
- `CONFIG.notifyEmail` — el correo donde quieres recibir el aviso de "ya pagué" que manda
  el botón de Zelle.

Mientras estos campos digan "PEGA_AQUI...", "TU_USUARIO..." o "PENDIENTE...", los botones
muestran una alerta al cliente en vez de dejarlo pagar — es intencional, para que no se
publique por error sin configurar.

## Pendiente antes de publicar (del taller)

- Confirmar con Central Park Conservancy (film@centralparknyc.org) si la restricción de
  fin de semana aplica a un grupo pequeño de fotografía fija — el 3 de octubre 2026 es sábado.
  Por ahora el texto en `index.html` (sección `.pricing`) sigue diciendo "en trámite de
  permiso oficial".
- Una vez confirmado el permiso, actualizar esa frase por "permiso oficial tramitado".
- Reemplazar los testimonios de ejemplo (`.testimonials` en `index.html`) si se suman más alumnas.

## Cómo publicarla (GitHub Pages)

1. `git init` en esta carpeta (si aún no es un repositorio).
2. Crear un repositorio en GitHub (con `gh repo create` o manualmente en github.com) y
   subir el contenido (`git push`).
3. En GitHub → Settings → Pages, activar Pages apuntando a la rama principal, carpeta raíz.
4. El link queda tipo `https://<usuario>.github.io/<repositorio>/` — ese es el que se
   manda a los clientes.

## Fuentes usadas

- Playfair Display (encabezados)
- Parisienne (acentos tipo cursiva/script)
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
