---
title: MSSQLSERVER_17084 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 17084 (Database Engine error)
ms.assetid: e579d104-3307-4edd-8587-b14ecbc02ed9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f10551994eca2a51b7add925c4680759851a3b11
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver17084"></a>MSSQLSERVER_17084
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|17084|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|P3_ATOMIC_WITH_MISSING_OPTION|  
|Texte du message|La clause WITH de l'instruction BEGIN ATOMIC doit spécifier une valeur pour l'option « %ls ».|  
  
## <a name="explanation"></a>Explication  
La clause WITH de l'instruction BEGIN ATOMIC n'a pas spécifié de valeur pour une option.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Les blocs **ATOMIC** requièrent des valeurs pour les options **WITH** **TRANSACTION ISOLATION LEVEL** et **LANGUAGE**. Par exemple :  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N’us_english’)  
```  
  
Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
