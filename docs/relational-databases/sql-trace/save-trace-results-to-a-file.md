---
title: "Enregistrer les résultats de trace dans un fichier | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-trace
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74f80667-62f3-4e14-bb1a-f0c2b6ef3402
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6555bf45840676342a9df3b37fee8830bfed246f
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="save-trace-results-to-a-file"></a>Enregistrer les résultats de trace dans un fichier
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Vous pouvez enregistrer les résultats d'une trace dans un fichier. Un fichier de trace est un fichier dans lequel sont écrits les résultats d'une trace. Un fichier de trace peut se situer dans un répertoire local (tel que C:\\*nom_dossier*\\*nom_fichier.trc*) ou un répertoire réseau (tel que \\\nom_ordinateur\nom_partage\nom_fichier.trc).  
  
 Vous pouvez utiliser les fichiers de trace pour effectuer les opérations suivantes :  
  
-   Relire des traces  
  
-   Auditer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Mener des analyses des performances  
  
-   Corréler des événements de trace et des compteurs de performances pour améliorer la détection des problèmes  
  
-   Effectuer une analyse de l'Assistant Paramétrage du moteur de base de données  
  
-   Exécuter une optimisation de requête  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enregistre les résultats de trace dans un fichier quand un chemin et un nom de fichier sont spécifiés pour l’argument **@tracefile** de la procédure stockée **sp_trace_create**.  
  
> [!NOTE]  
>  Si un chemin est spécifié pour la procédure stockée **sp_trace_create** pour l’enregistrement du fichier de trace, le répertoire doit être accessible au serveur. Sachez également que si un répertoire local est spécifié pour **sp_trace_create**, il s’agit d’un répertoire local sur le serveur.  
  
 Si le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] est utilisé, il vous permet d'enregistrer les résultats de trace dans un fichier ou dans une table. L'enregistrement des résultats de trace dans une table donne le même accès que l'enregistrement de la trace dans un fichier, et vous pouvez en plus rechercher des événements spécifiques dans la table.  
  
 Pour plus d’informations sur l’enregistrement des résultats de trace, consultez [Enregistrer des résultats d’une trace dans une table &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) et [Enregistrer des résultats d’une trace dans un fichier &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md).  
  
## <a name="see-also"></a> Voir aussi  
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [Créer une trace &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [Créer une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
