---
title: Membres de SQLServerXAConnection | Documents Microsoft
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
ms.assetid: 4b61dabd-369b-460c-8450-9fe424f76541
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 88fc82e655317b6dadd5795c575d58d8edec3040
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverxaconnection-members"></a>Membres de SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Les tableaux suivants répertorient les membres qui sont exposées par le [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) classe.  
  
## <a name="constructors"></a>Constructeurs  
 Aucun.  
  
## <a name="fields"></a>Champs  
 Aucun.  
  
## <a name="inherited-fields"></a>Champs hérités  
 Aucun.  
  
## <a name="methods"></a>Méthodes  
  
|Nom| Description|  
|----------|-----------------|  
|[addConnectionEventListener](../../../connect/jdbc/reference/addconnectioneventlistener-method-sqlserverpooledconnection.md)|(Héritée de [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) inscrit l’écouteur d’événement donné afin qu’il puisse être informé lorsqu’un événement se produit sur cet objet de connexion.|  
|[Fermer](../../../connect/jdbc/reference/close-method-sqlserverpooledconnection.md)|(Héritée de [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) ferme la connexion physique représentée par cet objet de connexion.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverpooledconnection.md)|(Héritée de [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) crée un handle d’objet pour la connexion physique représentée par cet objet de connexion.|  
|[getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md)|Récupère un [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) de l’objet que le Gestionnaire de transactions utilisera pour gérer la participation de ce [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) objet dans une transaction distribuée.|  
|[removeConnectionEventListener](../../../connect/jdbc/reference/removeconnectioneventlistener-method-sqlserverpooledconnection.md)|(Héritée de [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) supprime l’écouteur d’événement donné.|  
  
## <a name="inherited-methods"></a>Méthodes héritées  
  
|Classe héritée de :|Méthodes|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|javax.sql.PooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerXAConnection, classe](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
