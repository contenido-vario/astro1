# Publicación de sitio estático de Astro en Github
## (prueba)

Hay que agregar al archivo `astro.config.mjs` las líneas con los parámetros `site` y `base` y cambiar la carpeta de `_astro` por `assets`: 

```js
// @ts-check
import { defineConfig } from 'astro/config';
import tailwindcss from '@tailwindcss/vite';

// https://astro.build
export default defineConfig({
  vite: {
    plugins: [tailwindcss()]
  },

// Añade este bloque aquí abajo
  build: {
    assets: 'assets' // Cambia la carpeta '_astro' por 'assets'
  },

  // Configuración de producción para GitHub Pages
  site: 'https://contenido-vario.github.io',
  
  base: '/astro1/',
});


```

### ¿Qué carpeta exactamente se sube?

- Se debe subir la carpeta llamada `dist` que se genera con `pnpm build`.
- Arrastra todo el contenido que está DENTRO de `dist` (archivos como `index.html`, y carpetas como `_astro`) directamente a la ventana de tu repositorio en GitHub.
- _Nota importante:_ No arrastres la carpeta `dist` como tal; arrastra lo que hay dentro de ella para que el archivo `index.html` quede en la raíz de tu repositorio de GitHub.

### Configurar GitHub Pages

1. Ve a tu repositorio en la web de GitHub.
2. Entra en Settings (Configuración) -> Pages.
3. En _Source_, asegúrate de que esté seleccionado "Deploy from a branch".
4. Abajo, en _Branch_, selecciona tu rama (normalmente **`main`** o `master`) y en la carpeta deja seleccionado `/ (root)`. Haz clic en `Save`.

#### Para revisar en local ahora se escribe [localhost:4321/astro1/](localhost:4321/astro1/) al usar `pnpm run dev`
