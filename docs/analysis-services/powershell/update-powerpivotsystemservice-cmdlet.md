---
title: Applet de commande Update-PowerPivotSystemService | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a90f1158-68d3-4330-98c1-fb0f81e13328
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 045979085e6d8e1622fef2a961f6c9fdb21d772a
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="update-powerpivotsystemservice-cmdlet"></a>Applet de commande Update-PowerPivotSystemService
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Met à niveau l’objet parent du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans la batterie.  

>[!NOTE] 
>Cet article peut contenir des exemples et des informations obsolètes. Utilisez l’applet de commande Get-Help pour la dernière version.
  
 **S'applique à :** SharePoint 2010 et SharePoint 2013.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Update-PowerPivotSystemService [-Confirm <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a> Description  
 L’applet de commande **Update-PowerPivotSystemService** exécute une série d’actions de mise à niveau sur l’objet parent du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , les instances et les applications de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans la batterie. Tous les services et applications de niveau intermédiaire d’un déploiement [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint doivent s’exécuter au même niveau fonctionnel. Cette applet de commande effectue les actions de mise à niveau sur tous ces objets.  
  
 Exécutez cette applet de commande après avoir exécuté le programme d’installation de SQL Server pour installer une version plus récente de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint ou si vous avez appliqué une mise à jour cumulative sur le serveur. Pour vérifier si une mise à niveau est requise, exécutez `Get-PowerPivotSystemService` pour examiner la propriété **NeedsUpgrade** . Si la propriété **NeedsUpgrade** a la valeur true, vous devez exécuter l’applet de commande pour mettre à niveau les objets [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de niveau intermédiaire dans la batterie.  
  
 Étant donné qu’un déploiement [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint inclut des services de données de niveaux intermédiaires et principaux, vous devez exécuter **Update-PowerPivotEngineService** chaque fois que vous exécutez **Update-PowerPivotSystemService** pour garantir que les deux niveaux utilisent la même version dans toute la batterie.  
  
 La mise à niveau ne peut pas être restaurée à la version précédente. Si vous devez rétablir une version antérieure, supprimez [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de votre batterie SharePoint et réinstallez le logiciel. Pour vous assurer de la réussite de l'opération de mise à niveau, exécutez `Get-PowerPivotSystemService` pour passer en revue les informations de version dans les propriétés globales et pour vérifier que **NeedsUpgrade** n'a plus la valeur true.  
  
## <a name="parameters"></a>Paramètres  
  
### <a name="-confirm-switch"></a>-Confirmer \<commutateur >  
 Demande une confirmation avant d'exécuter la commande. Cette valeur est activée par défaut. Pour contourner la réponse de confirmation dans une commande, spécifiez Confirm:$false sur la commande.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="commonparameters"></a>\<CommonParameters>  
 Cette applet de commande prend en charge les paramètres suivants :  
  
-   Commentaires  
  
-   Débogage  
  
-   ErrorAction  
  
-   ErrorVariable  
  
-   WarningAction  
  
-   WarningVariable  
  
-   OutBuffer  
  
-   OutVariable  
  
 Pour plus d’informations, consultez [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun.|  
|Sorties|Aucun.|  
  
  
