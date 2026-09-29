# Plan Aguinaldo — antes de subir

Esta carpeta es el sitio completo. Se sube tal cual a cualquier hosting estático
(Netlify, Vercel, Cloudflare Pages, Hostinger, un `public_html` de cPanel, etc.).
No necesita servidor, base de datos ni build.

```
index.html                 la landing
aviso-de-privacidad.html   borrador legal — hay que completarlo
terminos.html              borrador legal — hay que completarlo
og-image.jpg               1200×630, la imagen que sale al compartir
robots.txt
sitemap.xml
```

---

## 1. Tres reemplazos y ya

Abre los archivos en cualquier editor y usa **Buscar y reemplazar en todos los archivos**.

| # | Busca | Reemplaza por | Dónde aparece |
|---|---|---|---|
| 1 | `TU_CODIGO_DE_PRODUCTO` | el código de tu producto en Hotmart | `index.html` (8 veces) |
| 2 | `TU_DOMINIO.com` | tu dominio final, sin `http://` ni barra final | los 5 archivos |
| 3 | `hola@` | el buzón que vas a leer de verdad | si no quieres usar `hola@` |

Después abre `index.html` y busca el bloque `window.LAUNCH` (está arriba, marcado).
Rellena los dos IDs de medición:

```js
gtmId       : 'GTM-XXXXXXX',        // Google Tag Manager
metaPixelId : '123456789012345',    // Píxel de Meta
```

Si dejas alguno vacío, simplemente no se carga. La página no le pide nada a
Google ni a Meta mientras estén vacíos.

---

## 2. La página te dice si te faltó algo

Abre `index.html` en el navegador y mira la consola (`F12` → Console).

- **Verde** → *"Todo listo para subir."*
- **Rojo** → te lista exactamente qué quedó sin rellenar y qué se rompe por eso.

Ese aviso solo sale en la consola. El visitante nunca lo ve.

---

## 3. Las dos páginas legales necesitan tus datos

`aviso-de-privacidad.html` y `terminos.html` son borradores **completos** pero
**generales**. Los campos que faltan están resaltados en amarillo dentro de la
página, imposibles de pasar por alto:

- Nombre o razón social
- Domicilio fiscal
- Proveedor de hosting
- País / estado y ciudad para la jurisdicción
- Fecha de última actualización

**Que los revise un abogado en tu país antes de publicar.** Yo redacté el
contenido cubriendo lo habitual (datos que se recaban, Hotmart como procesador,
derechos ARCO, garantía de 7 días, límite de responsabilidad, la cláusula de
que esto no es asesoría financiera), pero no es asesoría legal y Hotmart puede
pedirte requisitos concretos para aprobar el producto.

---

## 4. Comprobaciones después de subir

1. **Compartir por WhatsApp** — pégate el enlace a ti mismo. Debe salir la
   tarjeta con la imagen, no un recuadro gris. Si sale gris, usa el
   [depurador de Facebook](https://developers.facebook.com/tools/debug/) y dale
   "Scrape Again".
2. **Un botón de compra** — haz clic y confirma que llega al checkout correcto
   de Hotmart, con tu precio y tu moneda.
3. **El parámetro `sck`** — en la URL del checkout debe aparecer algo como
   `sck=landing_hero_mx`. Eso te dice en el reporte de ventas de Hotmart desde
   qué botón vino cada venta.
4. **La calculadora en el celular** — escribe un monto y comprueba que el
   reparto y la gráfica se actualizan.
5. **HTTPS** — que el candado aparezca. Casi todos los hostings lo dan gratis.

---

## 5. Lo que todavía falta, y no es técnico

La página no tiene **ninguna prueba social**: ni un nombre, ni una cara, ni un
testimonio, ni una línea en primera persona. Para un producto de dinero, de
marca nueva, comprado por impulso, eso es hoy el techo de la conversión.

Cuando tengas material real (tu foto y tu nombre, capturas de conversaciones de
quienes ya lo usaron, o un conteo honesto de planes creados), hay lugar natural
para meterlo junto a la tarjeta de precio.

También sigue pendiente decidir el precio. $119 MXN son ~6 USD para una página
con este nivel de acabado, y el desajuste entre lo que se ve y lo que cuesta
puede estar frenando ventas en lugar de acelerarlas.
