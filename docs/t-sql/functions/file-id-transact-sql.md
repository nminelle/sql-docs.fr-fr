---
title: FILE_ID (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILE_ID
- FILE_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IDs [SQL Server], files
- file IDs [SQL Server]
- FILE_ID function
- names [SQL Server], files
- identification numbers [SQL Server], files
- file names [SQL Server], FILE_ID
ms.assetid: 6a7382cf-a360-4d62-b9d2-5d747f56f076
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1b2025ee9fdc5ca0aaf4967305db40cb65d038c
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="fileid-transact-sql"></a>FILE_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie le numéro d'identification (ID) du fichier correspondant au nom du fichier logique donné dans la base de données actuelle.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FILE_ID ( file_name )  
```  
  
## <a name="arguments"></a>Arguments  
 *file_name*  
 Expression de type **sysname** qui représente le nom du fichier dont l’ID doit être retourné.  
  
## <a name="return-types"></a>Types de retour  
 **smallint**  
  
## <a name="remarks"></a>Notes   
 *file_name* correspond au nom de fichier logique affiché dans la colonne name de la vue de catalogue sys.master_files ou sys.database_files.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le numéro d'identification de fichier assigné aux catalogues de texte intégral est supérieur à 32767. Le type de retour de la fonction FILE_ID étant **smallint**, cette fonction ne peut pas être utilisée pour les fichiers de texte intégral. Utilisez plutôt [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne l'ID du fichier `AdventureWorks_Data`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT FILE_ID('AdventureWorks2012_Data')AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Fonctionnalités du moteur de base de données dépréciées dans SQL Server 2016](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [FILE_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/file-name-transact-sql.md)   
 [Fonctions de métadonnées &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
