---
title: APPLOCK_MODE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- APPLOCK_MODE_TSQL
- APPLOCK_MODE
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], applications
- applications [SQL Server], locks
- sessions [SQL Server], application locks
- APPLOCK_MODE function
ms.assetid: e43d4917-77f1-45cc-b231-68ba7fee3385
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b6b5c0a0879580e5c1e084259b61ff206d49c896
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="applockmode-transact-sql"></a>APPLOCK_MODE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Renvoie le mode de verrouillage détenu par le propriétaire du verrou sur une ressource d'application particulière. APPLOCK_MODE est une fonction de verrouillage d'application qui agit sur la base de données active. L'étendue des verrous d'application est la base de données.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
APPLOCK_MODE( 'database_principal' , 'resource_name' , 'lock_owner' )  
```  
  
## <a name="arguments"></a>Arguments  
'*database_principal*'  
Utilisateur, rôle ou rôle d'application qui peut se voir octroyer des autorisations sur des objets dans la base de données. L’appelant de la fonction doit être membre du rôle de base de données fixe *database_principal*, dbo ou db_owner pour pouvoir appeler la fonction.
  
'*resource_name*'  
Nom de ressource de verrou spécifié par l'application cliente. L'application doit vérifier que le nom de ressource est unique. Le nom spécifié est haché en interne en une valeur qui peut être stockée dans le gestionnaire de verrous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *resource_name* est de type **nvarchar(255)**, sans valeur par défaut. L’argument *resource_name* est évalué en binaire et respecte la casse, quels que soient les paramètres de classement de la base de données active.
  
'*lock_owner*'  
Propriétaire du verrou, qui est la valeur de *lock_owner* lorsque le verrou a été demandé. *lock_owner* est de type **nvarchar(32)** et sa valeur peut être **Transaction** (valeur par défaut) ou **Session**.
  
## <a name="return-types"></a>Types de retour
**nvarchar(32)**
  
## <a name="return-value"></a>Valeur retournée
Renvoie le mode de verrouillage détenu par le propriétaire du verrou sur une ressource d'application particulière. Le mode de verrouillage peut avoir une des valeurs suivantes :
  
||||  
|-|-|-|  
|**NoLock**|**Update**|**\*SharedIntentExclusive**|  
|**IntentShared**|**IntentExclusive**|**\*UpdateIntentExclusive**|  
|**Shared**|**Exclusive**||  
  
*Ce mode de verrouillage est une combinaison d'autres modes de verrouillage ; il n'est pas possible de l'acquérir explicitement en utilisant sp_getapplock.
  
## <a name="function-properties"></a>Propriétés de la fonction
**Non déterministe**
  
**Non indexable**
  
**Non parallélisable**
  
## <a name="examples"></a>Exemples  
Deux utilisateurs (A et B) exécutent la suite d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante dans des sessions différentes.
  
L'utilisateur A exécute :
  
```sql
USE AdventureWorks2012;  
GO  
BEGIN TRAN;  
DECLARE @result int;  
EXEC @result=sp_getapplock  
    @DbPrincipal='public',  
    @Resource='Form1',  
    @LockMode='Shared',  
    @LockOwner='Transaction';  
SELECT APPLOCK_MODE('public', 'Form1', 'Transaction');  
GO  
```  
  
L'utilisateur B exécute :
  
```sql
Use AdventureWorks2012;  
GO  
BEGIN TRAN;  
SELECT APPLOCK_MODE('public', 'Form1', 'Transaction');  
--Result set: NoLock  
  
SELECT APPLOCK_TEST('public', 'Form1', 'Shared', 'Transaction');  
--Result set: 1 (Lock is grantable.)  
  
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: 0 (Lock is not grantable.)  
GO  
```  
  
L'utilisateur A exécute ensuite :
  
```sql
EXEC sp_releaseapplock @Resource='Form1', @DbPrincipal='public';  
GO  
```  
  
L'utilisateur B exécute :
  
```sql
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: '1' (The lock is grantable.)  
GO  
```  
  
Les utilisateurs A et B exécutent ensuite :
  
```sql
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi
[APPLOCK_TEST &#40;Transact-SQL&#41;](../../t-sql/functions/applock-test-transact-sql.md)  
[sp_getapplock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
[sp_releaseapplock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)
  
  
