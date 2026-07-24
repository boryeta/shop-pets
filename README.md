# shop-pets — Tienda Shopify + landings convertibles

Este repositorio conecta el **tema de Shopify** de la tienda con GitHub. Desde
aquí se editan las secciones y plantillas del tema, y Shopify sincroniza los
cambios automáticamente al tema de la tienda.

El objetivo principal: poder pasar la **URL de un producto** y generar una
**landing altamente convertible** para ese producto, sobre el tema real de la
tienda.

---

## 🔒 Seguridad primero

- **Nunca** se comparte usuario/contraseña de Shopify en este repo ni en el chat.
- La conexión se hace por la **integración oficial GitHub de Shopify** (no requiere contraseña).
- Todo el trabajo se hace sobre **código del tema**, revisable en cada commit.

---

## 1. Conectar el tema de Shopify a este repo (una sola vez)

Se puede hacer desde el navegador del móvil:

1. Entra a tu **Shopify Admin** → **Online Store** → **Themes**.
2. En **Add theme** (o el menú `···` de un tema) elige **Connect from GitHub**.
3. Autoriza la app de Shopify en GitHub si te lo pide.
4. Selecciona:
   - **Repositorio:** `boryeta/shop-pets`
   - **Rama (branch):** `claude/shopify-mobile-account-access-ryj20x`
5. Confirma. Shopify **añadirá los archivos del tema** a esta rama.

> Al conectar una rama sin archivos de tema, Shopify sube tu tema actual a la
> rama. A partir de ahí, cada push a la rama se refleja en ese tema.

**Recomendación:** conecta primero una **copia/duplicado** de tu tema (no el
tema en vivo) para probar los cambios con tranquilidad antes de publicarlos.

---

## 2. Flujo para crear una landing de un producto

1. Me pasas la **URL del producto**, por ejemplo:
   `https://tu-tienda.myshopify.com/products/nombre-del-producto`
2. Leo los datos públicos del producto desde `.../products/nombre.json`
   (título, precio, imágenes, variantes, descripción).
3. Genero/actualizo la plantilla y secciones de la landing en el tema.
4. Hago push a la rama y Shopify sincroniza el cambio.
5. Tú revisas la landing en la vista previa del tema y publicas cuando quieras.

### Qué incluye una landing convertible (checklist de diseño)

- **Hero** claro: propuesta de valor + imagen del producto + CTA visible.
- **Prueba social**: reseñas, valoraciones, "X clientes".
- **Beneficios** (no solo características) con iconos.
- **Galería** del producto y detalles ampliables.
- **Bloque de confianza**: envíos, garantía, devoluciones, pagos seguros.
- **FAQ** para resolver objeciones.
- **CTA repetido** (sticky en móvil) que va directo al checkout.
- **Optimización móvil** primero (la mayoría del tráfico es móvil).

---

## Plantilla de landing incluida: `product.landing`

Ya hay una **landing de conversión lista** para producto único (pensada para la
snuffle mat / alfombra olfativa, y reutilizable para cualquier producto).

**Cómo usarla en Shopify:**

1. Crea el producto en Shopify (o impórtalo desde AliExpress con **DSers** o **CJ**).
   Sube buenas imágenes, pon el precio y el **precio comparado** (para mostrar el
   descuento tachado).
2. En el producto → **Theme template** → elige **`landing`**.
3. Abre el **editor de temas** (Customize) sobre ese producto para ajustar textos,
   reseñas, FAQ, garantía y colores. Todo es editable, sin tocar código.

**Qué incluye la landing (en este orden):**

- Caja de compra real de Dawn (galería, variantes, cantidad, **Add to cart** y
  checkout dinámico) + valoración en estrellas.
- **Barra de confianza** (envío, pago seguro, devoluciones).
- **Beneficios** (problema → solución) con iconos.
- **Cómo funciona** en 3 pasos.
- **Reseñas** con estrellas.
- **Garantía 30 días + CTA** que lleva al botón de compra.
- **FAQ** desplegable (rebate de objeciones).
- Productos relacionados.
- **Barra de compra fija en móvil** (sticky) que aparece al hacer scroll.

**Secciones nuevas** (todas con el prefijo `Landing ·` en el editor):
`landing-trust-bar`, `landing-benefits`, `landing-steps`,
`landing-testimonials`, `landing-guarantee`, `landing-faq`,
`landing-sticky-atc`, y el snippet `landing-icon`.

> Los textos vienen rellenos con copy orientado a conversión para la snuffle mat.
> El precio, título e imágenes salen del **producto de Shopify**, no están escritos
> en el código.

## Modo mono-producto: la home ES la landing

La página de inicio (`templates/index.json`) se ha convertido en la **landing
directa de un solo producto**. Al entrar al dominio, el visitante cae en la
página de venta (sin catálogo, sin home genérica).

**Para activarlo:**

1. En el **editor de temas** (Customize) sobre la **Home page**, abre la sección
   **"Producto destacado"** y en **Producto** elige tu snuffle mat.
2. Abre la sección **"Landing · Barra compra móvil"** y selecciona el **mismo
   producto** (para que la barra fija muestre precio y botón correctos).
3. Guarda. La home ya vende ese producto directamente.

**Opcional — esconder navegación para maximizar conversión:**

- Header: deja el menú vacío o reduce enlaces (Customize → Header).
- Footer: quita menús innecesarios y deja solo enlaces legales (aviso legal,
  privacidad, envíos, devoluciones).

> Sigue existiendo también la plantilla `product.landing` por si algún día
> quieres una página de producto aparte además de la home.

## Estructura

Cuando el tema esté conectado, aparecerán las carpetas estándar de Shopify
(`sections/`, `templates/`, `snippets/`, `assets/`, `config/`, `locales/`,
`layout/`). Las landings vivirán como plantillas de producto/página dedicadas
para no afectar al resto de la tienda.
