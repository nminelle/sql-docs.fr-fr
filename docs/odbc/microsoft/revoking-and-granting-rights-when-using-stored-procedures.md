---
title: "Révocation et accorder des droits lors de l’utilisation de procédures stockées | Documents Microsoft"
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
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 24070039-03ab-4623-a681-6308802eb399
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b2a34667e08e767a77f31917f5c373b795c7324
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Révocation et accorder des droits lors de l’utilisation de procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle retourne le message d’erreur suivant lorsque des droits d’utilisateur sont accordées et puis révoquées sur une table accédée par une procédure stockée :  
  
 SQL_ERROR =-1  
  
 szErrorMsg = « [Microsoft] [pilote ODBC pour Oracle] nombre de paramètres incorrect »  
  
 szErrorMsg = « [Microsoft] [pilote ODBC pour Oracle] syntaxe ou violation d’accès »  
  
 L’appel à la fonction Oracle OCI Odessp() échoue dans ce scénario, mais est nécessaire pour implémenter les paramètres par défaut. Une fois les autorisations de la table sous-jacente sont modifiées, la procédure stockée doit être recompilée avant d’exécuter à nouveau.
