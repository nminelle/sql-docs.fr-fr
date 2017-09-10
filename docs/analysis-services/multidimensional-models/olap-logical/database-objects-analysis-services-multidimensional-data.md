---
title: "Objets (Analysis Services - données multidimensionnelles) de base de données | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- objects [Analysis Services], about objects
- SQL Server Analysis Services, objects
- Analysis Services objects, about Analysis Services objects
- SSAS, objects
- Analysis Services objects
- objects [Analysis Services]
ms.assetid: f76d869b-fc1d-4807-9f28-da09c7be382d
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 32024dc0799fcc7324fd30349a65e741773db66b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="database-objects-analysis-services---multidimensional-data"></a>Objets de bases de données (Analysis Services - Données multidimensionnelles)
  A [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance contient des objets de base de données et des assemblys à utiliser pour le traitement analytique en ligne (OLAP) et d’exploration de données.  
  
-   Les bases de données contiennent des objets OLAP et des objets d'exploration de données, tels que des sources de données, des vues de sources de données, des cubes, des mesures, des groupes de mesures, des dimensions, des attributs, des hiérarchies, des structures d'exploration de données, des modèles d'exploration de données et des rôles.  
  
-   Les assemblys contiennent des fonctions définies par l'utilisateur qui étendent les fonctionnalités des fonctions intrinsèques fournies avec les langages MDX (Multidimensional Expressions) et DMX (Data Mining Extensions).  
  
 L'objet <xref:Microsoft.AnalysisServices.Database> est le conteneur pour tous les objets de données exigés pour un projet Business Intelligence (tel que les cubes OLAP, les dimensions et les structures d'exploration de données) et leurs objets de prise en charge (tel que <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Account> et <xref:Microsoft.AnalysisServices.Role>).  
  
 Un objet <xref:Microsoft.AnalysisServices.Database> fournit l'accès aux objets et attributs qui incluent les éléments suivants :  
  
-   Tous les cubes auxquels vous pouvez accéder, comme une collection.  
  
-   Toutes les dimensions auxquelles vous pouvez accéder, comme une collection.  
  
-   Toutes les structures d'exploration de données auxquelles vous pouvez accéder, comme une collection.  
  
-   Toutes les sources de données et vues de source de données, comme deux collections.  
  
-   Tous les rôles et autorisations de base de données, comme deux collections.  
  
-   La valeur de classement par défaut de la base de données.  
  
-   La taille estime de la base de données.  
  
-   La valeur de langage de la base de données.  
  
-   Le paramètre visible pour la base de données.  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes décrivent les objets communs aux fonctionnalités OLAP et aux fonctionnalités d'exploration de données dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Sources de données dans les modèles multidimensionnels](../../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)|Décrit les sources de données dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Vues de sources de données dans les modèles multidimensionnels](../../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)|Décrit un modèle de données logique basé sur une ou plusieurs sources de données dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Cubes dans les modèles multidimensionnels](../../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)|Décrit les cubes et les objets de cube, y compris les mesures, les groupes de mesures, les relations d'utilisation de dimension, les calculs, les indicateurs de performance clés (KPI), les actions, les traductions, les partitions et les perspectives.|  
|[Dimensions &#40; Analysis Services - données multidimensionnelles &#41;](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|Décrit les dimensions et les objets de dimension, y compris les attributs, les relations d'attributs, les hiérarchies, les niveaux et les membres.|  
|[Les Structures d’exploration de données &#40; Analysis Services - Exploration de données &#41;](../../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)|Décrit les structures d'exploration de données et les objets d'exploration de données, y compris les modèles d'exploration de données.|  
|[Rôles de sécurité &#40; Analysis Services - données multidimensionnelles &#41;](../../../analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)|Décrit les rôles, le mécanisme de sécurité utilisé pour contrôler l'accès aux objets dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Gestion des assemblys de modèle multidimensionnel](../../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)|Décrit les assemblys, des collections de fonctions définies par l'utilisateur qui sont utilisées pour étendre les langages MDX et DMX dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données prises en charge &#40; SSAS - multidimensionnel &#41;](../../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)   
 [Solutions de modèles multidimensionnels &#40; SSAS &#41;](../../../analysis-services/multidimensional-models/multidimensional-model-solutions-ssas.md)   
 [Solutions d’exploration de données](../../../analysis-services/data-mining/data-mining-solutions.md)  
  
  