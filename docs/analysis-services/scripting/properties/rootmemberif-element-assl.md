---
title: "Élément RootMemberIf (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: RootMemberIf Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: RootMemberIf
helpviewer_keywords: RootMemberIf element
ms.assetid: b695e271-c748-4abc-a09f-acb1014f768f
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c5a3a75efa13710bcc00a94ed55cee407dbbbc8d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="rootmemberif-element-assl"></a>Élément RootMemberIf (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Détermine la manière dont le membre racine ou les membres d’un attribut parent sont identifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <RootMemberIf>...</RootMemberIf>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*ParentIsBlankSelfOrMissing*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes   
 La valeur de la **RootMemberIf** élément est utilisé uniquement par les attributs parents (en d’autres termes, la valeur de la [utilisation](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) élément de la **DimensionAttribute** élément parent a la valeur *Parent*) pour déterminer les membres (plus haut) de la racine d’une hiérarchie parent-enfant.  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|Seuls les membres qui satisfont à une ou plusieurs des conditions décrites pour *ParentIsBlank*, *ParentIsSelf*, ou *ParentIsMissing* sont traités en tant que membres racines.|  
|*ParentIsBlank*|Seuls les membres avec une valeur null, un zéro ou une chaîne vide dans les colonnes clés représentées par le [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md) collection de **DimensionAttribute** sont traités en tant que membres racines.|  
|*ParentIsSelf*|Seuls les membres qui sont parents d'eux-mêmes sont traités en tant que membres racines.|  
|*ParentIsMissing*|Seuls les membres dont les parents sont introuvables sont traités en tant que membres racines.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **RootMemberIf** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.RootIfValue>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
