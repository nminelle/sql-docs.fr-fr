---
title: MSSQLSERVER_10060 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- "10060"
helpviewer_keywords:
- 10060 (Database Engine error)
ms.assetid: 28c21277-cad8-406c-a955-07933a56982a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8804ad6e01204446f1e5b3c2cab3b1e2bd85367f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver10060"></a>MSSQLSERVER_10060
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10060|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique||  
|Texte du message|Une erreur s'est produite lors de l'établissement d'une connexion au serveur.  Lors de la connexion à SQL Server, cet échec peut être dû au fait que les paramètres par défaut de SQL Server n'autorisent pas les connexions à distance. (fournisseur : Fournisseur TCP, erreur : 0 - Une tentative de connexion a échoué car le participant connecté n’a pas répondu convenablement au-delà d’une certaine durée, ou une connexion établie a échoué car l’hôte de connexion n’a pas répondu.) (Microsoft SQL Server, Erreur : 10060)|  
  
## <a name="explanation"></a>Explication  
Le client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas se connecter au serveur. Cette erreur s'est peut-être produite parce que le pare-feu sur le serveur a refusé la connexion ou le serveur n'est pas configuré pour accepter des connexions distantes.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour résoudre cette erreur, essayez d'effectuer l'une des opérations suivantes :  
  
-   Assurez-vous d'avoir configuré le pare-feu sur l'ordinateur afin de permettre à cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'accepter les connexions.  
  
-   Utilisez l'outil Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour permettre à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'accepter des connexions distantes.  
  
## <a name="see-also"></a>Voir aussi  
[Configurer un pare-feu Windows pour accéder au moteur de base de données](~/database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
[Configurer des protocoles clients](~/database-engine/configure-windows/configure-client-protocols.md)  
[Protocoles réseau et bibliothèques réseau](~/sql-server/install/network-protocols-and-network-libraries.md)  
[Configuration du réseau client](~/database-engine/configure-windows/client-network-configuration.md)  
[Configurer des protocoles clients](~/database-engine/configure-windows/configure-client-protocols.md)  
[Activer ou désactiver un protocole réseau de serveur](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
