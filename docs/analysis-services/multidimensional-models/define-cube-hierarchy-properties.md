---
title: "Définir des propriétés de hiérarchie de Cube | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 13934070e4121913b82a2604acf26581cf27796f
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="define-cube-hierarchy-properties"></a>Définir les propriétés des hiérarchies de cube
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Les propriétés des hiérarchies de cube vous permettent de spécifier des paramètres uniques pour les hiérarchies définies par l'utilisateur des dimensions de cube à partir de la même dimension de base de données. Le tableau suivant décrit les propriétés d'une hiérarchie de cube.  
  
|Propriété| Description|  
|--------------|-----------------|  
|**Activé**|Détermine si la hiérarchie est activée pour la dimension de cube.|  
|**HierarchyID**|Contient l'identificateur unique (ID) de la hiérarchie.|  
|**OptimizedState**|Détermine le niveau d'optimisation appliqué à la hiérarchie. Cette propriété peut avoir les valeurs suivantes :<br /><br /> **FullyOptimized**:<br />                    L'instance construit des index pour la hiérarchie afin d'augmenter les performances en matière de requêtes. Ceci est la valeur par défaut.<br /><br /> **NotOptimized**:<br />                    L'instance ne construit pas d'index supplémentaire.|  
|**Visible**|Détermine la visibilité de la hiérarchie du cube. La valeur par défaut est **True**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchies des utilisateurs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
