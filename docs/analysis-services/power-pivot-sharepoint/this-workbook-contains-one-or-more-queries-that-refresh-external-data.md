---
title: "Ce classeur contient une ou plusieurs requêtes qui actualisent les données externes | Documents Microsoft"
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
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 354c8c0baca1372c0bc6cb17e2acbfc74c45b9b4
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a>Ce classeur contient une ou plusieurs requêtes qui actualisent les données externes
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Pour les classeurs Excel qui contiennent des données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , Excel Services affiche cet avertissement lorsqu’il détecte des informations de connexion et vous demande d’activer ou de désactiver des requêtes pour ce classeur.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11_md](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14_md](../../includes/sssql14-md.md)]|  
|Cause|Excel Services est configuré pour avertir lors de l'actualisation des données.|  
|Texte du message|Ce classeur contient une ou plusieurs requêtes qui actualisent les données externes. Un utilisateur malveillant peut concevoir une requête pour accéder aux informations confidentielles et les distribuer à d'autres utilisateurs ou effectuer d'autres actions malfaisantes.<br /><br /> Si vous approuvez la source de ce classeur, cliquez sur Oui pour activer les requêtes à des données externes dans ce classeur. Si vous avez des doutes, cliquez sur Non afin que les modifications ne soient pas appliquées à votre classeur.<br /><br /> Souhaitez-vous activer des requêtes à des données externes dans ce classeur ?|  
  
## <a name="explanation"></a>Explication  
 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] contiennent des chaînes de connexion de données incorporées, utilisées par Excel pour communiquer avec un serveur [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] externe qui charge et calcule les données. Lorsque l'option Avertir lors de l'actualisation des données est activée, Excel Services détecte cette chaîne de connexion et avertit l'utilisateur en conséquence.  
  
 Pour que les données [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] puissent être coupées et filtrées dans le classeur, les requêtes doivent être activées. Assurez-vous que vous activez des requêtes uniquement pour les classeurs [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] que vous approuvez.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Cliquez sur **Oui** pour activer les requêtes.  
  
 Vous pouvez également modifier les paramètres de configuration de façon à ne plus avertir lors de l'actualisation des données :  
  
1.  Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur **Application Excel Services**.  
  
3.  Cliquez sur **Emplacement de fichier approuvé**.  
  
4.  Cliquez sur **http://** ou sur l’emplacement que vous voulez configurer.  
  
5.  Dans Données externes, désactivez la case à cocher **Avertir lors de l'actualisation**.  
  
6.  Cliquez sur **OK**.  
  
 Vous pouvez également créer un emplacement approuvé pour les sites qui contiennent des classeurs [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] , puis modifier les paramètres de configuration uniquement pour ce site. Pour plus d’informations, voir [Créer un emplacement approuvé pour les sites Power Pivot dans l’Administration centrale](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
