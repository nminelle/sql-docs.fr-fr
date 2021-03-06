---
title: Le regroupement de connexions prenant en charge les pilotes | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53e7e3f7-edab-4d0b-8943-45442ba3ebc9
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 337ce5bca53a3b9099cbe9cd91774b748930d7ea
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="driver-aware-connection-pooling"></a>Regroupement de connexions prenant en charge les pilotes
Le regroupement de connexions prenant en charge de pilote est une nouvelle fonctionnalité du Gestionnaire de pilotes dans Windows 8. Le regroupement de connexions prenant en charge de pilote permet les rédacteurs de pilotes personnaliser le comportement dans son pilote ODBC de pool de connexions.  
  
> [!NOTE]  
>  Le regroupement de connexions prenant en charge de pilote n’est pas pris en charge avec la bibliothèque de curseurs. Une application message d’erreur si elle tente d’activer la bibliothèque de curseurs via SQLSetConnectAttr, lorsque le regroupement de connexions prenant en charge de pilote est activé.  
  
 Pilote prenant en charge le regroupement de connexions adresses les problèmes suivants liés au regroupement de connexions du Gestionnaire de pilotes :  
  
 **Fragmentation de pool** le Gestionnaire de pilotes renvoie uniquement une connexion à partir du pool s’il s’agit d’une correspondance exacte avec la chaîne de connexion d’une nouvelle demande de connexion.  L’une des raisons pour le Gestionnaire de pilotes pour exiger une correspondance exacte sont que le Gestionnaire de pilotes ne comprend pas de chaque mot-clé de chaîne de connexion spécifiques au pilote et sa valeur.  Toutefois, certaines valeurs de mot clé de chaîne de connexion (par exemple, le nom de la base de données) ne peuvent pas exiger une correspondance exacte, puisque le pilote peut modifier la base de données en moins le temps nécessaire pour ouvrir une nouvelle connexion (la différence de temps exacte dépend de la source de données). Et les différences de certains attributs de connexion (par exemple, SQL_ATTR_CURRENT_CATALOG) peuvent prendre plus de temps pour la modifier que les différences dans les autres attributs (par exemple, SQL_ATTR_LOGIN_TIMEOUT). Cela, trop, peut empêcher le Gestionnaire de pilotes à partir du pool à l’aide de la connexion plus économique et réutilisable. Lorsqu’un pilote a créer le nombre de nouvelles connexions, peuvent réduire les performances d’une application et l’évolutivité de source de données peut diminuer. Fragmentation de pool peut être réduite avec le regroupement de connexions prenant en charge de pilote, car un pilote peut mieux estimer le coût de réutiliser une connexion dans le pool pour une demande de connexion.  
  
 **Aucune considération de préférence de l’application** certaines sources de données peuvent ouvrir efficacement de nouvelles connexions (par rapport à la réinitialisation de certains attributs), par conséquent, une application pouvez ouvrir une nouvelle connexion au lieu de tenter de réutiliser une connexion légèrement ne correspondent pas à partir du pool et réinitialiser certaines valeurs (bien que cela peut être plus lent lors de l’expression de l’initialisation de pool de connexion). Mais certaines applications peuvent conserver la plus petite de la charge du serveur et ouvrir des connexions moins, bien qu’il peut y avoir un coût plus grand pour résoudre les incompatibilités de comportement correct. Sans le regroupement de connexions prenant en charge de pilote, vous ne pouvez pas spécifier ce genre de préférence efficacement, car le Gestionnaire de pilote ne reconnaît pas tous les attributs de connexion spécifiques au pilote. Le regroupement de connexions prenant en charge les pilotes permet à un pilote obtenir la préférence utilisateur (avec un attribut spécifique au pilote de SQLSetConnectAttr) afin qu’il peut mieux estimer le coût de réutiliser une connexion à partir du pool selon la préférence de l’utilisateur.  
  
 Pour plus d’informations sur le regroupement de connexions prenant en charge les pilotes, consultez [développement reconnaissance du Pool de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
## <a name="determining-driver-support"></a>Déterminer les pilotes pris en charge  
 Le regroupement de connexions prenant en charge de pilote est une fonctionnalité facultative qui un pilote ne peut pas prendre en charge. Pour déterminer si un pilote prend en charge, utilisez le SQL_DRIVER_AWARE_POOLING_SUPPORTED *InfoType* de [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
## <a name="how-to-enable-driver-aware-connection-pooling"></a>Comment activer le regroupement de connexions prenant en charge de pilote  
 Une application peut utiliser la reconnaissance du regroupement de connexions d’un pilote en affectant à l’attribut SQL_ATTR_CONNECTION_POOLING SQL_CP_DRIVER_AWARE avec [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Si un pilote ne prend pas en charge la reconnaissance du pool de connexions, le regroupement de connexions du Gestionnaire de pilotes sera utilisé (identique comme si SQL_CP_ONE_PER_HENV avait été spécifié, au lieu de SQL_CP_DRIVER_AWARE). Les applications ODBC 2.x et 3.x peuvent activer cette fonctionnalité.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
