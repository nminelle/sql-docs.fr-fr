---
title: sp_recompile (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_recompile_TSQL
- sp_recompile
dev_langs:
- TSQL
helpviewer_keywords:
- sp_recompile
ms.assetid: 6192ca87-febd-4075-8199-14b4fa609b8c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 200bf01ba1127281d5ff25b9c69f3616c4cf64bd
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="sprecompile-transact-sql"></a>sp_recompile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Provoque la recompilation des procédures stockées, des déclencheurs et des fonctions définies par l'utilisateur lors de leur prochaine exécution. Pour cela, il supprime le plan existant du cache de procédures, ce qui force la création d'un nouveau plan lors de la prochaine exécution de la procédure ou du déclencheur. Dans une collection [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], l'événement SP:CacheInsert est journalisé au lieu de l'événement SP:Recompile.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
  
sp_recompile [ @objname = ] 'object'  
```  
  
## <a name="arguments"></a>Arguments  
 [ @objname=] '*objet*'  
 Nom qualifié ou non qualifié d'une procédure stockée, d'un déclencheur, d'une table, d'une vue ou d'une fonction définie par l'utilisateur dans la base de données actuelle. *objet* est **nvarchar(776)**, sans valeur par défaut. Si *objet* est le nom d’un déclencheur de fonction définie par l’utilisateur, la procédure stockée, déclencheur ou procédure stocké ou fonction est recompilées lors de la prochaine fois qu’elle est exécutée. Si *objet* est le nom d’une table ou une vue, toutes les procédures stockées, les déclencheurs ou les fonctions définies par l’utilisateur qui font référence à la table ou vue seront recompilées lors de la prochaine fois qu’ils sont exécutés.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou un nombre différent de zéro (échec)  
  
## <a name="remarks"></a>Notes   
 sp_recompile ne recherche un objet que dans la base de données active.  
  
 Les requêtes utilisées par les procédures stockées ou les déclencheurs et les fonctions définies par l'utilisateur ne sont optimisées que quand elles sont compilées. À mesure que vous ajoutez des index à votre base de données ou que vous y apportez d'autres changements modifiant ses statistiques, les procédures stockées, les déclencheurs et les fonctions définies par l'utilisateur compilés peuvent perdre de leur efficacité. En recompilant les procédures stockées et les déclencheurs qui agissent sur une table, vous pouvez réoptimiser les requêtes.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recompile automatiquement les procédures stockées, les déclencheurs et les fonctions définies par l'utilisateur quand il est avantageux de le faire.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation ALTER pour l'objet spécifié.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant engendre la recompilation des procédures stockées, des déclencheurs et des fonctions définies par l'utilisateur qui agissent sur la table `Customer` lors de leur prochaine exécution.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_recompile N'Sales.Customer';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
