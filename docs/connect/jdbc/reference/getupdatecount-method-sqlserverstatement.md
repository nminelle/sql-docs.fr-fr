---
title: "getUpdateCount (méthode) (SQLServerStatement) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerStatement.getUpdateCount
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: e9570228-4500-44b6-b2f1-84ac050b5112
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 129836495f7d9dd4076cd3aed7ede77e4c05f6a3
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getupdatecount-method-sqlserverstatement"></a>getUpdateCount (méthode) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le résultat actuel en tant que nombre de mises à jour.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int getUpdateCount()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui contient le nombre de mises à jour. Si le résultat retourné est un objet de jeu de résultats ou s'il n'y a plus de résultat, -1 est retourné.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getUpdateCount est spécifiée par la méthode getUpdateCount dans l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
