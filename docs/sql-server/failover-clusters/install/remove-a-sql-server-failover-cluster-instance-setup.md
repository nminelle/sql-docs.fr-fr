---
title: "Supprimer une instance de cluster de basculement SQL Server (programme d’installation) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: failover-clusters
ms.reviewer: 
ms.suite: sql
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clusters [SQL Server], removing failover clustered instance
- failover clustering [SQL Server], removing failover clustered instance
- uninstalling failover clustered instances
- removing failover clustered instances
ms.assetid: bf63353b-69cf-4c5c-98ea-7b151e36537f
caps.latest.revision: "38"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 75e968279a9ba006d3a40b766beda8eced6695b3
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="remove-a-sql-server-failover-cluster-instance-setup"></a>Supprimer une instance de cluster de basculement SQL Server (programme d'installation)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Suivez cette procédure pour désinstaller une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Pour mettre à jour ou supprimer un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , vous devez être un administrateur local autorisé à se connecter en tant que service sur tous les nœuds du cluster de basculement.  
  
 **Avant de commencer**  
  
 Prenez en compte les points importants suivants avant de désinstaller un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
-   Si [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client est désinstallé par accident, les ressources [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne pourront pas démarrer. Pour réinstaller [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, exécutez le programme d'installation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour installer les éléments requis de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   Si vous avez désinstallé un cluster de basculement comportant plusieurs ressources de cluster IP SQL, vous devez supprimer les ressources IP SQL supplémentaires à l'aide de l'administrateur de clusters.  
  
 Pour plus d’informations sur la syntaxe de l’invite de commandes, consultez [Installer SQL Server 2016 à partir de l’invite de commandes](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
### <a name="to-uninstall-a-includessnoversionincludesssnoversion-mdmd-failover-cluster"></a>Pour désinstaller un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
1.  Pour désinstaller un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], utilisez la fonctionnalité Supprimer un nœud fournie par le programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour supprimer chaque nœud individuellement. Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et lire les fichiers journaux d'installation de SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
