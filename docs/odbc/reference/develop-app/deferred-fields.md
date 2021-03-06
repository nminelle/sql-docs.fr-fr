---
title: "Différée champs | Documents Microsoft"
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
helpviewer_keywords:
- descriptors [ODBC], deferred fields
- deferred fields [ODBC]
ms.assetid: 5abeb9cc-4070-4f43-a80d-ad6a2004e5f3
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2042efcdacf45a8638bb5197da04f903a6ffdd0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="deferred-fields"></a>Champs différés
Les valeurs de *différée champs* ne sont pas utilisés lorsqu’ils sont définis, mais le pilote enregistre les adresses des variables pour un effet différé. Pour un descripteur de paramètre d’application, le pilote utilise le contenu des variables au moment de l’appel à **SQLExecDirect** ou **SQLExecute**. Pour le descripteur de ligne d’une application, le pilote utilise le contenu des variables au moment de l’extraction.  
  
 Champs différés sont les suivantes :  
  
-   Champs d’un enregistrement de descripteur SQL_DESC_DATA_PTR et SQL_DESC_INDICATOR_PTR.  
  
-   Le champ SQL_DESC_OCTET_LENGTH_PTR d’un enregistrement de descripteur d’application.  
  
-   Dans le cas d’une extraction de plusieurs ligne, les champs SQL_DESC_ARRAY_STATUS_PTR et SQL_DESC_ROWS_PROCESSED_PTR d’un en-tête de descripteur.  
  
 Lorsqu’un descripteur est alloué, champs de chaque enregistrement de descripteur différés ont initialement une valeur null. La signification de la valeur null est la suivante :  
  
-   Si SQL_DESC_ARRAY_STATUS_PTR a une valeur null, une extraction de lignes multiples ne peut pas retourner de ce composant par ligne informations de diagnostic.  
  
-   Si SQL_DESC_DATA_PTR a une valeur null, l’enregistrement est indépendant.  
  
-   Si le champ SQL_DESC_OCTET_LENGTH_PTR d’un ARD a une valeur null, le pilote ne retourne pas d’informations sur la longueur de cette colonne.  
  
-   Si le champ SQL_DESC_OCTET_LENGTH_PTR d’un APD a une valeur null et que le paramètre est une chaîne de caractères, le pilote part du principe que la chaîne est terminée par null. Paramètres de sortie dynamique, une valeur null dans ce champ empêche le pilote de retourner des informations de longueur. (Si le champ SQL_DESC_TYPE n’indique pas un paramètre de chaîne de caractères, le champ SQL_DESC_OCTET_LENGTH_PTR est ignoré.)  
  
 L’application ne doit pas libérer ou ignorer les variables utilisées pour les champs différés entre l’heure que les associe aux champs et l’heure, le pilote lit ou écrit les.
