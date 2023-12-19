#html #php
Todo formulario debe tener: 
- `Action`: ruta de quien va a procesar el formulario .
- `Method`: el método que usara el envió de datos `POST, GET`.
- `Button submit`:  para enviar los datos del formulario.
```html
<form action="archivo.php" method="post">
	<label>Nombre: <input type="text" name="nombre"> <br> </label>
	<label>Email: <inptu type="text" name="email"> <br> </label>
	<button type="submit">Enviar</button>
</form>
```
El `archivo.php` que procese la información se vera así : 
```php
<body> 
Hola <?php echo $_POST["nombre"]; ?> <br> 
Tu email es: <?php echo $_POST["email"]; ?> 
</body>
```
#### procesar el formulario en la misma pagina 
Usamos el código para verificar que se ha enviado la información del formulario
```php
if($_SERVER["REQUEST_METHOD"] == "POST"){
    $nombre = $_POST["nombre"];
    $email = $_POST["email"];  
}
```
Para usar las secciones del formulario debemos de darles **nombre**.
#### ¿`GET` o `POST`?
Usamos GET para sacar información de la base de datos y  POST para meterla.
### Validación de formulario ✔️
Las verificaciones por parte del servidor las realizamos en php, en las del cliente por javascript.
Los contratos no son obligatorios. Hay controles que si no interactúa el usuario no existe.

Para comprobar que existe ese elemento en el formulario usaremos la función `isset()`. 
```php
if (isset($_POST['name'], $_POST['email'])) { 	
$name = $_POST['name']; $email = $_POST['email'];
}
```
Debemos de asegurar los formularios para que no se ejecute código en los inputs.
`<script>alert('Hola.');</script>`
####  Ataques XSS (atreves de otro servidor) 🧨
Debemos sanear la entrada del usuario, existen siempre y se pueden acceder desde cualquier parte del guion en cualquier momento.

Informar de errores, Preguntar mantener la entrada y si existe value `value"<? variable=?>` mostrar 
`$REQUEST $POST $_GET`
- Emplear los botones de envió para lanzar procesos de comprobación y procesos de formulario
#### Sanitizar datos 💊
Para sanear los datos;
```php
function filtrarDatos($datos){
	$datos=trim($datos); // Elimina espacios antes y después de los datos
    $datos=stripslashes($datos); // Elimina backslashes \
    $datos=htmlspecialchars($datos); // Traduce caracteres especiales en entidades HTML
    return $datos;
}
```
Lo aplicamos al archivo que procesara los datos del formulario.
```php
	if(isset($_POST["submit"]) && $_SERVER["REQUEST_METHOD"] == "POST"){
	// Si EXISTEN los datos SANEARLOS
    $nombre = filtrado($_POST["nombre"]);
    $password = filtrado($_POST["password"]); 
}
```

#### Self-Procesing Form
```php
    <main>
        <?php if ($_SERVER['REQUEST_METHOD'] === 'GET') : ?>
            <form action="<?php htmlspecialchars($_SERVER['PHP_SELF']) ?>" method="post">
                <label>Name</label>
                <input type="text" name="name" required="required">
                <label>Email</label>
                <input type="email" name="email">
            <button type="submit">Enviar</button>
            </form>  
        <?php else: ?>
            <?php
                include_once "funciones.inc";
                if(isset($_POST['name'], $_POST['email'])){
                    //Saneamos la entrada de datos
                    $name = filtrar($_POST['name']);
                    $email = filtrar($_POST['email']);
                    echo "Thanks for your subscription $name. <br>";
                    echo "Confirm it in your inbox of the $email.";
                } else {
                    echo "You need to provide your name and  email address.";
                }
            ?>
        <?php endif?>
    </main>
```
