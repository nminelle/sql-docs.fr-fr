---
title: "Élément EstimatedRows (ASSL) | Documents Microsoft"
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
apiname: EstimatedRows Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: EstimatedRows
helpviewer_keywords: EstimatedRows element
ms.assetid: 08a66481-6479-4a93-aa7e-15e8b1f854f2
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2d230c46ae750a852cb57724675db8c3d15169e4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="estimatedrows-element-assl"></a>Élément EstimatedRows (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Contient le nombre estimé de lignes représentées par l’élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AggregationDesign> <!-- or Cube, MeasureGroup, MeasureGroupBinding, Partition -->  
   ...  
   <EstimatedRows>...</EstimatedRows>  
   ...  
</AggregationDimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Long|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md), [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md), [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes   
 Les éléments qui correspondent aux parents de **EstimatedRows** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.AggregationDesign>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.MeasureGroup>, <xref:Microsoft.AnalysisServices.MeasureGroupBinding>, et <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
