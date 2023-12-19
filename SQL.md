#sql #transacciones #rollback

### Ejemplos Transacciones
```sql
USE AdventureWorks2022 go begin transaction
	delete sales.SalesOrderDetail where SalesOrderID = 43659
	and SalesOrderDetailID = 1
	select * from sales.SalesOrderDetail
```
### Selección parámetros de los valores
```php
<?php
$con = new PDO("sqlsrv:Server=(local); Database = Prueba");
$con->beginTransaction();
$ret = $con->exec("insert into Tabla1 (col1, col2) values ('a','b')");
$ret = $con->exec("insert into Tabla1 (col1, col2) values ('a','c')");
$ret = $con->exec("delete from Tabla1 where col1='a' and col2='b'");
$con->commit();
//$con->rollback();
echo $ret;
```
Una transaccion rara
```php
<?php

/* FUNCTION: perform_trans_ops */

function perform_trans_ops(PDO $con, int $orderId):bool
{
    $sql1 = "UPDATE Production.ProductInventory
            SET Quantity = Quantity + s.OrderQty
            FROM Production.ProductInventory p
            JOIN Sales.SalesOrderDetail s
            ON s.ProductID = p.ProductID
            WHERE s.SalesOrderID = ?";
    $sql2 = "DELETE FROM Sales.SalesOrderDetail
                    WHERE SalesOrderID = ?";
    $params = array($orderId);
    try
    {
        $snt = $con->prepare($sql1);
        $snt->execute($params);
        $snt2 = $con->prepare($sql2);
        $snt2->execute($params);
        return true;
    } catch(PDOException $ex)
    {
        throw $ex;
        return false;
    }
}

$server = "(local)";
$db = "AdventureWorks2022";
$con = null;
$orderId = 43667; // Set the Order ID.
try {
    $con = new PDO("sqlsrv:server=$server;Database=$db");
    $con->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    $con->beginTransaction();
    if (perform_trans_ops($con, $orderId)) {
        if ($con->commit()) {
            echo "Transaction committed.<br>\n";
        } else {
            echo "Commit failed - rolling back.<br>\n";
            $con->rollback();
        }
    } else {
        echo "Error in transaction operation - rolling back.<br>\n";
        $con->rollBack();
    }
} catch (PDOException $ex) {
    if (isset($con))
        $con->rollBack();
    throw $ex;
} finally {
    $con = null;
}
```