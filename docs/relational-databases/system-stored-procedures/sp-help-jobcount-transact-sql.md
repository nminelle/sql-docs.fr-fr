---
title: sp_help_jobcount (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_jobcount
- sp_help_jobcount_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_jobcount
ms.assetid: ae8ef851-646c-4889-bc11-c8ec78762572
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eae74b9745c8b5ad4f5e2cc5b9268e5a297b03b2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sphelpjobcount-transact-sql"></a>sp_help_jobcount (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Indique le nombre de travaux auxquels une planification est attachée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_jobcount   
     [ @schedule_name = ] 'schedule_name' ,  
     [ @schedule_id = ] schedule_id   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@schedule_id=** ] *id_de_la_planification*  
 Identificateur de la planification à répertorier. *id_de_la_planification* est **int**, sans valeur par défaut. Soit *id_de_la_planification* ou *nom_de_la_planification* peut être spécifié.  
  
 [  **@schedule_name=** ] **'***nom_de_la_planification***'**  
 Nom de la planification à répertorier. *nom_de_la_planification* est **sysname**, sans valeur par défaut. Soit *id_de_la_planification* ou *nom_de_la_planification* peut être spécifié.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne le jeu de résultats suivant :  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**JobCount**|**int**|Nombre de travaux pour la planification spécifiée.|  
  
## <a name="remarks"></a>Notes  
 Cette procédure indique le nombre de travaux attachés à la planification spécifiée.  
  
## <a name="permissions"></a>Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Seuls les membres du **sysadmin** peuvent afficher le nombre de travaux qui est détenus par d’autres.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant indique le nombre de travaux attachés à la planification `NightlyJobs`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_jobcount  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [L’Agent SQL Server stockées procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  