---
title: sqlsrv_cancel | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: sqlsrv_cancel
apitype: NA
helpviewer_keywords:
- sqlsrv_cancel
- API Reference, sqlsrv_cancel
ms.assetid: 75798c9b-f711-445d-9b8f-ba4d405ca50a
caps.latest.revision: "32"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3d16a6d3407f6533cbf9a0b3ed9ad440a8ad2ab1
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="sqlsrvcancel"></a>sqlsrv_cancel
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Annule une instruction. Cela signifie que les résultats de l’instruction en attente sont ignorés. Une fois que cette fonction est appelée, l’instruction peut être réexécutée si elle a été préparée avec [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md). L’appel de cette fonction n’est pas nécessaire si tous les résultats associés à l’instruction ont été consommés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sqlsrv_cancel( resource $stmt)  
```  
  
#### <a name="parameters"></a>Paramètres  
*$stmt*: instruction à annuler.  
  
## <a name="return-value"></a>Valeur retournée  
Valeur booléenne : **true** si l’opération a réussi. Dans le cas contraire, la valeur est **false**.  
  
## <a name="example"></a>Exemple  
L’exemple suivant cible la base de données [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) pour exécuter une requête, puis consomme et compte les résultats jusqu’à ce que la variable *$salesTotal* atteigne le montant spécifié. Les autres résultats de requête sont alors ignorés. L’exemple part du principe que SQL Server et la base de données AdventureWorks sont installés sur l’ordinateur local. Toute la sortie est écrite dans la console quand l’exemple est exécuté à partir de la ligne de commande.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Prepare and execute the query. */  
$tsql = "SELECT OrderQty, UnitPrice FROM Sales.SalesOrderDetail";  
$stmt = sqlsrv_prepare( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in statement preparation.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
if( sqlsrv_execute( $stmt ) === false)  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Initialize tracking variables. */  
$salesTotal = 0;  
$count = 0;  
  
/* Count and display the number of sales that produce revenue  
of $100,000. */  
while( ($row = sqlsrv_fetch_array( $stmt)) && $salesTotal <=100000)  
{  
     $qty = $row[0];  
     $price = $row[1];  
     $salesTotal += ( $price * $qty);  
     $count++;  
}  
echo "$count sales accounted for the first $$salesTotal in revenue.\n";  
  
/* Cancel the pending results. The statement can be reused. */  
sqlsrv_cancel( $stmt);  
?>  
```  
  
## <a name="comments"></a>Commentaires  
Une instruction préparée et exécutée à l’aide de la combinaison de [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) et [sqlsrv_execute](../../connect/php/sqlsrv-execute.md) peut être réexécutée avec **sqlsrv_execute** après l’appel de **sqlsrv_cancel**. Une instruction est exécutée avec [sqlsrv_query](../../connect/php/sqlsrv-query.md) ne peut pas être réexécutée après l’appel **sqlsrv_cancel**.  
  
## <a name="see-also"></a>Voir aussi  
[référence d’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Connexion au serveur](../../connect/php/connecting-to-the-server.md)  
[Récupération de données](../../connect/php/retrieving-data.md)  
[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)  
[sqlsrv_free_stmt](../../connect/php/sqlsrv-free-stmt.md)  
  
