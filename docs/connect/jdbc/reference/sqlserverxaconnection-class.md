---
title: Classe SQLServerXAConnection | Documents Microsoft
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
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e6c016a665405a50ce133de5e45ef77ddf0981d0
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverxaconnection-class"></a>Classe SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente les connexions JDBC qui peuvent participer à des transactions distribuées (XA).  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
 **Implémente :** javax.sql.XAConnection  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerXAConnection  
```  
  
## <a name="remarks"></a>Notes  
 Un objet SQLServerXAConnection peut être inscrit dans une transaction distribuée au moyen d’un [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) objet. Un gestionnaire de transactions, faisant généralement partie d’un serveur de couche intermédiaire, gère un objet SQLServerXAConnection via l’objet SQLServerXAResource.  
  
> [!NOTE]  
>  En général, les programmateurs d'applications n'utilisent pas cette interface directement. Elle est principalement utilisée par un gestionnaire de transactions actif dans le serveur de couche intermédiaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Référence d’API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
