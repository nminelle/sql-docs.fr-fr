---
title: "Supprimer un modèle (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting models [Master Data Services]
- models [Master Data Services], deleting models
ms.assetid: f0ad3cc4-aed7-47c8-94bc-2971fe9fe871
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a15f86baf249faca4a50cc5d2107c2e74832bf37
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2018
---
# <a name="delete-a-model-master-data-services"></a>Supprimer un modèle (Master Data Services)
  Supprimez un modèle afin de supprimer le modèle et toutes ses données de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
> [!NOTE]  
>  Lorsque vous effectuez cette procédure, tous les objets et toutes les données de toutes les versions du modèle sont supprimés définitivement.  
  
## <a name="prerequisites"></a>Prerequisites  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-a-model"></a>Pour supprimer un modèle  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Modèles**.  
  
3.  Dans la grille de la page **Gérer les modèles** , sélectionnez la ligne du modèle à supprimer.  
  
4.  Cliquez sur **Supprimer**.  
  
5.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
6.  Dans la boîte de dialogue de confirmation supplémentaire, cliquez sur **OK**.  
  
 La colonne **État** de la grille affiche l’état de l’opération sur le modèle. Quand vous cliquez sur le bouton **Enregistrer le modèle**, l’image ![Mise à jour](../master-data-services/media/mds-model-status-updating.png "Mise à jour") s’affiche, ce qui signifie que le modèle est en cours de mise à jour. En cas d’erreur pendant la création ou la modification d’un modèle, l’image ![Erreur](../master-data-services/media/mds-model-status-error.png "Erreur") apparaît. Dans le cas contraire, le statut est OK et l’image ![OK](../master-data-services/media/mds-model-status-ok.png "OK") apparaît.  
  
## <a name="see-also"></a> Voir aussi  
 [Modèles &#40;Master Data Services&#41;](../master-data-services/models-master-data-services.md)   
 [Créer un modèle &#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md)  
  
  
