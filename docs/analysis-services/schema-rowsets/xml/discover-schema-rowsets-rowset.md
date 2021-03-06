---
title: Ensemble de lignes DISCOVER_SCHEMA_ROWSETS | Documents Microsoft
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
apiname: DISCOVER_SCHEMA_ROWSETS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_SCHEMA_ROWSETS rowset
ms.assetid: e5012aa0-6ef8-497f-96c1-2772e2394f62
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 73fe1580fb43a090a7df04a43432e5b213e86369
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="discoverschemarowsets-rowset"></a>Ensemble de lignes DISCOVER_SCHEMA_ROWSETS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Retourne les noms, restrictions, description et autres informations pour toutes les valeurs d’énumération et toutes les valeurs d’énumération spécifique au fournisseur supplémentaires pris en charge par le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML pour le fournisseur Analysis (XMLA).  
  
 Si vous appelez le [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) méthode avec la **DISCOVER_SCHEMA_ROWSETS** valeur d’énumération dans le [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) élément, le **Discover** méthode retourne la **DISCOVER_SCHEMA_ROWSETS** ensemble de lignes.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes DISCOVER_SCHEMA_ROWSETS contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|**SchemaName**|**DBTYPE_WSTR**||Nom du schéma ou de la requête. Cette requête retourne les valeurs de l'énumération *RequestTypes* .|  
|**SchemaGuid**|**DBTYPE_GUID**||GUID du schéma.|  
|**Restrictions**|**DBTYPE_HCHAPTER**||Tableau des restrictions prises en charge par le fournisseur.|  
|**Description**|**DBTYPE_WSTR**||Description localisable du schéma.|  
|**RestrictionsMask**|**DBTYPE_UI8**|||  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
 Pour un fournisseur qui prend en charge trois restrictions pour l'ensemble de lignes de schéma DBSCHEMA_MEMBERS, le tableau **Restrictions** peut retourner le résultat suivant. Les éléments du résultat font référence aux noms de colonne dans le schéma.  
  
```  
<Restrictions>  
      <CATALOG_NAME type="string" />   
      <SCHEMA_NAME type="string" />   
      <CUBE_NAME type="string" />   
</Restrictions>  
```  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DISCOVER_SCHEMA_ROWSETS** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**SchemaName**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
