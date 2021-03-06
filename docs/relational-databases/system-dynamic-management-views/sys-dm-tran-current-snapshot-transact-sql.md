---
title: sys.dm_tran_current_snapshot (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_current_snapshot_TSQL
- dm_tran_current_snapshot
- dm_tran_current_snapshot_TSQL
- sys.dm_tran_current_snapshot
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_current_snapshot dynamic management view
ms.assetid: 7509d595-c0e1-4237-a5ac-b41ad934544c
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5cd469a45975ee2d86c11d076b0dceeec48d1a4d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmtrancurrentsnapshot-transact-sql"></a>sys.dm_tran_current_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une table virtuelle qui affiche toutes les transactions qui sont actives au moment où la transaction d'instantané active démarre. Si la transaction actuelle n'est pas une transaction d'instantané, cette fonction ne retourne aucune ligne. **Sys.dm_tran_current_snapshot** est similaire à **sys.dm_tran_transactions_snapshot**, sauf que **sys.dm_tran_current_snapshot** retourne uniquement les transactions actives pour la transaction d’instantané en cours.  
  
> [!NOTE]  
>  Pour appeler cette de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_tran_current_snapshot**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.dm_tran_current_snapshot  
```  
  
## <a name="table-returned"></a>Table retournée  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**transaction_sequence_num**|**bigint**|Numéro de séquence de la transaction active.|  
|pdw_node_id|**int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur du nœud qui se trouve sur cette distribution.|  
  
## <a name="permissions"></a>Autorisations  
 Sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert l’autorisation VIEW SERVER STATE sur le serveur.  
  
 Sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] niveaux Premium requiert l’autorisation VIEW DATABASE STATE dans la base de données. Sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard et les niveaux de base nécessite le [!INCLUDE[ssSDS](../../includes/sssds-md.md)] compte d’administrateur.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre un scénario de test dans lequel quatre transactions simultanées, chacune étant identifiée par un numéro de séquence de transaction, sont exécutées dans une base de données où les options ALLOW_SNAPSHOT_ISOLATION et READ_COMMITTED_SNAPSHOT sont définies à ON. Les transactions suivantes sont exécutées :  
  
-   XSN-57 est une opération Update exécutée avec le niveau d'isolement sérialisable.  
  
-   XSN-58 est identique à XSN-57.  
  
-   XSN-59 est une opération Select exécutée avec le niveau d'isolement d'instantané.  
  
-   XSN-60 est identique à XSN-59.  
  
 La requête suivante est exécutée dans l'étendue de XSN-59.  
  
```  
SELECT   
    transaction_sequence_num  
  FROM sys.dm_tran_current_snapshot;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
transaction_sequence_num  
------------------------  
57  
58  
```  
  
 Les résultats indiquent que XSN-57 et XSN-58 étaient actives au moment où la transaction d'instantané XSN-59 a démarré. Ce même résultat persiste, même après la validation ou l'annulation de XSN-57 et XSN-58, jusqu'à la fin de la transaction d'instantané.  
  
 La même requête est exécutée dans l'étendue de XSN-60.  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
transaction_sequence_num  
------------------------  
57  
58  
59  
```  
  
 La sortie de XSN-60 inclut les mêmes transactions que celles qui apparaissent pour XSN-59, mais elle inclut également XSN-59, qui était active lorsque XSN-60 a démarré.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Fonctions et vues de gestion dynamique relatives aux transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


