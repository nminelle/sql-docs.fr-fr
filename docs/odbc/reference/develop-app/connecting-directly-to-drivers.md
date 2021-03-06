---
title: "Se connecter directement à des pilotes | Documents Microsoft"
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
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4da4d454eddccae8f72a29d5903887ffec14842c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="connecting-directly-to-drivers"></a>Se connecter directement à des pilotes
Comme mentionné dans [choisir une Source de données ou le pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md), plus haut dans cette section, certaines applications ne souhaitez pas utiliser une source de données du tout. Au lieu de cela, ils souhaitent se connecter directement à un pilote. **SQLDriverConnect** fournit un moyen de l’application de se connecter directement à un pilote sans spécifier une source de données. Point de vue conceptuel, une source de données temporaire est créée au moment de l’exécution.  
  
 Pour vous connecter directement à un pilote, l’application spécifie le **pilote** mot clé dans la chaîne de connexion à la place de la **DSN** (mot clé). La valeur de la **pilote** mot clé est la description du pilote renvoyé par **SQLDrivers**. Par exemple, un pilote a la description du pilote Paradox et exige que le nom d’un répertoire contenant les fichiers de données. Pour vous connecter à ce pilote, l’application peut utiliser une des chaînes de connexion suivantes :  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 Avec la première chaîne, le pilote n’est pas nécessaire d’autres informations. Avec la deuxième chaîne, le pilote doit demander le nom du répertoire contenant les fichiers de données.
