# Cómo se actualizan las escalas del monotributo

La página lee `escalas.json` al abrir. Para incorporar una nueva vigencia de ARCA
(normalmente desde el 1 de febrero y el 1 de agosto) **no hace falta tocar `index.html`**:

1. Agregar al final de `vigencias` una entrada con:
   - `d`: fecha desde (YYYY-MM-DD), `h`: fecha hasta.
   - `ing`: 11 topes de ingresos brutos anuales, categorías A..K, en orden.
   - `alq`: 11 topes de alquileres devengados anuales.
   - `cs`: 11 cuotas mensuales totales para servicios; `cb`: 11 para venta de bienes.
2. Cerrar la vigencia anterior: su `h` debe ser el día previo al nuevo `d`.
3. Actualizar `actualizado` con la fecha del cambio y hacer commit a `main`.
   GitHub Pages republica solo en un minuto.

Validaciones que hace la página antes de aceptar el archivo: `vigencias` es una lista,
cada entrada tiene `d`, `h` y 11 valores en `ing`. Si el archivo falla, usa los valores
embebidos en `index.html` y lo indica en el pie de página.

Fuente oficial: https://www.arca.gob.ar/monotributo/categorias.asp
