---
title: Applet de commande Remove-PowerPivotSystemServiceInstance | Documents Microsoft
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
ms.assetid: bc46094a-5584-47ba-8883-77dc79373a5d
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bc93af457830a9efe0c57707a37ec946597887fe
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="remove-powerpivotsystemserviceinstance-cmdlet"></a>Applet de commande Remove-PowerPivotSystemServiceInstance
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Supprime une instance du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de la batterie de serveurs.  

>[!NOTE] 
>Cet article peut contenir des exemples et des informations obsolètes. Utilisez l’applet de commande Get-Help pour la dernière version.
  
 **S'applique à :** SharePoint 2010 et SharePoint 2013.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Remove-PowerPivotSystemServiceInstance [-Confirm <switch>] [-DeleteLocal <switch>] [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a> Description  
 L’applet de commande Remove-PowerPivotSystemServiceInstance supprime les informations d’instance relatives au service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de la batterie de serveurs. Elle ne supprime pas les fichiers programme. Pour supprimer définitivement les fichiers programme, vous devez les désinstaller.  
  
 Si vous supprimez le service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , veillez à exécuter également Remove-PowerPivotEngineServiceInstance pour supprimer l’instance Analysis Services associée, puis Remove-PowerPivotServiceApplication pour supprimer toutes les applications de service PowerPivot. Les applications de service ne s'exécuteront plus une fois les services supprimés.  
  
 Pour annuler cette modification, vous pouvez exécuter New-PowerPivotSystemServiceInstance pour réactiver les informations d'instance.  
  
## <a name="parameters"></a>Paramètres  
  
### <a name="-identity-powerpivotmidtierserviceinstancepipebind"></a>-Identity \<PowerPivotMidTierServiceInstancePipeBind>  
 Spécifie le GUID de l’instance du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que vous souhaitez supprimer. Il existe une instance de service sur chaque serveur d’applications comportant une installation de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-deletelocal-switch"></a>-DeleteLocal \<commutateur >  
 Supprime l’instance du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] installée sur l’ordinateur local, ce qui vous permet de supprimer l’instance sans avoir à spécifier d’identité d’objet.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
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
 Cette applet de commande prend en charge les paramètres communs : Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer et OutVariable. Pour plus d’informations, consultez [About_Commonparameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun.|  
|Sorties|Aucun.|  
  
## <a name="example-1"></a>Exemple 1  
  
```  
C:\PS>Remove-PowerPivotSystemServiceInstance -deletelocal  
```  
  
 Cet exemple indique comment supprimer l’instance du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] qui s’exécute sur le serveur d’applications local.  
  
## <a name="example-2"></a>Exemple 2  
  
```  
C:\PS>Remove-PowerPivotSystemServiceInstance -identity 1234567-890a-bcde-fghijklmn  
```  
  
 Cet exemple indique comment supprimer un service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] spécifique en fonction de son identité.  
  
  
