---
title: sys.fulltext_catalogs (Transact-SQL) | Microsoft Docs
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
- sys.fulltext_catalogs_TSQL
- sys.fulltext_catalogs
- fulltext_catalogs
- fulltext_catalogs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_catalogs catalog view
ms.assetid: cf1489ff-4819-41fa-a62a-4ed797a16207
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d4c3f1c279176dea69b27a2c1416af3d15338924
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysfulltextcatalogs-transact-sql"></a>sys.fulltext_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque catalogue de texte intégral.  
  
> [!NOTE]  
>  Les colonnes suivantes seront supprimées dans une future version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **data_space_id**, **file_id**, et **chemin d’accès**. Évitez d'utiliser ces colonnes dans de nouveaux travaux de développement et modifiez dès que possible les applications qui les utilisent actuellement.  
 
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|fulltext_catalog_id|**int**|Identificateur du catalogue de texte intégral. Il est unique parmi les catalogues de texte intégral de la base de données.|  
|name|**sysname**|Nom du catalogue. Unique dans la base de données.|  
|path|**nvarchar(260)**|Nom du répertoire du catalogue dans le système de fichiers.|  
|is_default|**bit**|Catalogue de texte intégral par défaut.<br /><br /> True = est la valeur par défaut.<br /><br /> False = n'est pas la valeur par défaut.|  
|is_accent_sensitivity_on|**bit**|Paramètre indiquant le respect des accents pour le catalogue.<br /><br /> True = respecte les accents.<br /><br /> False = ne respecte pas les accents.|  
|data_space_id|**int**|Groupe de fichiers dans lequel le catalogue a été créé.|  
|file_id|**int**|ID du fichier de texte intégral associé au catalogue.|  
|principal_id|**int**|ID du principal de base de données propriétaire du catalogue de texte intégral.|  
|is_importing|**bit**|Indique si le catalogue de texte intégral est en cours d'importation :<br /><br /> 1 = le catalogue est en cours d'importation.<br /><br /> 2 = le catalogue n'est pas en cours d'importation.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [CRÉER le catalogue de texte intégral &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [DROP FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)  
  
  
