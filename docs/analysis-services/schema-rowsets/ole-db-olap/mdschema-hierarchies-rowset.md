---
title: Ensemble de lignes MDSCHEMA_HIERARCHIES | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MDSCHEMA_HIERARCHIES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_HIERARCHIES rowset
ms.assetid: 2e5b2a81-366e-4d5b-af1e-1d372bf596d9
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7ecdc6817c5a2d7e1e88b909080a3156c55f40eb
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemahierarchies-rowset"></a>Ensemble de lignes MDSCHEMA_HIERARCHIES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Décrit chaque hiérarchie dans une dimension particulière.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le **MDSCHEMA_HIERARCHIES** ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Nom du catalogue auquel appartient cette hiérarchie. Valeur**NULL** si le fournisseur ne prend pas en charge les catalogues.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Non pris en charge|  
|**CUBE_NAME**|**DBTYPE_WSTR**|(Obligatoire) Nom du cube auquel appartient cette hiérarchie.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Nom unique de la dimension à laquelle appartient cette hiérarchie. Pour les fournisseurs qui produisent des noms uniques par qualification, chaque composant du nom est délimité.|  
|**HIERARCHY_NAME**|**DBTYPE_WSTR**|Nom de la hiérarchie. Vide si la dimension ne contient qu'une seule hiérarchie. Cela aura toujours une valeur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Nom unique de la hiérarchie.|  
|**HIERARCHY_GUID**|**DBTYPE_GUID**|Non pris en charge|  
|**HIERARCHY_CAPTION**|**DBTYPE_WSTR**|Une étiquette ou légende associée à la hiérarchie. Principalement utilisée à des fins d'affichage. Si une légende n’existe pas, **HIERARCHY_NAME** est retourné. Si la dimension ne contient pas de hiérarchie ou n'en possède qu'une seule, cette colonne contient le nom de la dimension.|  
|**DIMENSION_TYPE**|**DBTYPE_I2**|Type de la dimension. Les valeurs valides sont les suivantes :<br /><br /> **MD_DIMTYPE_UNKNOWN** (**0**)<br /><br /> **MD_DIMTYPE_TIME** (**1**)<br /><br /> **MD_DIMTYPE_MEASURE** (**2**)<br /><br /> **MD_DIMTYPE_OTHER** (**3**)<br /><br /> **MD_DIMTYPE_QUANTITATIVE** (**5**)<br /><br /> **MD_DIMTYPE_ACCOUNTS** (**6**)<br /><br /> **MD_DIMTYPE_CUSTOMERS** (**7**)<br /><br /> **MD_DIMTYPE_PRODUCTS** (**8**)<br /><br /> **MD_DIMTYPE_SCENARIO** (**9**)<br /><br /> **MD_DIMTYPE_UTILIY** (**10**)<br /><br /> **MD_DIMTYPE_CURRENCY** (**11**)<br /><br /> **MD_DIMTYPE_RATES** (**12**)<br /><br /> **MD_DIMTYPE_CHANNEL** (**13**)<br /><br /> **MD_DIMTYPE_PROMOTION** (**14**)<br /><br /> **MD_DIMTYPE_ORGANIZATION** (**15**)<br /><br /> **MD_DIMTYPE_BILL_OF_MATERIALS** (**16**)<br /><br /> **MD_DIMTYPE_GEOGRAPHY** (**17**)|  
|**HIERARCHY_CARDINALITY**|**DBTYPE_UI4**|Nombre de membres de la hiérarchie.|  
|**DEFAULT_MEMBER**|**DBTYPE_WSTR**|Membre par défaut de cette hiérarchie. Il s'agit d'un nom unique. Chaque hiérarchie doit avoir un membre par défaut.|  
|**ALL_MEMBER**|**DBTYPE_WSTR**|Membre au niveau le plus élevé du cumul.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Description explicite de la hiérarchie. **NULL** si aucune description n’existe.|  
|**STRUCTURE**|**DBTYPE_I2**|Structure de la hiérarchie. Les valeurs valides sont les suivantes :<br /><br /> **MD_STRUCTURE_FULLYBALANCED** (**0**)<br /><br /> **MD_STRUCTURE_RAGGEDBALANCED** (**1**)<br /><br /> **MD_STRUCTURE_UNBALANCED** (**2**)<br /><br /> **MD_STRUCTURE_NETWORK** (**3**)|  
|**IS_VIRTUAL**|**DBTYPE_BOOL**|Retourne toujours **False**.|  
|**IS_READWRITE**|**DBTYPE_BOOL**|Valeur booléenne indiquant si la colonne d'écriture différée dans la dimension est activée.<br /><br /> Retourne **TRUE** si le **d’écriture différée de dimension** colonne qui représente cette hiérarchie est activée.|  
|**DIMENSION_UNIQUE_SETTINGS**|**DBTYPE_I4**|Retourne toujours **MDDIMENSIONS_MEMBER_KEY_UNIQUE** (**1**).|  
|**DIMENSION_MASTER_UNIQUE_NAME**|**DBTYPE_WSTR**|Retourne toujours **NULL**.|  
|**DIMENSION_IS_VISIBLE**|**DBTYPE_BOOL**|Retourne toujours **true**. Si la dimension n'est pas visible, elle n'apparaît pas dans l'ensemble de lignes du schéma.|  
|**HIERARCHY_ORDINAL**|**DBTYPE_UI4**|Nombre ordinal de la hiérarchie, parmi toutes les hiérarchies du cube.|  
|**DIMENSION_IS_SHARED**|**DBTYPE_BOOL**|Retourne toujours **TRUE**.|  
|**HIERARCHY_IS_VISIBLE**|**DBTYPE_BOOL**|Valeur booléenne qui indique si la hiérarchie est visible.<br /><br /> Retourne **TRUE** si la hiérarchie est visible ; sinon, **FALSE**.|  
|**HIERARCHY_ORIGIN**|**DBTYPE_UI2**|Masque de bits qui détermine la source de la hiérarchie :<br /><br /> **MD_USER_DEFINED** identifie les hiérarchies définies par l’utilisateur, et a la valeur **0 x 0000001**.<br /><br /> **MD_SYSTEM_ENABLED** identifie les hiérarchies d’attributs, et a la valeur **0x0000002**.<br /><br /> **MD_SYSTEM_INTERNAL** identifie des attributs sans hiérarchies d’attribut et a la valeur **0 x 0000004**.<br /><br /> <br /><br /> Notez qu’une hiérarchie d’attribut parent/enfant est à la fois **MD_USER_DEFINED** et **MD_SYSTEM_ENABLED**.|  
|**HIERARCHY_DISPLAY_FOLDER**|**DBTYPE_WSTR**|Chemin d'accès à utiliser pour l'affichage de la hiérarchie dans l'interface utilisateur. Les noms de dossiers doivent être séparés par un point-virgule (;). Les dossiers imbriqués sont indiqués par une barre oblique inverse (\\).|  
|**INSTANCE_SELECTION**|**DBTYPE_UI2**|Indicateur fourni à l'application cliente sur la manière d'afficher la hiérarchie. Les valeurs valides sont les suivantes :<br /><br /> **MD_INSTANCE_SELECTION_NONE**<br /><br /> **MD_INSTANCE_SELECTION_DROPDOWN**<br /><br /> **MD_INSTANCE_SELECTION_LIST**<br /><br /> **MD_INSTANCE_SELECTION_FILTEREDLIST**<br /><br /> **MD_INSTANCE_SELECTION_MANDATORYFILTER**|  
|**GROUPING_BEHAVIOR**|**DBTYPE_I2**|Énumération qui spécifie le comportement de regroupement attendu des clients pour cette hiérarchie. Les valeurs possibles sont les suivantes :<br /><br /> **EncourageGrouping** (1)<br /><br /> **DiscourageGrouping** (2)|  
|**STRUCTURE_TYPE**|**DBTYPE_WSTR**|Indique le type de hiérarchie. Les valeurs valides sont les suivantes :<br /><br /> **Naturelle**<br /><br /> **Non naturelles**<br /><br /> **Unknown**|  
  
 L’ensemble de lignes est trié sur **CATALOG_NAME**, **nom_schéma**, **CUBE_NAME**, **DIMENSION_UNIQUE_NAME**, **HIERARCHY_NAME**.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le **MDSCHEMA_HIERARCHIES** ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facultatif.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facultatif.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facultatif.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Facultatif.|  
|**HIERARCHY_NAME**|**DBTYPE_WSTR**|Facultatif.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Facultatif.|  
|**HIERARCHY_ORIGIN**|**DBTYPE_UI2**|(Facultatif) Une restriction par défaut est appliquée sur MD_USER_DEFINED et MD_SYSTEM_ENABLED.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Facultatif) Restriction par défaut est une valeur de 1. Une image bitmap avec l’une des valeurs valides suivantes :<br /><br /> 1 CUBE<br /><br /> 2 DIMENSION|  
|**HIERARCHY_VISIBILITY**|**DBTYPE_UI2**|(Facultatif) Restriction par défaut est une valeur de 1. Une image bitmap avec l’une des valeurs valides suivantes :<br /><br /> 1 Visible<br /><br /> 2 non visible|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
