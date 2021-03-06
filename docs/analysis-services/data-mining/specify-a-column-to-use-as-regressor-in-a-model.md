---
title: "Spécifier une colonne à utiliser comme régresseur dans un modèle | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8e0cb8e-302a-4166-9ed0-e2d9e2919b0a
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3f97137b00c611c1be5671f52d8e23cefb8c7c55
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="specify-a-column-to-use-as-regressor-in-a-model"></a>Spécifier une colonne à utiliser comme régresseur dans un modèle
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Un modèle de régression linéaire représente la valeur de l’attribut prédictible comme résultat d’une formule qui combine les entrées de telle sorte que les données sont ajustées le mieux possible à une ligne de régression estimée. L'algorithme accepte uniquement les valeurs numériques comme entrées, et détecte automatiquement les entrées qui sont le mieux adaptées.  
  
 Vous pouvez toutefois spécifier qu'une colonne soit incluse en tant que régresseur en ajoutant le paramètre FORCE_REGRESSOR au modèle et en spécifiant les régresseurs à utiliser. Ce peut être le cas lorsque l'attribut a une signification même si l'effet est trop limité pour être détecté par le modèle, ou lorsque vous voulez vous assurer que l'attribut est inclus dans la formule.  
  
 La procédure suivante explique comment créer un modèle de régression linéaire simple, en utilisant le même exemple de données que celui utilisé pour le [didacticiel sur les réseaux neuronaux](http://msdn.microsoft.com/library/42c3701a-1fd2-44ff-b7de-377345bbbd6b). Le modèle n'est pas nécessairement fiable, mais il montre comment utiliser le Concepteur d'exploration de données pour personnaliser un modèle de régression linéaire.  
  
### <a name="how-to-create-a-simple-linear-regression-model"></a>Procédure de création d'un modèle de régression linéaire simple  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dans l’ **Explorateur de solutions**, développez **Structures d’exploration de données**.  
  
2.  Double-cliquez sur Call Center.dmm pour l'ouvrir dans le concepteur.  
  
3.  Dans le menu **Modèle d’exploration de données** , sélectionnez **Nouveau modèle d’exploration de données**.  
  
4.  Pour l’algorithme, sélectionnez **MLR (Microsoft Linear Regression)**. Pour le nom, tapez **Call Center Regression**.  
  
5.  Sous l’onglet **Modèles d’exploration de données** , modifiez l’utilisation des colonnes de la façon suivante. La valeur **Ignorer**doit être affectée à toutes les colonnes ne figurant pas dans la liste suivante, si ce n’est pas déjà fait.  
  
     FactCallCenterID**Key**  
  
     ServiceGrade**PredictOnly**  
  
     Total Operators**Input**  
  
     AverageTimePerIssue**Input**  
  
6.  Dans le menu **Modèle d’exploration de données** , sélectionnez **Définir les paramètres du modèle**.  
  
7.  Pour le paramètre FORCE_REGRESSOR, dans la colonne **Valeur** , tapez les noms de colonnes entre crochets et séparés par une virgule, comme suit :  
  
    ```  
    [Average Time Per Issue],[Total Operators]  
    ```  
  
    > [!NOTE]  
    >  L'algorithme détectera automatiquement les colonnes qui constituent les meilleurs régresseurs. Vous devez uniquement forcer l'utilisation des régresseurs lorsque vous voulez vous assurer qu'une colonne est incluse dans la formule finale.  
  
8.  Dans le menu **Modèle d’exploration de données** , sélectionnez **Traiter le modèle**.  
  
     Dans la visionneuse, le modèle est représenté sous la forme d'un nœud unique contenant la formule de régression. Vous pouvez afficher la formule dans la **Légende d’exploration de données**, ou extraire les coefficients de la formule à l’aide de requêtes.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme MLR (Microsoft Linear Regression)](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)   
 [Requêtes d'exploration de données](../../analysis-services/data-mining/data-mining-queries.md)   
 [Référence technique de Microsoft Linear Regression algorithme](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)   
 [Contenu du modèle d’exploration de données pour les modèles de régression linéaire &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
