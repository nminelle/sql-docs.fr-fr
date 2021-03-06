---
title: Sys.column_master_keys (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- column_master_key_definitions_TSQL
- column_master_key_definitions
- sys.column_master_key_definitions_TSQL
- sys.column_master_key_definitions
- column_master_keys_TSQL
- column_master_keys
- sys.column_master_keys_TSQL
- sys.column_master_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_key_definitions catalog view
- sys.column_master_keys catalog view
ms.assetid: fbec2efa-5fe9-4121-9b34-60497b0b2aca
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e22e052d88c339828e0a7e5d6f5803bc04b30925
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="syscolumnmasterkeys-transact-sql"></a>sys.column_master_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque clé principale de base de données ajouté à l’aide de la [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) instruction. Chaque ligne représente une clé principale de colonne (CMK).  
    
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Le nom de la clé CMK.|  
|**column_master_key_id**|**int**|ID de la clé principale de colonne.|  
|**create_date**|**datetime**|Date de que création de la clé principale de colonne.|  
|**modify_date**|**datetime**|Date de que dernière modification de la clé principale de colonne.|  
|**key_store_provider_name**|**sysname**|Nom du fournisseur pour le magasin de clés principales de colonne qui contient la clé CMK. Les valeurs autorisées sont :<br /><br /> MSSQL_CERTIFICATE_STORE – si le magasin de clés principales de colonne est un magasin de certificats.<br /><br /> Défini par l’utilisateur valeur, si le magasin de clés principales de colonne est d’un type personnalisé.|  
|**key_path**|**nvarchar(4000)**|Une colonne clé principale spécifique à la banque de chemin d’accès de la clé. Le format du chemin d’accès varie selon le type de magasin de clé principale de colonne. Exemple :<br /><br /> `'CurrentUser/Personal/'<thumbprint>`<br /><br /> Pour un magasin de clés principales de colonne personnalisée, le développeur est chargé de définir un chemin de clé est pour le magasin de clés principales de colonne personnalisé.|  
  
## <a name="permissions"></a>Permissions  
 Requiert le **VIEW ANY COLUMN MASTER KEY** autorisation.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Always Encrypted &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
  
  
