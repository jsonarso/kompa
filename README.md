# KOMPA · Coming Soon

Página "Muy pronto" de KOMPA (brazaletes modulares coleccionables, Costa Rica). Sitio estático de una sola página, sin build.

- Tipografía: Montserrat (autoalojada). Colores y logo según el Libro de Marca 2026.
- Archivos: `public/index.html`, `public/assets/`, `public/_headers`, `wrangler.jsonc`.

## Despliegue en Cloudflare (Workers con assets estáticos)
El sitio vive en `public/` y `wrangler.jsonc` apunta a esa carpeta.
1. Workers & Pages → Create → conectar este repositorio.
2. Project name: `kompa`. Build command: *(vacío)*. Deploy command: `npx wrangler deploy`.
3. Deploy. Cada push a `main` redespliega.

## Editar contactos
Enlaces de Instagram en `public/index.html` (según el libro de marca: @KOMPA.CR, KOMPA.cr, somoskompa@gmail.com).
