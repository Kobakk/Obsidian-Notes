#DataStructure 
1. Set: Esto declara una variable llamada **uniques** que almacenará un conjunto de números enteros (Integer en Java). Un conjunto es una colección de elementos donde cada elemento es único, es decir, no puede haber duplicados.
Ejemplo : [[217. Contains Duplicate]]
```Java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> uniques = new HashSet<>();
        for (int i = 0; i < nums.length; i++) {
            if (uniques.contains(nums[i])) {
                return true;
            }
            uniques.add(nums[i]);
        }
        return false;
    }
}
```

También lo podemos encontrar en JavaScript 

```JavaScript 
let uniques = new Set();

uniques.add(5);
uniques.add(10);
uniques.add(15);

// Evitar elementos duplicados
uniques.add(10); // Esto no se agregará

console.log([...uniques]); // [5, 10, 15]
```
#### Lógica propia
En anteriores versiones no había la estructura Set pero podíamos crearla nosotros mediante

```JavaScript 
let uniques = [];

// Agregar elementos únicos al conjunto simulado
uniques.push(5);
uniques.push(10);
uniques.push(15);

// Evitar elementos duplicados / Aplicanos nuestra lógica 
if (!uniques.includes(10)) {
    uniques.push(10);
}

console.log(uniques); // [5, 10, 15]
```
Lógica para que un elemento no sea repetido