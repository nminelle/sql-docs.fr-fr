---
title: sys.service_queue_usages (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.service_queue_usages
- sys.service_queue_usages_TSQL
- service_queue_usages
- service_queue_usages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_queue_usages catalog view
ms.assetid: d58dcdaf-f82d-43d9-941b-f520581442bf
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e70dfba1094f4845c345ed212673918b270e6ac
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysservicequeueusages-transact-sql"></a>sys.service_queue_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cet affichage catalogue retourne une ligne pour chaque référence entre un service et la file d'attente du service. Un service peut être associé à une seule file d'attente. Une file d'attente peut être associée à plusieurs services.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**service_id**|**int**|ID du service. Unique dans la base de données. Cette colonne n'accepte pas la valeur NULL.|  
|**service_queue_id**|**int**|ID de la file d'attente utilisée par le service. Cette colonne n'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [sys.services &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-services-transact-sql.md)  
  
  
