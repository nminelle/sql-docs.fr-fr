---
title: "Leçon supplémentaire de Analysis Services tutorial : les lignes de détails | Documents Microsoft"
description: "Décrit comment créer une Expression de lignes de détails dans le didacticiel Analysis Services."
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: 
author: Minewiskan
manager: kfile
editor: 
tags: 
ms.assetid: 
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
ms.openlocfilehash: 7efcdc724792656a917b95892ed699bc57590ce7
ms.sourcegitcommit: 7ed8c61fb54e3963e451bfb7f80c6a3899d93322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2018
---
# <a name="supplemental-lesson---detail-rows"></a>Leçon supplémentaire - les lignes de détails

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans cette leçon supplémentaire, vous utilisez l’éditeur DAX pour définir une Expression de lignes de détail personnalisée. Une Expression de lignes de détail est une propriété sur une mesure, en fournissant aux utilisateurs plus d’informations sur les résultats agrégés d’une mesure. 
  
Durée estimée pour effectuer cette leçon : **10 minutes**  
  
## <a name="prerequisites"></a>Configuration requise  

Cet article de la leçon supplémentaire fait partie d’un didacticiel de modélisation tabulaire. Avant d’effectuer les tâches de cette leçon supplémentaire, vous devez avoir terminé toutes les leçons précédentes ou avoir un projet de modèle d’exemple Adventure Works Internet Sales terminé.  
  
## <a name="whats-the-issue"></a>Quel est le problème ?

Examinons les détails de la mesure InternetTotalSales, avant d’ajouter une Expression de lignes de détail.

1.  Dans SSDT, cliquez sur le **modèle** menu > **analyser dans Excel** pour ouvrir Excel et créer un tableau croisé dynamique vide.
  
2.  Dans **PivotTable Fields**, ajoutez le **InternetTotalSales** mesure à partir de la table FactInternetSales **valeurs**, **CalendarYear** à partir de la table DimDate pour **colonnes**, et **EnglishCountryRegionName** à **lignes**. Le tableau croisé dynamique fournit maintenant des résultats agrégés dans la mesure InternetTotalSales par régions et l’année. 

    ![as-lesson-detail-rows-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-rows-pivottable.png)

3. Dans le tableau croisé dynamique, double-cliquez sur une valeur agrégée pour une année et un nom de région. Ici, nous avons double-cliqué sur la valeur de l’Australie et l’année 2014. Une nouvelle feuille s’ouvre, contenant des données, mais les données inutiles.

    ![as-lesson-detail-rows-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-rows-sheet.png)
  
Ce que nous voulons ici est une table contenant des colonnes et lignes de données qui contribuent au résultat de la mesure InternetTotalSales agrégé. Pour ce faire, nous pouvons ajouter une Expression de lignes de détail en tant que propriété de la mesure.

## <a name="add-a-detail-rows-expression"></a>Ajouter une Expression de lignes de détail

#### <a name="to-create-a-detail-rows-expression"></a>Pour créer une Expression de lignes de détail 
  
1. Dans la grille de mesures de la table FactInternetSales, cliquez sur le **InternetTotalSales** mesure. 

2. Dans **propriétés** > **Expression de lignes de détail**, cliquez sur le bouton de l’éditeur pour ouvrir l’éditeur DAX.

    ![as-lesson-detail-rows-ellipse](../tutorial-tabular-1400/media/as-lesson-detail-rows-ellipse.png)

3. Dans l’éditeur DAX, entrez l’expression suivante :

    ```
    SELECTCOLUMNS(
    FactInternetSales,
    "Sales Order Number", FactInternetSales[SalesOrderNumber],
    "Customer First Name", RELATED(DimCustomer[FirstName]),
    "Customer Last Name", RELATED(DimCustomer[LastName]),
    "City", RELATED(DimGeography[City]),
    "Order Date", FactInternetSales[OrderDate],
    "Internet Total Sales", [InternetTotalSales]
    )

    ```

    Cette expression spécifie les noms de colonnes, et les résultats de mesure à partir de la table FactInternetSales et les tables associées sont retournés lorsqu’un utilisateur double-clique sur un résultat agrégé dans un tableau croisé dynamique ou un rapport.

4. Dans Excel, supprimez de la feuille créée à l’étape 3, puis double-cliquez sur une valeur agrégée. Cette fois, avec une propriété d’Expression de lignes de détail définie pour la mesure, une nouvelle feuille s’ouvre contenant des données beaucoup plus utiles.

    ![as-lesson-detail-rows-detailsheet](../tutorial-tabular-1400/media/as-lesson-detail-rows-detailsheet.png)

5. Redéployer votre modèle.

  
## <a name="see-also"></a>Voir aussi  

[Fonction SELECTCOLUMNS (DAX)](https://msdn.microsoft.com/library/mt761759.aspx)  
[Leçon supplémentaire - Sécurité dynamique](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[Leçon supplémentaire - Hiérarchies déséquilibrées](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)  
