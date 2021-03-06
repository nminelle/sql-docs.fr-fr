---
title: sqlsrv_rows_affected | Documents Microsoft
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
apiname: sqlsrv_rows_affected
apitype: NA
helpviewer_keywords:
- sqlsrv_rows_affected
- API Reference, sqlsrv_rows_affected
ms.assetid: 6f43fbfc-fc92-449b-82d0-33fa780e8f09
caps.latest.revision: "24"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62fd71d47b762680d9c85a24366c0c3b55cf9109
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="sqlsrvrowsaffected"></a>sqlsrv_rows_affected
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Retourne le nombre de lignes modifiées par la dernière instruction exécutée. Cette fonction ne retourne pas le nombre de lignes renvoyées par une instruction SELECT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sqlsrv_rows_affected( resource $stmt)  
```  
  
#### <a name="parameters"></a>Paramètres  
*$stmt*: ressource d’instruction correspondant à une instruction exécutée.  
  
## <a name="return-value"></a>Valeur retournée  
Entier indiquant le nombre de lignes modifiées par la dernière instruction exécutée. Si aucune ligne n’a été modifiée, la valeur zéro (0) est retournée. Si aucune information sur le nombre de lignes modifiées n’est disponible, la valeur moins un (-1) est retournée. Si une erreur s’est produite lors de la récupération du nombre de lignes modifiées, **false** est retourné.  
  
## <a name="example"></a>Exemple  
L’exemple suivant affiche le nombre de lignes modifiées par une instruction UPDATE. L’exemple suppose que SQL Server et la base de données [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) sont installés sur l’ordinateur local. Toute la sortie est écrite dans la console quand l’exemple est exécuté à partir de la ligne de commande.  
  
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
  
/* Set up Transact-SQL query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET SpecialOfferID = ?   
         WHERE ProductID = ?";  
  
/* Set parameter values. */  
$params = array(2, 709);  
  
/* Execute the statement. */  
$stmt = sqlsrv_query( $conn, $tsql, $params);  
  
/* Get the number of rows affected and display appropriate message.*/  
$rows_affected = sqlsrv_rows_affected( $stmt);  
if( $rows_affected === false)  
{  
     echo "Error in calling sqlsrv_rows_affected.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
elseif( $rows_affected == -1)  
{  
      echo "No information available.\n";  
}  
else  
{  
      echo $rows_affected." rows were updated.\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[référence d’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)  
[Mise à jour des données &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  
  
