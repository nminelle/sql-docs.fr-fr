---
title: "Append (méthode) (Index ADOX) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Indexes::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6695769f-275b-4b70-81bd-1a5f7d74926c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 00c0f00c1c5de2e049742603c08d323e2978d3fd
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="append-method-adox-indexes"></a>Append (méthode) (Index ADOX)
Ajoute un nouveau [Index](../../../ado/reference/adox-api/index-object-adox.md) de l’objet à la [index](../../../ado/reference/adox-api/indexes-collection-adox.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Index*  
 Le **Index** objet à ajouter ou le nom de l’index à créer et à ajouter.  
  
 *Columns*  
 Ce paramètre est facultatif. A **Variant** valeur qui spécifie l’ou les noms des colonnes à indexer. Le *colonnes* paramètre correspond à l’ou les valeurs de la [nom](../../../ado/reference/adox-api/name-property-adox.md) propriété d’un [colonne](../../../ado/reference/adox-api/column-object-adox.md) ou les objets.  
  
## <a name="remarks"></a>Notes  
 Le *colonnes* paramètre peut prendre le nom d’une colonne ou un tableau de noms de colonnes.  
  
 Une erreur se produit si le fournisseur ne prend pas en charge la création d’index.  
  
## <a name="applies-to"></a>S'applique à  
 [Indexes, collection (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Indexes Append, méthode-exemple (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Append (méthode) (colonnes ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (méthode) (groupes ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (méthode) (clés ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (méthode) (procédures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append (méthode) (Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (méthode) (utilisateurs ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append, méthode (vues ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
