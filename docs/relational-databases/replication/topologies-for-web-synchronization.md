---
title: "Topologies pour la synchronisation web | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web synchronization, topologies
- IIS server configuration [SQL Server replication]
ms.assetid: 59444faf-bcb6-4421-a3df-8715753e453b
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2cabfb9884256a3445af3634676d0a889a6e23a5
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="topologies-for-web-synchronization"></a>Topologies pour la synchronisation web
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Vous pouvez choisir parmi différentes topologies de réplication de synchronisation Web [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les façons courantes de configurer une synchronisation Web sont les suivantes :  
  
-   Serveur unique  
  
-   Deux serveurs  
  
-   Plusieurs systèmes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) et la republication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Pour plus d’informations sur la configuration de la synchronisation web, consultez [Configurer la synchronisation web](../../relational-databases/replication/configure-web-synchronization.md).  
  
## <a name="single-server"></a>Serveur unique  
 Dans la topologie la plus simple, IIS, le serveur de publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le serveur de distribution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] résident tous trois sur le même serveur. Les Abonnés se synchronisent en se connectant à IIS sur le serveur de publication. Le serveur de publication peut être situé derrière un pare-feu.  
  
> [!NOTE]  
>  Cette configuration est recommandée uniquement pour les scénarios intranet. Pour les autres scénarios, il est recommandé que le serveur IIS et les serveurs de publication et de distribution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] soient placés sur des ordinateurs distincts.  
  
 ![Synchronisation web avec un serveur unique](../../relational-databases/replication/media/web-sync02.gif "Synchronisation web avec un serveur unique")  
  
## <a name="two-servers"></a>Deux serveurs  
 Vous pouvez placer IIS sur un serveur et configurer les serveurs de publication et de distribution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un autre serveur. Le serveur exécutant IIS peut être isolé d'Internet par un pare-feu. Les Abonnés se synchronisent en se connectant à IIS.  
  
 ![Synchronisation web avec deux serveurs](../../relational-databases/replication/media/web-sync03.gif "Synchronisation web avec deux serveurs")  
  
## <a name="multiple-iis-systems-and-sql-server-republishing"></a>Plusieurs systèmes IIS et la republication SQL Server  
 Si vous devez prendre en charge un très grand nombre d'Abonnés qui se synchronisent au même moment, vous pouvez partitionner le travail entre plusieurs ordinateurs exécutant IIS.  
  
 ![Synchronisation web avec deux serveurs](../../relational-databases/replication/media/web-sync04.gif "Synchronisation web avec deux serveurs")  
  
 Si un équilibrage de charge est encore nécessaire sur l'ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez créer une hiérarchie de republication sur plusieurs ordinateurs. Le serveur de publication de niveau supérieur publie les données vers les Abonnés, qui à leur tour republient ces données, équilibrant la charge des requêtes en provenance des Abonnés.  
  
> [!NOTE]  
>  Les Abonnés ne peuvent effectuer des synchronisations qu'avec un serveur de publication donné. Par exemple, un Abonné au serveur de republication A ne peut effectuer aucune synchronisation avec le serveur de republication B si le serveur A n'est pas disponible.  
  
 ![Synchronisation web avec republication](../../relational-databases/replication/media/web-sync05.gif "Synchronisation web avec republication")  
  
## <a name="see-also"></a> Voir aussi  
 [Configurer la synchronisation web](../../relational-databases/replication/configure-web-synchronization.md)   
 [Synchronisation web pour la réplication de fusion](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
