#javascript #obb

### Creando clases
```javascript
function Persona(nombre){
	this.nombre = nombre;
	return () => console.log(this.nombre, 77);//Devuelve esta funcion
}
let clase = new Persona("sebas");
sebas();//Impreme nombre 77, la arrow function no crea scope y toma el del padre
```
- Elemento `this`