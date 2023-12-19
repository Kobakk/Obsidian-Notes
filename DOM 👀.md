#Noviembre #DOM
La manera en la que estructuramos un documento HTML, y sus ==elementos anidados==.
### ¿Cómo interactuamos con los documentos?
- Una vez cargada la pagina, es decir cargados **todos los elementos del DOM**.
```html
<html>
  <head>
    <script>
      // ejecuta esta función cuando se cargue el documento
      window.onload = function () {
		// crea dinámicamente un par de elementos HTML en una página vacia
        var heading = document.createElement("h1");
        var heading_text = document.createTextNode("el texto que desee");
        heading.appendChild(heading_text);
        document.body.appendChild(heading);
      };
    </script>
  </head>
  <body></body>
</html>
```
Las estructuras de datos mas comunes son: 
- Objeto `document` hace referencia al propio documento.
- La función `element` hace referencia a un nodo del elemento que esta en el documento.
- `nodeList` es una serie de elementos que guardamos en un "array" por ejemplo en una lista HTML con muchos enlaces.
```javascript
// Seleccionar todos los elementos con la clase "item" y obtener un NodeList
const items = document.querySelectorAll(".item");
// Iterar a través de los elementos del NodeList
items.forEach(function(item, index) {
    // Acceder al contenido de cada elemento y modificarlo
    item.textContent = `Nuevo elemento ${index + 1}`;
});
// Agregar un nuevo elemento a la lista
const newListElement = document.createElement("li");
newListElement.textContent = "Elemento Nuevo";
document.querySelector("ul").appendChild(newListElement);
```
- `attribute` nos referimos a un atributo de un objeto.
```javascript
// Seleccionar el elemento con el id "miEnlace"
const enlace = document.getElementById("miEnlace");
// Obtener el valor del atributo href
const hrefValue = enlace.getAttribute("href");
console.log("Valor actual del atributo href:", hrefValue);
// Modificar el valor del atributo href
enlace.setAttribute("href", "https://www.nuevaweb.com");
// Verificar el nuevo valor del atributo href
const nuevoHrefValue = enlace.getAttribute("href");
console.log("Nuevo valor del atributo href:", nuevoHrefValue);

```
- ¿Qué es el objeto window? Windows es un objeto que contiene información de toda la pagina web. Podemos ver todos sus atributos con `console.log(this)`
### Modificar elementos
```javascript
let var = document.getElementByID("nombreID"); //Seleccionamos el elemento
var.textContent = "nuevo texto"; // Modificamos el contenido del texto
```