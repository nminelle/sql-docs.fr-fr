---
title: sp_helpremotelogin (Transact-SQL) | Documents Microsoft
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
- sp_helpremotelogin_TSQL
- sp_helpremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpremotelogin
ms.assetid: 93f50869-2627-4642-899f-8f626f8833f4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b34842bc6265d9a1615cb1f2e45d727b257a5c90
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpremotelogin-transact-sql"></a>sp_helpremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur les connexions distantes d'un serveur distant spécifique ou de tous les serveurs distants, définis sur le serveur local.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Utilisez des serveurs liés et des procédures stockées de serveur lié à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpremotelogin [ [ @remoteserver = ] 'remoteserver' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @remoteserver  **=**  ] **'***remoteserver***'**  
 Nom du serveur distant sur lequel les informations relatives à la connexion distante sont retournées. *RemoteServer* est **sysname**, avec NULL comme valeur par défaut. Si *remoteserver* est ne pas spécifié, les informations sur tous les serveurs distants définis sur le serveur local sont retournées.  
  
 [ @remotename  **=**  ] **'***nom_distant***'**  
 Connexion distante spécifique du serveur distant. *nom_distant* est **sysname**, avec NULL comme valeur par défaut. Si *nom_distant* n’est pas spécifié, les informations sur tous les utilisateurs distants définis pour *remoteserver* est retourné.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|server|**sysname**|Nom d'un serveur distant défini sur le serveur local.|  
|local_user_name|**sysname**|Connexion du serveur local à laquelle sont mappées les connexions distantes.|  
|remote_user_name|**sysname**|Ouverture de session sur le serveur distant qui est mappée à local_user_name.|  
|options|**sysname**|Trusted = La connexion distante n'a pas à fournir de mot de passe lors de la connexion au serveur local à partir du serveur distant.<br /><br /> Untrusted (ou vide) = La connexion distante doit fournir un mot de passe lors de la connexion au serveur local à partir du serveur distant.|  
  
## <a name="remarks"></a>Notes  
 Faites appel à sp_helpserver pour répertorier les noms des serveurs distants définis sur le serveur local.  
  
## <a name="permissions"></a>Permissions  
 Aucuns autorisations ne sont vérifiées.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-reporting-help-on-a-single-server"></a>A. Affichage de l'aide sur un seul serveur  
 L'exemple suivant affiche des informations sur tous les utilisateurs distants du serveur distant `Accounts`.  
  
```  
EXEC sp_helpremotelogin 'Accounts';  
```  
  
### <a name="b-reporting-help-on-all-remote-users"></a>B. Affichage de l'aide sur tous les utilisateurs distants  
 L'exemple suivant affiche des informations sur tous les utilisateurs distants de tous les serveurs distants connus sur le serveur local.  
  
```  
EXEC sp_helpremotelogin;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addremotelogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_dropremotelogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
