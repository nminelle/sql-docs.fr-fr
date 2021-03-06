---
title: Regroupement de connexions (Microsoft Drivers for PHP for SQL Server) | Documents Microsoft
ms.custom: 
ms.date: 07/10/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: connection pooling support
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5edf501c5a3a46fd30d21c4c5fdad81711c539d5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="connection-pooling-microsoft-drivers-for-php-for-sql-server"></a>Regroupement de connexions (Microsoft Drivers for PHP for SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Voici des points importants à noter sur le regroupement de connexions dans [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]:  
  
-   [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] utilise le regroupement de connexions ODBC.  
  
-   Par défaut, le regroupement de connexions est activé dans Windows. Linux et Mac OS X, les connexions sont regroupées uniquement si le regroupement de connexions est activé pour ODBC. Lorsque le regroupement de connexions est activé et que vous vous connectez à un serveur, le pilote tente d’utiliser une connexion regroupée avant d’en créer un nouveau. Si une connexion équivalente est introuvable dans le regroupement, une nouvelle connexion est créée et ajoutée à ce regroupement. Le pilote détermine si les connexions sont équivalentes, par comparaison avec des chaînes de connexion.  
  
-   Quand une connexion du regroupement est utilisée, l’état de la connexion est réinitialisé.  
  
-   La fermeture de la connexion retourne la connexion au regroupement.  
  
Pour plus d’informations sur le regroupement de connexions, consultez [Regroupement de connexions du Gestionnaire de pilotes](http://go.microsoft.com/fwlink/?linkid=119622).  
  
## <a name="enablingdisabling-connection-pooling"></a>Le regroupement de l’activation/désactivation de la connexion
### <a name="windows"></a>Windows
Vous pouvez forcer le pilote pour créer une nouvelle connexion (au lieu de rechercher une connexion équivalente dans le pool de connexions) en définissant la valeur de la *ConnectionPooling* attribut dans la chaîne de connexion à **false**  (ou 0).  
  
Si le *ConnectionPooling* attribut est omis à partir de la chaîne de connexion ou si elle est définie sur **true** (ou 1), le pilote crée uniquement une nouvelle connexion si aucune connexion équivalente n’existe pas dans le pool de connexions.  
  
Pour plus d’informations sur les autres attributs de connexion, consultez [Connection Options](../../connect/php/connection-options.md).  
### <a name="linux-and-mac-os-x"></a>Linux et Mac OS X
*ConnectionPooling* attribut ne peut pas être utilisé pour activer ou désactiver le regroupement de connexions. 

Le regroupement de connexions peut être activé/désactivé en modifiant le fichier de configuration odbcinst.ini. Le pilote doit être rechargé pour que les modifications prennent effet.

Paramètre `Pooling` à `Yes` et un nombre positif `CPTimeout`valeur dans le fichier odbcinst.ini permet le regroupement de connexions. 
```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
CPTimeout=<int value>
```
Paramètre `Pooling` à `No` dans le fichier odbcinst.ini force le pilote à créer une nouvelle connexion.
```
[ODBC]
Pooling=No
```
  
## <a name="see-also"></a>Voir aussi  
[Procédure : se connecter avec l’authentification Windows](../../connect/php/how-to-connect-using-windows-authentication.md)  
[Procédure : se connecter à l’aide de l’authentification SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
  
