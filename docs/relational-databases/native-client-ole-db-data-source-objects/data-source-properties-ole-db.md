---
title: "Propriétés (OLE DB) la Source de données | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-data-source-objects
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 6e14fefc-4e0b-4847-a833-4cf0abe65d50
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 31983f3c9884f12aa33e6ff8ab7397e8f0c3c5c5
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="data-source-properties-ole-db"></a>Propriétés de la source de données (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur implémente les propriétés de source de données comme suit.  
  
|ID de propriété| Description|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|R/W : lecture/écriture Par défaut : aucune<br /><br /> Description : La valeur de DBPROP_CURRENTCATALOG signale la base de données en cours pour un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session du fournisseur OLE DB Native Client. Définition de la valeur de propriété possède un effet identique que la définition de la base de données actuelle à l’aide de la [!INCLUDE[tsql](../../includes/tsql-md.md)] utilisez *base de données* instruction.<br /><br /> À partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], si vous appelez [sp_defaultdb](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md) et spécifiez le nom de la base de données en minuscules, même si la base de données a été créé avec un nom de casse mixte, DBPROP_CURRENTCATALOG retourne le nom en minuscules. Avec les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], DBPROP_CURRENTCATALOG retourne la casse mixte attendue.|  
|DBPROP_MULTIPLECONNECTIONS|R/W : lecture/écriture Par défaut : VARIANT_FALSE<br /><br /> Description : si la connexion exécute une commande qui ne produit pas un ensemble de lignes ou génère un ensemble de lignes qui n'est pas un curseur côté serveur et que vous exécutez une autre commande, une nouvelle connexion est créée pour exécuter la nouvelle commande si DBPROP_MULTIPLECONNECTIONS a la valeur VARIANT_TRUE.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ne crée pas une autre connexion si DBPROP_MULTIPLECONNECTION a la valeur VARIANT_FALSE ou si une transaction est active sur la connexion. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne DB_E_OBJECTOPEN si DBPROP_MULTIPLECONNECTIONS a la valeur VARIANT_FALSE et retourne E_FAIL s’il existe une transaction active. Les transactions et le verrouillage sont gérés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion par connexion. Si une deuxième connexion est générée, les commandes sur les connexions séparées ne partagent pas les verrous. Pour garantir qu'une commande n'en bloque pas une autre, maintenez les verrous sur les lignes demandées par l'autre commande. Ceci reste vrai en cas de création de plusieurs sessions.<br /><br /> Chaque session possède une connexion distincte.|  
  
 Dans la propriété spécifique au fournisseur de jeu de propriétés DBPROPSET_SQLSERVERDATASOURCE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client définit les propriétés de la source de données supplémentaires.  
  
|ID de propriété| Description|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|R/W : lecture/écriture Par défaut : VARIANT_FALSE<br /><br /> Description : pour permettre la copie en bloc à partir de la mémoire, la propriété SSPROP_ENABLEFASTLOAD doit avoir la valeur VARIANT_TRUE. Avec cette propriété est définie sur la source de données, la session nouvellement créée autorise l’accès du consommateur à le [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) interface.<br /><br /> Si la propriété est définie avec la valeur VARIANT_TRUE, **IRowsetFastLoad** interface est disponible via **IOpenRowset::OpenRowset** en demandant le **IID_IRowsetFastLoad** interface ou en définissant **SSPROP_IRowsetFastLoad** avec la valeur VARIANT_TRUE.|  
|SSPROP_ENABLEBULKCOPY|R/W : lecture/écriture Par défaut : VARIANT_FALSE<br /><br /> Description : pour permettre la copie en bloc à partir de fichiers, la propriété SSPROP_ENABLEBULKCOPY doit avoir la valeur VARIANT_TRUE. Avec cette propriété définie sur la source de données, l'accès du consommateur à l'interface IBCPSession est disponible sous le même niveau que Sessions.<br /><br /> SSPROP_IRowsetFastLoad doit également être défini avec la valeur VARIANT_TRUE.|  
  
## <a name="see-also"></a>Voir aussi  
 [Objets Source de données &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
