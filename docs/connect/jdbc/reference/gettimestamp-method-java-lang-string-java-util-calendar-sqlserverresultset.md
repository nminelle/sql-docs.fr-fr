---
title: "Méthode getTimestamp (java.lang.String, java.util.Calendar) | Documents Microsoft"
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
apiname: SQLServerResultSet.getTimestamp (java.lang.String, java.util.Calendar)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 44474000-8951-49ee-93a5-c8cb879eaf55
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62466b3b77d2ce85fcc9573804b1cd8b7347280e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="gettimestamp-method-javalangstring-javautilcalendar-sqlserverresultset"></a>Méthode getTimestamp (java.lang.String, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du nom de colonne désigné dans la ligne actuelle de ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet comme un objet java.sql.Timestamp dans le langage de programmation, à l’aide d’un objet de calendrier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Timestamp getTimestamp(java.lang.String colName,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nom de colonne*  
  
 A **chaîne** qui contient le nom de colonne.  
  
 *licences d’accès client*  
  
 Un objet de calendrier.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet Timestamp.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTimestamp est spécifiée par la méthode getTimestamp dans l’interface java.sql.ResultSet.  
  
 Cette méthode retourne des valeurs uniquement à partir de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] colonnes datetime et smalldatetime.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getTimestamp &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
