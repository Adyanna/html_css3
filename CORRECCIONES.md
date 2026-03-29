Correcciones recomendadas (estructura y semántica)
===================================================

Contexto: revisión rápida de `login.html` y estilos asociados. No se modificaron textos/acentos; los ajustes aquí son sobre HTML semántico, estructura y enlaces.

1) Navegación y encabezado
- `header` sin `nav`: envolver el bloque de enlaces/acciones en un `<nav>` para accesibilidad y roles claros. Archivo: `login.html` (header de la cabecera).
- Botón “Iniciar sesión” debería ser un enlace (`<a href="login.html">`) o un `<button type="button">` dentro de un formulario; hoy es un botón suelto sin destino.

2) Formularios
- Inputs de email sin atributo `name`; agrega `name="email"` para que los valores se envíen. Archivo: `login.html`, ambos formularios.
- Tipo de input usa `type="Email"` (E mayúscula). Debe ser `type="email"` (HTML es case-insensitive pero es buena práctica). Ambos formularios.
- Falta `aria-label` o `<label for>` asociado a cada input para accesibilidad; añade un label visible u oculto. Ambos formularios.

3) Jerarquía de títulos
- Hay múltiples `<h1>` dentro del carrusel de tendencias (los números). Sustituirlos por `<span>` o `<p>`; reservar `<h1>` para el título principal de la página. Archivo: `login.html`, sección “Tendencias”.
- Verificar orden jerárquico: hay `h1`, luego `h2`/`h3` pero los bloques de motivos usan `h3` dentro de otro `h3` padre; conviene degradarlos a `h4` o usar `<p>`/`strong`.

4) Listados y repetición de tarjetas
- Las tarjetas del carrusel deberían ir en una lista semántica (`<ul><li>`) en vez de divs planos, especialmente porque se desplazan y representan un conjunto ordenado. Archivo: `login.html`, sección “Tendencias”.
- Igual para la sección de motivos: cada motivo puede ser `<article>` dentro de un `<section>` o `<ul><li>`.

5) Preguntas frecuentes (FAQ)
- Cada ítem podría usar `<details><summary>` para accesibilidad en vez de divs con SVG; reduce JavaScript y mejora navegación con teclado. Archivo: `login.html`, sección “preguntasFrecuentes”.
- Los iconos SVG se repiten; añadir `aria-hidden="true"` y texto alternativo con `aria-label` en el contenedor si se mantienen.


6) Imágenes
- Las imágenes del carrusel usan `background-image` sin texto alternativo; si no son decorativas, conviene usar `<img alt="...">` para describir el título/puesto en el ranking. 


7) CSS / overflow
- Asegurar que los contenedores de carrusel tengan `overflow-x: auto` y que el `body` no herede scroll horizontal (ya ajustado en `styles/pages/inicio.css`, aplicar mismo patrón si se replica carrusel aquí).
