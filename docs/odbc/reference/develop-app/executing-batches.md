---
title: "Exécuter des traitements | Documents Microsoft"
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
- batches [ODBC], executing
- SQL statements [ODBC], batches
ms.assetid: f082c717-4f82-4820-a2fa-ba607d8fd872
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 620965b524b6d76d1f1d0a3d7adaf84c05c4540c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="executing-batches"></a>L’exécution de lots
Avant qu’une application exécute un lot d’instructions, il doit tout d’abord vérifier si elles sont prises en charge. Pour ce faire, l’application appelle **SQLGetInfo** avec les options SQL_BATCH_SUPPORT, SQL_PARAM_ARRAY_ROW_COUNTS et SQL_PARAM_ARRAY_SELECTS. La première option retourne si la création de nombre de lignes et le résultat d’instructions de création de jeu sont prises en charge dans les lots explicites et procédures, pendant les deux dernières options de renvoyer des informations sur la disponibilité du nombre de lignes et résultat définit dans paramétrable d’exécution.  
  
 Lots d’instructions sont exécutées via **SQLExecute** ou **SQLExecDirect**. Par exemple, l’appel suivant exécute un lot explicit d’instructions pour ouvrir une nouvelle commande.  
  
```  
SQLCHAR *BatchStmt =  
   "INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)"  
      "VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 1, 1234, 10);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 2, 987, 8);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 3, 566, 17);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 4, 412, 500)";  
  
SQLExecDirect(hstmt, BatchStmt, SQL_NTS);  
```  
  
 Lorsqu’un lot de génération de résultat instructions est exécutée, elle retourne l’une ou plusieurs nombres de lignes ou de résultat définit. Pour plus d’informations sur la façon de récupérer ces, consultez [plusieurs résultats](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Si un lot d’instructions inclut des marqueurs de paramètres, ceux-ci sont numérotées en augmentant l’ordre des paramètres, comme dans toute autre instruction. Par exemple, le lot suivant d’instructions a des paramètres numérotées de 1 à 21 ; celles figurant dans la première **insérer** instruction sont numérotés 1 à 5 et celles de la dernière **insérer** instruction sont numérotés de 18 à 21.  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 Pour plus d’informations, consultez [paramètres de l’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.
