---
title: "Méthode prepareStatement (java.lang.String, int[]) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.prepareStatement (java.lang.String, int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 72b5c4a5-1382-4b2c-80a0-47c97c5f52d3
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f9806010a9e30b86926f257326cdf719c1b87057
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="preparestatement-method-javalangstring-int"></a>Méthode prepareStatement (java.lang.String, int[])
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) objet pour envoyer des instructions SQL paramétrées à la base de données, et qui est capable de retourner les clés générées automatiquement désignées par le tableau donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sql,  
                                                   int[] columnIndexes)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *SQL*  
  
 A **chaîne** qui contient une instruction SQL.  
  
 *columnIndexes*  
  
 Un tableau d'entiers.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet PreparedStatement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode prepareStatement est spécifiée par la méthode prepareStatement dans l’interface java.sql.Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode prepareStatement &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)   
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  