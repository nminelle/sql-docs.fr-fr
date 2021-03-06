---
title: "Par défaut des Types de données SQL Server | Documents Microsoft"
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
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: 65c7c211-96d3-4e65-a1de-1fe8d21348e7
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7b81f0a84c40fc7d184beccf1532386b4284fafd
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="default-sql-server-data-types"></a>Types de données SQL Server par défaut
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Lors de l’envoi de données au serveur, le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] convertit les données de leur type de données PHP vers un type de données SQL Server si aucun type de données SQL Server n’a été spécifié par l’utilisateur. Le tableau suivant indique le type de données PHP (type de données envoyé au serveur) et le type de données SQL Server par défaut (type de données vers lequel les données sont converties). Pour plus d’informations sur la spécification des types de données durant l’envoi de données au serveur, consultez [Procédure : spécifier des types de données SQL Server quand vous utilisez le pilote SQLSRV](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md).  
  
|Type de données PHP|Type SQL Server par défaut dans le pilote SQLSRV|Type SQL Server par défaut dans le pilote PDO_SQLSRV|  
|-----------------|------------------------------------------------|-----------------------------------------------------|  
|NULL|varchar(1)|Non pris en charge|  
|Booléen|bit|bit|  
|Integer|int|int|  
|Float|float(24)|Non pris en charge|  
|String (longueur inférieure à 8000 octets)|varchar (<string length>)|varchar (<string length>)|  
|String (longueur supérieure à 8000 octets)|varchar(max)|varchar(max)|  
|Ressource|Non pris en charge.|Non pris en charge.|  
|Flux (encodage : non binaire)|varchar(max)|varchar(max)|  
|Flux (encodage : binaire)|varbinary|varbinary|  
|Tableau|Non pris en charge.|Non pris en charge.|  
|Objet|Non pris en charge.|Non pris en charge.|  
|DateTime (1)|datetime|Non pris en charge.|  
  
## <a name="see-also"></a>Voir aussi  
[Constantes &#40;pilotes Microsoft SQL Server pour PHP&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Converting Data Types](../../connect/php/converting-data-types.md)  
[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
[Types PHP](http://go.microsoft.com/fwlink/?LinkId=109071)  
[Types de données (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=109068)  
  
