---
title: "Abandonner les modifications apportées aux requêtes (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reverting queries
- queries [SQL Server], discarding changes
- discarding query changes
ms.assetid: 7bb17ece-1222-4622-b476-5789d7641c64
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5412ede653f8bd6eb67091dd4ebc532b1d7f1b19
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="discard-changes-made-to-queries-visual-database-tools"></a>Abandonner les modifications apportées aux requêtes (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Vous pouvez abandonner les changements apportés à une définition de requête avant de les enregistrer. Une fois enregistrées, leur état antérieur ne peut pas être rétabli.  
  
> [!NOTE]  
> Pour annuler une modification apportée à des valeurs dans le volet Résultats, appuyez sur la touche Échap avant de quitter l'enregistrement. Si, lorsque vous quittez un enregistrement, un message vous avertit que les modifications ne seront pas validées dans la base de données, vous pouvez également appuyer sur la touche Échap pour rétablir la valeur antérieure.  
  
### <a name="to-discard-changes-made-to-a-query-definition"></a>Pour ignorer les modifications apportées à une définition de requête  
  
1.  Quand la requête est ouverte dans le Concepteur de requêtes et de vues, cliquez sur **Fermer** dans le menu **Fichier**.  
  
2.  Dans la boîte de dialogue **Microsoft SQL Server Management Studio** , cliquez sur **Non**.  
  
    La définition de requête retrouve l'état qui était le sien lors du dernier enregistrement.  
  
## <a name="see-also"></a> Voir aussi  
[Enregistrer des requêtes (Visual Database Tools)](../../ssms/visual-db-tools/save-queries-visual-database-tools.md)  
[Rubriques de procédures relatives à la conception de requêtes et de vues (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Effectuer des opérations de base concernant les requêtes (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[Utiliser des données du volet de résultats (Visual Database Tools)](../../ssms/visual-db-tools/work-with-data-in-the-results-pane-visual-database-tools.md)  
  
