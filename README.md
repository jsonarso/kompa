# KOMPA · Sitio Web Oficial (Costa Rica)

Sitio web estático de KOMPA (brazaletes modulares coleccionables para atletas y exploradores en Costa Rica). Desplegado en **Cloudflare Pages / Workers con assets estáticos**, sin paso de compilación pesado (cero dependencias de build).

---

## 📁 Estructura del Proyecto

```text
kompa/
├── .gitignore              # Archivos ignorados por Git (.DS_Store, node_modules, etc.)
├── wrangler.jsonc          # Configuración de despliegue en Cloudflare (apunta a ./public)
├── README.md               # Documentación y guía de desarrollo
└── public/                 # Directorio raíz servido en producción
    ├── index.html          # Página principal / Landing ("Muy pronto" y acceso a herramientas)
    ├── _headers            # Cabeceras HTTP de seguridad y caché en Cloudflare
    ├── assets/             # Recursos estáticos globales compartidos
    │   ├── kompa-logo-blanco.png     # Logo oficial completo (símbolo + tipografía + claim)
    │   ├── kompa-simbolo-blanco.png  # Símbolo oficial KOMPA
    │   ├── hero.webp                 # Fotografía hero de la página principal
    │   ├── og.jpg                    # Imagen para Open Graph / redes sociales
    │   ├── favicon.ico, favicon-32.png, apple-touch-icon.png, icon-512.png
    │   └── fonts/                    # Tipografía Montserrat autoalojada (woff2)
    └── marco/              # Aplicación web: Marco oficial para Instagram Stories (1080×1920)
        ├── index.html      # Estructura de la app de marco y Tailwind CDN
        ├── app.js          # Lógica Canvas 9:16, cámara WebRTC, zoom táctil, exportación
        └── style.css       # Estilos específicos de zonas seguras y controles
```

---

## 🌐 Rutas Activas

- `/` → **Página Principal**: Landing con identidad de marca, llamado a la acción a Instagram y acceso directo a la app de marco.
- `/marco/` → **Marco Oficial de Stories**: Aplicación interactiva donde los atletas encuadran selfies o fotos con el marco oficial KOMPA en 1080×1920 y las comparten a Instagram Stories.

---

## 🎨 Identidad Visual y Tokens (Manual de Marca KOMPA 2026)

- **Tipografía:** Montserrat (pesos `500`, `700`, `800`, `900`).
- **Paleta de Colores:**
  - `KOMPA INK`: `#07111E` (Fondo y contraste)
  - `KOMPA WHITE`: `#FFFFFF` (Wordmark, textos principales)
  - `KOMPA SAND`: `#F4F0E9` (Textos secundarios y acentos suaves)
  - `KOMPA METAL`: `#B5B8B7` (Placas de pulseras)
  - **Acentos de Colección:**
    - Amarillo Meta: `#FFD100`
    - Turquesa Océano: `#38CBC4` / `#2EC4B6`
    - Rosa Vibrante: `#F24E96`
    - Verde Naturaleza: `#2B7A58`
    - Naranja Cumbre: `#F0652D`

---

## 🚀 Guía: Cómo continuar agregando contenido a futuro

1. **Agregar una nueva página o sección:**
   - Para crear una nueva ruta como `/catalogo/` o `/historia/`, crea una carpeta dentro de `public/` (ej: `public/catalogo/index.html`).
   - Cloudflare Pages la servirá automáticamente en esa URL sin configuración adicional.
2. **Agregar nuevas imágenes o recursos:**
   - Coloca siempre los archivos compartidos dentro de `public/assets/`.
   - Haz referencia a ellos mediante rutas relativas (`assets/mi-foto.jpg` desde la raíz o `../assets/mi-foto.jpg` desde subcarpetas).
3. **Probar localmente antes de publicar:**
   ```bash
   python3 -m http.server 8080 --directory public
   # Abre en tu navegador: http://localhost:8080
   ```
4. **Publicar cambios a producción:**
   ```bash
   git add .
   git commit -m "feat: descripción de los cambios"
   git push origin main
   ```
   Cloudflare detectará el push a la rama `main` y desplegará automáticamente en cuestión de segundos.
