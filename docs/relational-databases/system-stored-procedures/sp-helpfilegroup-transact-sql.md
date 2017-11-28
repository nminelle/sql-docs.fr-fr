---
title: sp_helpfilegroup (Transact-SQL) | Documents Microsoft
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
- sp_helpfilegroup_TSQL
- sp_helpfilegroup
dev_langs: TSQL
helpviewer_keywords: sp_helpfilegroup
ms.assetid: 619716b5-95dc-4538-82ae-4b90b9da8ebc
caps.latest.revision: "35"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d70701850b1dbeff112f0d8683aa9e8b422722c3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpfilegroup-transact-sql"></a>sp_helpfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie le nom et les attributs des groupes de fichiers associés à la base de données active.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpfilegroup [ [ @filegroupname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@filegroupname =** ] **'***nom***'**  
 Nom logique des groupes de fichiers de la base de données active. *nom* est **sysname**, avec NULL comme valeur par défaut. Si *nom* n’est pas spécifié, tous les groupes de fichiers dans la base de données actuelle sont répertoriées et uniquement le premier jeu de résultats dans la section des jeux de résultats s’affiche.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**nom de groupe**|**sysname**|Nom du groupe de fichiers|  
|**GroupID**|**smallint**|Identificateur numérique du groupe de fichiers.|  
|**FileCount**|**int**|Nombre de fichiers appartenant au groupe de fichiers.|  
  
 Si *nom* est spécifié, une ligne pour chaque fichier dans le groupe de fichiers est retournée.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**file_in_group**|**sysname**|Nom logique du fichier dans le groupe de fichiers.|  
|**fileid**|**smallint**|Identificateur numérique du fichier.|  
|**nom de fichier**|**NCHAR(260)**|Nom physique du fichier, y compris le chemin d'accès du répertoire.|  
|**taille**|**nvarchar (15)**|Taille du fichier en kilo-octets.|  
|**MaxSize**|**nvarchar (15)**|Taille maximale du fichier.<br /><br /> Taille maximale que peut atteindre le fichier. La valeur UNLIMITED indique que le fichier peut augmenter jusqu'à ce que le disque soit plein.|  
|**croissance**|**nvarchar (15)**|Incrément de croissance du fichier. Quantité d'espace ajoutée au fichier chaque fois que de l'espace supplémentaire est nécessaire.<br /><br /> 0 = La taille du fichier est fixe et n'augmente pas.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-all-filegroups-in-a-database"></a>A. Renvoi de tous les groupes de fichiers d'une base de données  
 L'exemple suivant renvoie des informations sur les groupes de fichiers dans la base de données exemple [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```tsql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup;  
GO  
```  
  
### <a name="b-returning-all-files-in-a-filegroup"></a>B. Renvoi de tous les fichiers d'un groupe de fichiers  
 L'exemple suivant renvoie des informations sur tous les fichiers du groupe de fichiers `PRIMARY` dans la base de données exemple [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```tsql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup 'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de base de données stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfile &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [Sys.master_files &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Sys.FileGroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Groupes de fichiers et fichiers de base de données](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  