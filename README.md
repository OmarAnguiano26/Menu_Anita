# ¿Qué se te antoja, amor? — Menús sorpresa

Página web sencilla para que tu novia elija primero el tipo de comida y después explore varios menús numerados con fotografías. No pregunta presupuesto ni modalidad del plan. Cuando elige una opción, envía la selección a tu correo mediante Formspree.

## Archivos
- `index.html`: diseño, categorías y lógica de selección.
- `images/`: carpeta donde debes guardar las fotos de los menús.
- No necesita instalar paquetes.

## 1. Abrir en VS Code
1. Descomprime el ZIP.
2. Abre VS Code y elige **File → Open Folder…** (Archivo → Abrir carpeta).
3. Selecciona la carpeta `antojito-game`.
4. Opcional: instala la extensión **Live Server** de Ritwick Dey. Abre `index.html` y presiona **Go Live** para probarlo en el navegador.

## 2. Agregar fotos de menús
1. Guarda las fotos dentro de la carpeta `images`.
2. Usa nombres sencillos, sin espacios ni acentos, por ejemplo `asiatica-opcion1-menu1.jpg`.
3. En `index.html`, busca `const MENUS = {`.
4. Cada categoría contiene opciones. Cada opción tiene `internalName`, `subtitle` e `images`.
5. En `images`, cambia `src` para que coincida exactamente con el nombre del archivo. Por ejemplo:

```js
{
  internalName: "Restaurante que solo tú identificas",
  subtitle: "Menú para explorar",
  images: [
    { src: "images/asiatica-opcion1-menu1.jpg", caption: "Menú · página 1" },
    { src: "images/asiatica-opcion1-menu2.jpg", caption: "Menú · página 2" }
  ]
}
```

Puedes poner varias fotos por opción, por ejemplo una foto por página del menú. Cuando ella pulse **Ver menú e imágenes**, las fotos se desplegarán. Si una imagen todavía no existe, aparecerá un aviso con la ruta que debes agregar.

## 3. Añadir o quitar restaurantes
Dentro de `MENUS`, cada objeto entre llaves `{ ... }` representa una opción numerada. Copia un objeto para agregar otra opción, cambia su `internalName` y sus imágenes, y separa objetos con una coma. El número se genera automáticamente según el orden: Opción 1, Opción 2, Opción 3…

Las categorías actuales son `asiatica`, `mexicana`, `italiana`, `hamburguesas` y `otra`. Puedes cambiar sus nombres visibles en `FOOD_TYPES`. Si creas una categoría nueva, añade también una lista con la misma clave dentro de `MENUS`.

**Privacidad:** `internalName` no aparece en la pantalla de selección, pero está escrito en el código de la página y puede inspeccionarse si el sitio se publica en internet. Es una etiqueta para ayudarte a identificar la opción en el correo, no un secreto seguro.

## 4. Configurar el correo
1. Entra a https://formspree.io/ y crea un formulario.
2. Copia el endpoint que te proporciona, parecido a `https://formspree.io/f/xxxxxxxx`.
3. En `index.html`, reemplaza `TU_ID_AQUI` en esta línea y guarda:

```js
const FORMSPREE_ENDPOINT = "https://formspree.io/f/TU_ID_AQUI";
```

4. Haz una prueba y verifica que el correo llegue. Formspree puede pedirte confirmar el correo receptor; revisa también spam.

## 5. Probar y publicar
- Prueba en el navegador que puedes elegir una categoría, desplegar fotos y seleccionar una opción.
- Para publicar gratis, crea un repositorio en GitHub, sube `index.html` y la carpeta `images/`, y habilita **Settings → Pages**. Sube todas las fotos junto con el HTML para que se vean en el sitio publicado.
- Antes de compartir el enlace, confirma que las imágenes cargan desde el teléfono y que Formspree recibe la selección.
