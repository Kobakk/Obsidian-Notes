Un **for-each** iteramos sobre cosas que **obligatoriamente** deben de existir (elementos de una cadena)
Es especialmente útil cuando solo necesitas acceder a los elementos uno por uno y no necesitas llevar un registro de las posiciones.
```java
int[] numeros = {1, 2, 3, 4, 5};    
// Usando el bucle for-each para imprimir cada número
for (int numero : numeros) {
    System.out.println(numero);
}
```

Un **for** iteramos sobre cosas que no tienen porque existir, y nos garantiza el orden de acceso dandonos un mayor control

```java
for (int i = 0; i < 5; i++)
```