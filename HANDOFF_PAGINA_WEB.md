# Casa Edel — Contexto para armar la página web propia (catálogo + carrito a WhatsApp)

Documento de traspaso desde el chat donde se armó la tienda en Tienda Nube. Está pensado para que un chat nuevo sepa con qué se encuentra. Autor del pedido: Tiago (tiago.cj60@gmail.com, Argentina, habla en español).

## 1. El negocio
- **Casa Edel**: casa de electricidad / ferretería. Tienda actual: `electricidadcasaedel.mitiendanube.com` (plan Pro).
- El sistema de gestión se llama **Alquimia**. Su código de artículo (`COD_ART`) es el "código de alquimia"; el SKU que aparece en la descripción de cada producto de la tienda es ese código u otro del proveedor (a veces difieren levemente entre planilla y tienda).
- Los artículos del sistema se agrupan por familia, pero familias y marcas muchas veces no coinciden. Hay códigos raros para avisos internos que no son productos.

## 2. Qué quiere ahora
Una **web propia desde cero** (no Tienda Nube) que:
1. Muestre el catálogo con fotos, precios y variantes.
2. Tenga un **carrito**; al finalizar arma un mensaje con el detalle y el total y **abre WhatsApp** con ese texto ya escrito, dirigido a **uno de los vendedores**.
3. Se pueda **mantener con una planilla** (Google Sheets) que Tiago o un empleado editen, y también pidiéndoselo a Claude. Las dos vías a la vez.
4. Se vea **profesional y funcione bien en celular**.
5. Hosting: **lo decide Claude**; la propuesta es sitio estático gratis (GitHub Pages sobre este repo, o equivalente), con link propio y dominio propio opcional más adelante.

Sin pagos online, sin cálculo de envíos, sin seguimiento de pedidos: el cierre es por WhatsApp.

## 3. Alcance inicial: solo lo más vendido
- Arrancar con los **~1.500 artículos del ranking de más vendidos con todas sus variantes**, más las marcas nuevas (Macroled, Jadever, King, Chint y las del grupo Coresa). Todo lo demás se oculta aunque tenga foto.
- Ranking: `Articulos_mas_vendidos_Casa_Edel_.xlsx` (si el chat nuevo no lo tiene, pedírselo a Tiago).
- Los productos fuera del ranking **no se borran**, se ocultan.
- **Cables**: se muestran las dos versiones: **rollo de 100 m** (el metro sale más barato) y **por metro cortado** (un poco más caro). Lo mismo para casos similares.
- Lo que más sale: cables unipolares (todas las medidas), TPR, subterráneo, paralelos, cajas de chapa/PVC/embutir/paso, caños y accesorios, canales, lámparas (A60, dicro, GU10, GU9, AR111), corrugados, tiras LED 12V/220V y COB, térmicas y disyuntores (Sica, Jeluz, Schneider, GE), todo Sica, llaves Teclastar/Cambre/Jeluz/Macroled, apliques Candil/San Justo, veladores, jabalinas, pipetas y herramientas en general.
- Marcas relevantes: Teclastar (importante, la gente la compra), Sica, Cambre, Jeluz, Schneider, Interelec, JA, Candil, San Justo, Kalop, Genrod (Sistelectric, Tubelectric), grupo Coresa (Jadever, Macroled, Inteck, DKC, Noak, Ronin, Uniview, King, Intek), Ferretera como proveedor (Bosch, Tekbond, Duke, Delta, etc.).
- Casa Edel **ya no vende Plasnavi** ni fichas industriales Kalop (ocultas). Los "PQ Armado … S/T" (combos internos de Teclastar) **no se publican**.

## 4. Precios
- **Precio en la web = precio de lista con 20% de descuento** (en mostrador aplican 25/30/35%, pero el 20% cubre costos de IA y Tienda Nube).
- El **10% extra por pago en efectivo** NO va en los precios: se menciona/configura aparte.
- Lista cruda del sistema: `2026.10.09_LISTA_DE_PRECIOS_1.xlsx`. Planilla ya limpia e importada a Tienda Nube: `Planilla_Tienda_nube_15-10-26.csv` (8.064 productos, 12 rubros).
- Categorías: pocas, legibles y bien organizadas.

## 5. Fotos (importante: cómo está ordenado)
Todas las fotos viven en el repositorio público **`TiagoJobson25/fotos-casa-edel`** (rama `main`). Carpetas por marca/tema:
`ag, bael, baw, bulit, cables, cambre, candil, chapa, chint, commax, conextube, elent, faltantes, ferre, genrod, genrod_tab, inteck, interelec, ja, jadever, jeluz, kalop, king, macroled, rbc, sanjusto, sanjusto2, schneider, selene, sica, suprabond, teclastar, weidmuller, zoloda`.
- **`faltantes/`** (111 fotos): las que Tiago fue mandando por el chat, producto por producto, y que se normalizaron y subieron. Los nombres son descriptivos (ej. `tarugo-comun.jpg`, `cinta-python.jpg`).
- Resto de carpetas: fotos sacadas de catálogos PDF de cada marca; muchas se nombran por código de artículo (ej. `sica/374018.jpg`).
- **Normalización**: JPG 1000×1000, fondo blanco (producto centrado, margen ~40 px). Excepciones conocidas: algunas con fondo gris claro (cinta Richi, pasa pared), una con marca de agua "Valdesoco" (cinta 3M 175) y otra de "Ferretería Santa María" (zapatilla Richi 5 tomas).
- **Regla de reutilización**: una misma foto para variantes del mismo tipo (térmicas según polos, cuplas, uniones, conectores, curvas, grampas, medidas distintas de un mismo producto, mismo modelo en otro color). El nombre del producto aclara la medida/color.
- Fotos de Tacsa: están además en un Excel de Drive con links; se prefieren esas (mejor calidad) aun donde ya había otra.
- URL directa de una foto: `https://raw.githubusercontent.com/TiagoJobson25/fotos-casa-edel/main/<carpeta>/<archivo>.jpg`

### ⚠️ Lo que NO está resuelto: relación producto ↔ foto
El repositorio **no tiene un índice** que diga qué foto va con qué producto. Esa relación hoy está en Tienda Nube (cada producto tiene su imagen cargada). Para la web nueva hay que reconstruirla. Opciones, de mejor a peor:
1. Exportar desde el admin de Tienda Nube la planilla de productos con **URLs de imágenes** y, a partir de ahí, generar el índice (la CDN de Tienda Nube también sirve las fotos, pero conviene copiarlas al hosting propio para no depender de la tienda).
2. Releer cada producto público de la tienda y extraer su imagen.
3. Cruzar por código de artículo / nombre de archivo (funciona en las carpetas por código, no en `faltantes/`).
Hay que decidirlo al arrancar y validar con una muestra antes de generar todo.

## 6. Arquitectura propuesta
- **Fuente de verdad: una Google Sheet** con una fila por producto/variante: código, nombre, marca, categoría/subcategoría, precio (ya con el 20%), unidad (u / m / rollo), variante, foto (ruta relativa), stock (opcional), `visible` (sí/no), orden.
- La web lee esa planilla al cargar (publicada como CSV). Cambios tardan unos minutos en verse: aceptable.
- Sitio estático: HTML/CSS/JS (sin servidor). Búsqueda y filtros del lado del cliente (por texto, categoría, marca). Carrito guardado en el navegador. Botón final → `https://wa.me/<numero>?text=<pedido codificado>`.
- Los vendedores: Tiago debe pasar nombres y números; definir si el cliente elige vendedor o se asigna uno.
- SEO básico (títulos, descripciones, páginas por categoría) para no perder visibilidad frente a Tienda Nube.
- Mantener Tienda Nube como respaldo/ordenador de datos mientras tanto; no se abandona lo cargado.

## 7. Lo que hay que preguntarle a Tiago al arrancar
- Números y nombres de los vendedores; cómo se reparte el pedido.
- Estilo: colores, logo, alguna web que le guste.
- Dominio propio (opcional).
- Confirmar el ranking y la lista de precios más recientes.
- Si quiere mostrar stock o solo "consultar disponibilidad".
- Si el 10% de descuento por efectivo se muestra en la web.

## 8. Notas técnicas de lo hecho en el chat anterior
- Las herramientas de Tienda Nube (`update_product`, `search_products`, `list_products`) **no devuelven la lista de imágenes** al leer; solo la devuelven al actualizar. `update_product(images=[...])` **reemplaza** las imágenes existentes.
- El servidor de Tienda Nube descarga bien las URLs `raw.githubusercontent.com` del repo.
- El contenedor de trabajo no accede a Drive ni a sitios fuera de una lista permitida (sí a GitHub y a los registros de paquetes).
- Pendientes menores de la tienda actual: fotos de Genrod, Cinta LED F220, repartidores Zoloda de 7 y 15, algunos módulos Candil/Genrod/Nera/RBC, y la configuración del 10% por efectivo.
