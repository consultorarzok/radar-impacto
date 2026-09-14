# Radar Impacto — sitio web

Sitio estático (GitHub Pages) para Radar Impacto, en el mismo patrón que
`album-pokemon` y `expojuy-2026`: sin servidor, sin costo de hosting.

- `index.html` — portada + vista de nota, todo client-side (una sola página, ruteo por `#hash`).
- `data/noticias.json` — las notas. Esto es lo único que el workflow de n8n
  va a tener que escribir (vía GitHub API) para publicar una nota nueva:
  agrega un objeto al array y GitHub Pages reconstruye solo.

## Estado actual: prototipo con notas de ejemplo

Las notas de `data/noticias.json` son de ejemplo (marcadas como tal en el
sitio) para poder revisar diseño y estructura antes de conectar la carga
automática desde el workflow real. Todavía no hay ningún paso en n8n que
escriba en este archivo.

## Próximo paso (cuando se apruebe el diseño)

Agregar al workflow de Radar Impacto un nodo redactor adicional que, a
diferencia del copy corto de Facebook/Instagram, genere el cuerpo largo
para la web (varios párrafos), y un paso que haga commit de la nota nueva
a este repo vía GitHub API (Contents API: leer `data/noticias.json`,
agregar el objeto, volver a escribir el archivo).

## Dominio propio

Cuando se compre el dominio: agregar un archivo `CNAME` en la raíz con el
dominio elegido, y apuntar los DNS (A records a las IPs de GitHub Pages,
o CNAME si es subdominio) — GitHub Pages sirve el sitio en HTTPS solo.
