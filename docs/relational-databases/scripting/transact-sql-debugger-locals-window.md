---
title: "Variables locales, fenêtre | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.locals
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 12634c2ab4acec714dbedb4aa41aa45e7bc8ef4c
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2018
---
# <a name="transact-sql-debugger---locals-window"></a>Débogueur Transact-SQL - Fenêtre Variables locales
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] La fenêtre **Variables locales** affiche des informations sur les expressions locales dans l’étendue actuelle du débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'étendue est définie selon le frame de pile des appels actuellement sélectionné dans la fenêtre **Pile des appels** . Vous devez être en mode débogage pour afficher les expressions locales.  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour accéder à la fenêtre Variables locales**  
  
-   Dans le menu **Déboguer** , cliquez sur **Fenêtres**, puis sur **Variables locales**.  
  
 **Pour modifier la valeur d'une expression**  
  
-   Cliquez avec le bouton droit sur l’expression, puis sélectionnez **Modifier la valeur**.  
  
## <a name="columns"></a>Colonnes  
 **Nom**  
 Nom de l'expression locale. Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] répertorie les variables, les paramètres et les fonctions système dont les noms commencent par @@.  
  
 **Value**  
 Affiche la valeur actuellement assignée à l'expression locale. Cette colonne est vide si aucune valeur n'a été assignée à l'expression.  
  
 Si la longueur d'une expression dépasse la largeur de la colonne **Valeur** , une info-bulle affiche la valeur complète lorsque vous placez le pointeur sur la cellule **Valeur** de cette expression.  
  
 La présence d'une icône de loupe dans une cellule **Valeur** indique que le visualiseur du débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] est disponible. Dans la liste, vous pouvez spécifier **Visualiseur de texte**, **Visualiseur XML**ou **Visualiseur HTML**. Pour démarrer un visualiseur du débogueur, cliquez sur l'icône de loupe. Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] ouvre une boîte de dialogue qui affiche les données dans un format adapté au type de données.  
  
 **Type**  
 Affiche le type de données de l'expression.  
  
## <a name="see-also"></a> Voir aussi  
 [Débogueur Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Informations du débogueur Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [Espion (fenêtre)](../../relational-databases/scripting/transact-sql-debugger-watch-window.md)   
 [Fenêtre Pile des appels](../../relational-databases/scripting/transact-sql-debugger-call-stack-window.md)   
 [Boîte de dialogue Espion express](../../relational-databases/scripting/transact-sql-debugger-quickwatch-dialog-box.md)   
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
