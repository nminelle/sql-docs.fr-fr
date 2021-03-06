---
title: sys.dm_pdw_resource_waits (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a43ce9a2-5261-41e3-97f0-555ba05ebed9
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a1cceb10fd8f1da138c1f7ff660d4764223e9394
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwresourcewaits-transact-sql"></a>sys.dm_pdw_resource_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Affiche attendre les informations pour tous les types de ressources dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Position de la demande dans la liste d’attente.|ordinal à partir de 0. Cela n’est pas unique pour toutes les entrées de l’attente.|  
|session_id|**nvarchar(32)**|ID de la session dans laquelle l’état d’attente s’est produite.|Consultez session_id dans [sys.dm_pdw_exec_sessions &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|type|**nvarchar(255)**|Type d’attente de que cette entrée représente.|Valeurs possibles :<br /><br /> Connexion<br /><br /> Simultanéité des requêtes local<br /><br /> Simultanéité des requêtes distribuées<br /><br /> Concurrence DMS<br /><br /> Concurrence de sauvegarde|  
|object_type|**nvarchar(255)**|Type d’objet affecté par l’attente.|Valeurs possibles :<br /><br /> **OBJECT**<br /><br /> **DATABASE**<br /><br /> **SYSTEM**<br /><br /> **SCHEMA**<br /><br /> **APPLICATION**|  
|object_name|**nvarchar(386)**|Nom ou le GUID de l’objet spécifié qui a été affectée par l’attente.|Tables et vues sont affichent avec des noms en trois parties.<br /><br /> Index et les statistiques sont affichées avec des noms en quatre parties.<br /><br /> Noms principaux et bases de données sont des noms de chaîne.|  
|request_id|**nvarchar(32)**|ID de la demande sur laquelle l’état d’attente s’est produite.|Identificateur QID de la demande.<br /><br /> Identificateur GUID pour les demandes de charge.|  
|request_time|**datetime**|Heure à laquelle le verrou ou la ressource a été demandée.||  
|acquire_time|**datetime**|Heure à laquelle le verrou ou la ressource a été acquis.||  
|state|**nvarchar(50)**|État de l’état d’attente.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Priorité de l’élément en attente.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|concurrency_slots_used|**int**|Nombre d’emplacements d’accès concurrentiel (32 max) réservé pour cette demande.|1 – pour SmallRC<br /><br /> 3 – pour MediumRC<br /><br /> 7 pour LargeRC<br /><br /> 22 : pour XLargeRC|  
|resource_class|**nvarchar(20)**|La classe de ressource pour cette demande.|SmallRC<br /><br /> MediumRC<br /><br /> LargeRC<br /><br /> XLargeRC|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de gestion dynamique de l’entrepôt de données en parallèle &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
