---
title: sys.dm_db_log_space_usage (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.dm_db_log_space_usage
- sys.dm_db_log_space_usage_TSQL
- dm_db_log_space_usage
- dm_db_log_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_log_space_usage dynamic management view
ms.assetid: f6b40060-c17d-472f-b0a3-3b350275d487
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: df77bbd3302f73e898fbb4ef053810492819c89e
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmdblogspaceusage-transact-sql"></a>sys.dm_db_log_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Retourne l’espace informations d’utilisation pour le journal des transactions. 
  
> [!NOTE]
> Tous les fichiers journaux des transactions sont combinées.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|ID de la base de données.|  
|total_log_size_in_bytes |**bigint** |La taille du journal  |
|used_log_space_in_bytes |**bigint** |La taille du journal d’occupé  |     
|used_log_space_in_percent |**real** |La taille occupée du journal en tant que pourcentage de la taille du journal |
|log_space_in_bytes_since_last_backup |**bigint** |La quantité d’espace utilisée depuis la dernière sauvegarde de journal <br />**S’applique à :** [!INCLUDE[sssql14-md](../../includes/sssql14-md.md)] via [!INCLUDE[sscurrent-md](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|
    
  
## <a name="permissions"></a>Autorisations  
 Sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert `VIEW SERVER STATE` autorisation sur le serveur.  
  
 Sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] niveaux Premium requiert le `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard et les niveaux de base nécessite le [!INCLUDE[ssSDS](../../includes/sssds-md.md)] compte d’administrateur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-determine-the-amount-of-free-log-space-in-tempdb"></a>A. Déterminer la quantité de journal espace dans tempdb   
La requête suivante retourne l’espace de journal total en mégaoctets (Mo) disponible dans tempdb.

```sql
USE tempdb;  
GO  

SELECT (total_log_size_in_bytes - used_log_space_in_bytes)*1.0/1024/1024 AS [free log space in MB]  
FROM sys.dm_db_log_space_usage;  
```
  
## <a name="see-also"></a>Voir aussi  
[Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Base de données associés des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_file_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)    
[sys.dm_db_task_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
[sys.dm_db_session_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)  
[sys.dm_db_log_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md)    
[sys.dm_db_log_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md) 



