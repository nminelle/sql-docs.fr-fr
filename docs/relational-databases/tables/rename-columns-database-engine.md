---
title: "Renommer des colonnes (moteur de base de données) | Microsoft Docs"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [SQL Server], names
- renaming columns
- column names [SQL Server]
ms.assetid: 7c71ec9f-0180-4398-b32a-4bfb7592e75d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: 0bb8f1e02fa372e33174b2268584885808e25790
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="rename-columns-database-engine"></a>Renommer des colonnes (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Vous pouvez renommer une colonne de table dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour renommer des colonnes, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Si vous renommez une colonne, les références à cette colonne ne sont pas automatiquement renommées. Vous devez modifier manuellement tout objet qui référence la colonne renommée. Par exemple, si vous renommez une colonne de table et si cette colonne est référencée dans un déclencheur, vous devez modifier le déclencheur pour refléter le nouveau nom de colonne. Utilisez [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) pour obtenir la liste des dépendances de l’objet avant de le renommer.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert une autorisation ALTER sur l'objet.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-rename-a-column-using-object-explorer"></a>Pour renommer une colonne à l'aide de l'Explorateur d'objets  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur la table dans laquelle vous souhaitez renommer des colonnes et choisissez **Renommer**.  
  
3.  Tapez une nouvelle colonne.  
  
#### <a name="to-rename-a-column-using-table-designer"></a>Pour renommer une colonne à l'aide du Concepteur de tables  
  
1.  Dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur la table dans laquelle vous souhaitez renommer des colonnes et choisissez **Conception**.  
  
2.  Sous **Nom de la colonne**, sélectionnez le nom que vous souhaitez modifier et tapez-en un nouveau.  
  
3.  Dans le menu **Fichier**, cliquez sur **Enregistrer***nom de la table*.  
  
> [!NOTE]  
>  Vous pouvez également modifier le nom d'une colonne sous l'onglet **Propriétés des colonnes** . Sélectionnez la colonne dont vous souhaitez modifier le nom et tapez une nouvelle valeur pour **Nom**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour renommer une colonne**  
  
#### <a name="to-rename-a-column"></a>Pour renommer une colonne  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  L'exemple suivant renomme la colonne `TerritoryID` dans la table `Sales.SalesTerritory` en `TerrID`. Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md).  
  
  
