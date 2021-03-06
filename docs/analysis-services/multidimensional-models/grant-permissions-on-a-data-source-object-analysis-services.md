---
title: "Accorder des autorisations sur un objet de source de données (Analysis Services) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.asvs.roledesignerdialog.datasources.f1
helpviewer_keywords:
- read/write permissions
- user access rights [Analysis Services], data sources
- security [Analysis Services], data sources
- connection strings [Analysis Services]
- data sources [Analysis Services], security
ms.assetid: b4e302d3-c93b-4383-aa4a-37d15c129830
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f7cd02446a61b7ff1c8d9fdaa2803c30ee81a6e0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="grant-permissions-on-a-data-source-object-analysis-services"></a>Octroyer des autorisations sur un objet de source de données (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]En règle générale, la plupart des utilisateurs de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne nécessitent pas d’accès aux sources de données qui sous-tendent une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet. D'ordinaire, les utilisateurs interrogent simplement les données d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Toutefois, dans le contexte de l'exploration de données, lors de l'exécution de prévisions en fonction d'un modèle d'exploration, par exemple, l'utilisateur doit joindre les données connues d'un modèle d'exploration de données avec les données fournies par l'utilisateur. Pour se connecter à la source de données qui contient les données fournies par l’utilisateur, celui-ci doit utiliser une requête DMX (Data Mining Extensions) qui contient la clause [OPENQUERY &#40;DMX&#41;](../../dmx/source-data-query-openquery.md) ou la clause [OPENROWSET &#40;DMX&#41;](../../dmx/source-data-query-openrowset.md).  
  
 Pour exécuter une requête DMX qui se connecte à une source de données, l’utilisateur doit avoir accès à l’objet de source de données dans la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Par défaut, seuls les administrateurs du serveur et les administrateurs de base de données ont accès aux objets source de données. Cela signifie qu'un utilisateur ne peut pas accéder à un objet source de données à moins que l'administrateur ne lui en accorde l'autorisation.  
  
> [!IMPORTANT]  
>  Pour des raisons de sécurité, la soumission de requêtes DMX à l’aide d’une chaîne de connexion ouverte dans la clause OPENROWSET est désactivée.  
  
## <a name="set-read-permissions-to-a-data-source"></a>Définir des autorisations de lecture sur une source de données  
 Un rôle de base de données peut ne pas être autorisé à accéder à un objet source de données ou peut bénéficier d'autorisations de lecture.  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], développez **Rôles** pour la base de données appropriée dans l’Explorateur d’objets, puis cliquez sur un rôle de base de données existant (ou créez-en un).  
  
2.  Dans le volet **Accès à la source de données** , recherchez l’objet source de données dans la liste **Source de données** , puis sélectionnez **Lecture** dans la liste **Accès** de la source de données. Si cette option n’est pas disponible, consultez le volet **Général** pour savoir si Contrôle total est sélectionné. Contrôle total fournit déjà cette autorisation ; vous ne pouvez pas remplacer les autorisations sur la source de données.  
  
## <a name="working-with-the-connection-string-used-by-a-data-source-object"></a>Utilisation de la chaîne de connexion utilisée par un objet de source de données  
 L'objet de source de données contient la chaîne de connexion utilisée pour se connecter à la source de données sous-jacente. Cette chaîne de connexion peut spécifier l'un des éléments suivants :  
  
-   **Un nom d'utilisateur et un mot de passe**  
  
     Si la chaîne de connexion qu'utilise un objet de source de données définit un nom d'utilisateur et un mot de passe, vous pouvez créer plusieurs objets de source de données ayant chacun un compte d'utilisateur différent. La création de plusieurs objets de source de données permet aux utilisateurs d'accéder à certains objets de source de données et d'empêcher ces utilisateurs d'accéder à d'autres objets de source de données. Ces derniers peuvent être utilisés par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour traiter des objets, tels que des cubes et des modèles d’exploration.  
  
-   **L'authentification Windows**  
  
     Si la chaîne de connexion qu'utilise un objet source de données spécifie l'authentification Windows, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] doit pouvoir emprunter l'identité du client. Si la source de données se trouve sur un ordinateur distant, les deux ordinateurs doivent être approuvés pour l'emprunt d'identité en utilisant l'authentification Kerberos, sinon la requête échoue. Pour plus d’informations, consultez [Configurer Analysis Services pour la délégation contrainte Kerberos](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md) .  
  
     Si le client n’autorise pas l’emprunt d’identité (via la propriété Impersonation Level dans OLE DB et d’autres composants du client), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente de se connecter de manière anonyme à la source de données sous-jacente. Les connexions anonymes aux sources de données distantes réussissent rarement, car la plupart des sources de données n'acceptent pas les connexions anonymes.  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données dans des modèles multidimensionnels](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Propriétés de chaîne de connexion &#40; Analysis Services &#41;](../../analysis-services/instances/connection-string-properties-analysis-services.md)   
 [Méthodologies d'authentification prises en charge par Analysis Services](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md)   
 [Octroyer un accès personnalisé à la dimension de données &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)   
 [Octroyer des autorisations de cube ou de modèle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)   
 [Octroyer un accès personnalisé à des données de cellule &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)  
  
  
