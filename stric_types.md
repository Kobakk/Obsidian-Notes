#php #syntax

```php
declare(stric_types=1);
```

Se utiliza para habilitar el modo estricto de tipos en una parte específica del archivo.php, se realiza la conversión de tipos mas riguroso sin permitir conversiones automáticas. 

```php
declare(strict_types=1);

function sumar(int $a, int $b) {
    return $a + $b;
}

echo sumar(5, "10"); // Esto generará un error debido a la conversión automática de tipo

function dividir(int $a, int $b): float {
    return $a / $b;
}

echo dividir(10, 3); // Esto está bien, devuelve un float
echo dividir(10, 3.5); // Esto generará un error debido a la conversión automátic
```

- Es útil cuando deseas escribir código más seguro y evitar errores sutiles relacionados con los tipos de datos. Ayuda a detectar y prevenir problemas de tipo en tiempo de ejecución.
- Solo afecta al archivo en el que se coloca y a las funciones definidas en ese archivo. ==No afecta a otros archivos incluidos o requeridos en el script==
