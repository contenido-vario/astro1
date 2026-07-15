# Publicación de sitio estático de Astro en Github
## (prueba)

Hay que agregar al archivo `astro.config.mjs` las líneas con los parámetros `site` y `base`: 

```js
// @ts-check
import { defineConfig } from 'astro/config';
import tailwindcss from '@tailwindcss/vite';

// https://astro.build/config
export default defineConfig({
  vite: {
    base: '/astro1/', // <-- Para el plugin de Vite/Tailwind
    plugins: [tailwindcss()]
  },

  // Para publicar en Pages de Github Astro Estático
  site: 'https://contenido-vario.github.io', // <-- sin barra final
  base: '/astro1/',
});
```
### Ver el site en local

Como se agregó la propiedad `base: '/astro1/'`, Astro ahora espera que toda la página web funcione dentro de esa subcarpeta. Por eso, en lugar de buscar tu web en **localhost:4321**, ahora tienes que verla en:

👉 **http://localhost:4321/astro1/**


### ¿Qué carpeta exactamente se sube?

- Debes entrar a la carpeta llamada `dist` que se acaba de generar.
- Arrastra todo el contenido que está DENTRO de `dist` (archivos como `index.html`, y carpetas como `_astro`) directamente a la ventana de tu repositorio en GitHub.
- _Nota importante:_ No arrastres la carpeta `dist` como tal; arrastra lo que hay dentro de ella para que el archivo `index.html` quede en la raíz de tu repositorio de GitHub.

## Configurar GitHub Pages

1. Ve a tu repositorio en la web de GitHub.
2. Entra en Settings (Configuración) -> Pages.
3. En _Source_, asegúrate de que esté seleccionado "Deploy from a branch".
4. Abajo, en _Branch_, selecciona tu rama (normalmente **`main`** o `master`) y en la carpeta deja seleccionado `/ (root)`. Haz clic en `Save`.
