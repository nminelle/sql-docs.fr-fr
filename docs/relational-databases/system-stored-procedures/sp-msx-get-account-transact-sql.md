---
title: sp_msx_get_account (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_msx_get_account_TSQL
- sp_msx_get_account
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_get_account
ms.assetid: 7b478049-e2d0-4bac-865a-b97fd1d8dfbc
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8c25aa5896cb3256f77bf07df5b34af3c9637629
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="spmsxgetaccount-transact-sql"></a>sp_msx_get_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie les informations d'identification utilisées par le serveur cible pour se connecter au serveur maître.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_msx_get_account  
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne le jeu de résultats suivant :  
  
|Nom de la colonne|Type| Description|  
|-----------------|----------|-----------------|  
|msx_connection|**int**|Numéro de connexion du serveur maître.|  
|msx_credential_id|**int**|Identificateur des informations d'identification utilisées pour cette connexion au serveur maître.|  
|msx_credential_name|**sysname**|Nom des informations d'identification utilisées pour cette connexion au serveur maître.|  
|msx_login_name|**nvarchar(4000)**|Nom de domaine et nom de l'utilisateur Windows pour les informations d'identification.|  
  
## <a name="remarks"></a>Notes  
 Retourne un jeu de résultats vide si aucune information d'identification n'est spécifiée pour ce serveur cible. Pour définir les informations d'identification, utilisez sp_msx_set_account.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle serveur fixe sysadmin.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant répertorie les informations d'identification utilisées par ce serveur cible pour se connecter au serveur maître.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_get_account ;  
GO  
```  
  
 Voici un exemple d’ensemble de résultats :  
  
 `msx_connection msx_credential_id msx_credential_name  msx_login_name`  
  
 `-------------- ----------------- -------------------- ------------------------------`  
  
 `1              65538             MsxAccount           AdventureWorks2012\MsxAccount`  
  
## <a name="see-also"></a>Voir aussi  
 [L’Agent SQL Server stockées procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_set_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-set-account-transact-sql.md)  
  
  
