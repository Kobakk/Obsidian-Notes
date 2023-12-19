#javascript 
```javascript
//Podemos poner todos los parametros que queramos en nuestra función
funcion(parametro, (parametro) => {
	return parametro *2;
});
//Una función con una función con parametro dentro de ella 
funcion(parametro, (parametro) => parametro * 2);
```
En javascript tenemos mas formas de crear funciones, para  simplificar o crear funciones mas complejas
### Clases
Ejemplo de  como llamar a una función compleja de un objeto.
```javascript
const objeto = {
	funcionRecorrer: function (otraFuncion){
		for (let index in puntos)
		puntos[index] = otraFuncion(puntos[index]);
	}
}
objeto.funcionRecorrer((valor) => valor *2);
```
- **Las clases en javascript no existen**, solo los objetos que son creado en el acto.
### Bucles
```javascript
const array = [1, 2, 3];
array.forEach((value) => value++);
console.log(values)
```
De esta manera operamos con funciones sobre arrays.