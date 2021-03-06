---
title: DrilldownLevelTop (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: DRILLDOWNLEVELTOP
dev_langs: kbMDX
helpviewer_keywords: DrilldownLevelTop function
ms.assetid: b3b45dd6-2ade-4dd7-83dd-849231e2e517
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f4f3454f14371a7d75cf04f18ba69f11bce6d71f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="drilldownleveltop-mdx"></a>DrilldownLevelTop (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Extrait vers le bas les membres les plus hauts d'un jeu, d'un niveau à partir du niveau spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DrilldownLevelTop(<Set_Expression>, <Count> [,[<Level_Expression>] [,[<Numeric_Expression>][,INCLUDE_CALC_MEMBERS]]])  
  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Nombre*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
 *Numeric_expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
 *Include_Calc_Members*  
 Mot clé pour ajouter les membres calculés aux résultats de l'extraction vers le bas.  
  
## <a name="remarks"></a>Notes   
 Si une expression numérique est spécifiée, la **DrilldownLevelTop** fonction trie, par ordre décroissant, les enfants de chaque membre dans le jeu spécifié en fonction de la valeur de l’expression numérique, telle qu’évaluée sur le jeu de membres enfants. Si une expression numérique n'est pas spécifiée, cette fonction trie, par ordre décroissant, les enfants de chaque membre dans le jeu spécifié selon les valeurs des cellules représentées par le jeu des membres enfants, comme le détermine le contexte de la requête.  
  
 Après le tri, le **DrilldownLevelTop** fonction retourne un jeu qui contient les membres parents et le nombre de membres enfants spécifiés dans *Count,* avec la valeur la plus élevée.  
  
 Le **DrilldownLevelTop** fonction est similaire à la [DrilldownLevel](../mdx/drilldownlevel-mdx.md) (fonction), mais au lieu d’inclure tous les enfants de chaque membre au niveau spécifié, le **DrilldownLevelTop** fonction retourne le premier nombre de membres enfants.  
  
 Interrogez la propriété XMLA MdpropMdxDrillFunctions vous permet de vérifier le niveau de prise en charge par le serveur pour les fonctions d’extraction ; consultez [pris en charge les propriétés XMLA &#40; XMLA &#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) pour plus d’informations.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne les trois enfants supérieurs du niveau Product Category en fonction de la mesure par défaut. Dans l'exemple de cube Adventure Works, les trois premiers enfants pour Accessories sont Bike Racks, Bike Stands et Bottles and Cages. Dans Management Studio, dans la fenêtre de requête MDX, vous pouvez accéder à Products | Product Categories | Members | All Products | Accessories pour afficher la liste complète. Vous pouvez augmenter l'argument Count pour retourner davantage de membres.  
  
```  
SELECT DrilldownLevelTop   
   ([Product].[Product Categories].children,  
   3,  
   [Product].[Product Categories].[Category])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 L’exemple suivant illustre l’utilisation de la **include_calc_members** indicateur, utilisé pour inclure les membres calculés dans le niveau de zoom. La mesure [Reseller Order Count] est incluse dans le **DrilldownLevelTop** instruction pour vous assurer que les valeurs de retour sont triés par cette mesure.  
  
```  
WITH MEMBER   
[Product].[Product Categories].[Category].&[3].[Premium Clothes] AS  
[Product].[Product Categories].[Subcategory].&[18] +  
[Product].[Product Categories].[Subcategory].&[21]  
SELECT [Measures].[Reseller Order Count] ON 0,  
DRILLDOWNLEVELTOP(  
  [Product].[Product Categories].children ,  
  2,  
  [Product].[Product Categories].[Category] ,  
  [Measures].[Reseller Order Count],  
  INCLUDE_CALC_MEMBERS ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DrilldownLevel &#40; MDX &#41;](../mdx/drilldownlevel-mdx.md)   
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
