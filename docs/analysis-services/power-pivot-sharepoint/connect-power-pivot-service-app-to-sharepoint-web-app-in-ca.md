---
title: "Connecter l’application de Service Power Pivot à une application Web SharePoint dans l’autorité de certification | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5da8e29-7ffd-44e7-bf61-344fa5bea8ce
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 888a9c7c06a43f1fcee9306a7edeaed4b484e24b
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="connect-power-pivot-service-app-to-sharepoint-web-app-in-ca"></a>Connecter l’application de Service Power Pivot à une application Web SharePoint dans l’autorité de certification
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Une application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] peut être utilisée par un nombre illimité d’applications web SharePoint de la batterie de serveurs. Pour définir une application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] comme disponible, vous devez l’ajouter à une liste d’association de services.  
  
> [!IMPORTANT]  
>  Vous devez disposer d’une seule application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans le groupe par défaut pour garantir le bon fonctionnement du tableau de bord de gestion [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . N’ajoutez pas plusieurs applications de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] au groupe par défaut. L'ajout de plusieurs entrées du même type d'application de service n'est pas une configuration prise en charge et risque de provoquer des erreurs. Si vous créez des applications de service supplémentaires, ajoutez-les aux listes personnalisées.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Ajouter une application de services Power Pivot au groupe par défaut](#default)  
  
 [Ajouter une application de services Power Pivot à une liste d’association de services personnalisée](#custom)  
  
##  <a name="default"></a> Ajouter une application de services au groupe par défaut  
 Une liste d'association de services est une liste de services partagés qui fournissent des ressources à d'autres applications Web SharePoint de la batterie de serveurs. Il existe un groupe par défaut d'association de services pour la batterie de serveurs.  
  
 Pour faire figurer une application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans la liste, vous pouvez l’ajouter, soit lorsque vous créez l’application, soit ultérieurement en procédant comme suit.  
  
1.  Dans Administration centrale, dans **Gestion des applications**, cliquez sur **Configurer les paramètres d'application de service**.  
  
2.  Dans Groupe de proxy d'application, cliquez sur **valeur par défaut**.  
  
3.  Cochez la case en regard de l’application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] (signalée par la valeur **Proxy de l’application du service PowerPivot**pour le nom de type). Si vous disposez de plusieurs applications de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , n’en choisissez qu’une seule.  
  
4.  Cliquez sur **OK**.  
  
##  <a name="custom"></a> Ajouter une application de services [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] à une liste d’association de services personnalisée  
 Le groupe par défaut peut être remplacé par une liste personnalisée. Une liste personnalisée est créée spécifiquement pour une application Web SharePoint précise. Elle remplace le groupe par défaut par les associations de services spécifiées par un administrateur de batterie de serveurs ou de service. Si vous avez créé plusieurs applications de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , vous devez utiliser une liste personnalisée pour spécifier l’application à utiliser. Une liste personnalisée ne peut pas être réutilisée par d'autres applications Web. Elle s'applique uniquement à l'application Web pour laquelle elle a été créée.  
  
1.  Dans Administration Centrale, sous **Gestion des applications**, cliquez sur **Gérer les applications Web**.  
  
2.  Sélectionnez l'application (par exemple, SharePoint -80).  
  
3.  Dans Applications Web, dans Gérer, cliquez sur **Connexions aux services**.  
  
4.  Dans **Modifier le groupe suivant de connexions**, sélectionnez **[personnalisé]**.  
  
5.  Activez la case à cocher en regard de chaque connexion d'application de service que vous souhaitez utiliser. Si vous disposez de plusieurs applications de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] (signalées par la valeur **Proxy de l’application du service PowerPivot**pour Type), veillez à n’en choisir qu’une seule.  
  
6.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration d’une application de service Power Pivot dans l'Administration centrale](../../analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)   
 [Configuration initiale (PowerPivot pour SharePoint)](http://msdn.microsoft.com/en-us/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)  
  
  
