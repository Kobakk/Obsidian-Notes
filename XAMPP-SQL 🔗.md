#php #config 

### Instalación y configuración de SQL
Necesitamos instalar dos programas.
- SQL2022-SSEI
- SSMS
Configuramos el puerto del servidor SSMS 
TCP/IP 1433
Importamos una base de datos .back

C:\Program Files\Microsoft SQL Server\MSSQL16.SEV\MSSQL\Backup
### Configuración de XAMPP
Para añadir extensiones a XAMPP ponemos la ruta 
xampp->php->ext 
ponemos  nuestras extensiones.dll 
(**php_sqlsrv_82_ts_x64** y **php_pdo_sqlsrv_82_ts_x64**)
[Link para descargar extensione](https://github.com/Microsoft/msphpsql/releases)
Añadimos las rutas de las nuevas extensiones en xampp->php->php.ini
que es el archivo de configuración de xampp
### Configuración SQL
- Servidor 1324
### Código para conectarnos a una bbdd
Necesitamos utilizar este código para conectarnos a nuestra bbdd de sql.
```php
try {
    $con = new PDO("sqlsrv:Server=(local);
    Database=AdventureWorks2022", NULL, NULL);
    $con->setAttribute(
        PDO::ATTR_ERRMODE,
        PDO::ERRMODE_EXCEPTION
    );
} catch (PDOException $ex) {
    die("Error al conectar a SQL Server " . $ex->getMessage());
}
```
### Interacciones con BBDD


#### Recuperación de Información
`PDO `
```php
$query = "SELECT ModifiedDate FROM HumanResources.Employee WHERE BusinessEntityID=1";
try {
    $con = new PDO("sqlsrv:Server=(local); Database = AdventureWorks2022");
    //Esrablece el atributo de conexión
    $con->setAttribute(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE, true);
    $stn = $con->prepare($query);
    $stn->execute();
    //Espera un valor ModifiedDate de tipo PHP DateTime
    $row = $stn->fetch(PDO::FETCH_ASSOC);
    var_dump($row);
} catch (PDOException $ex) {
    die("Error al conectar a SQL Server " . $ex->getMessage());
} finally {
    unset($stn);
    unset($con);
}
```

#### Concurrencia optimista 📈
%%21/11%%
```sql
update tabla
	set edad =39;L
where nombre = 'test';
	and edad = 38
	and tlf = '9231313';
```
Un bucle concurrente, numero de acceso a dicha información y imponemos bloqueos para frenar las **concurrencias**.  Maneja los datos de la manera que los bloquea hasta que revisa los siguientes datos.