---
title: "DateCreated, propriété (ADOX) | Documents Microsoft"
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
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c7f405958cdd28e6dd4ae285c29ce806c2a61074
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="datecreated-property-adox"></a>DateCreated, propriété (ADOX)
Indique la date de que création de l’objet.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **Variant** valeur qui spécifie la date de création. La valeur est null si **DateCreated** n’est pas pris en charge par le fournisseur.  
  
## <a name="remarks"></a>Notes  
 Le **DateCreated** propriété est null pour les objets récemment ajoutés. Après avoir ajouté un nouvel [vue](../../../ado/reference/adox-api/view-object-adox.md) ou [procédure](../../../ado/reference/adox-api/procedure-object-adox.md), vous devez appeler la [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) méthode de la [vues](../../../ado/reference/adox-api/views-collection-adox.md) ou [procédures](../../../ado/reference/adox-api/procedures-collection-adox.md) collection pour obtenir les valeurs de la **DateCreated** propriété.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Procedure, objet (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Table, objet (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[View, objet (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [DateCreated et DateModified, propriétés-exemple (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateModified, propriété (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)
