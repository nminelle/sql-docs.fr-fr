---
title: "Conteneur d’hôte de tâche | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2c1f9de6131f52454b991165b228c7e78958a5c8
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="task-host-container"></a>conteneur d'hôte de tâche
  Le conteneur d'hôte de tâche encapsule une seule tâche. Dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , l'hôte de tâche n'est pas configuré séparément ; il est configuré lorsque vous définissez les propriétés de la tâche qu'il encapsule. Pour plus d'informations sur les tâches encapsulées par les conteneurs d’hôte de tâche, consultez [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md).  
  
 Ce conteneur étend l'utilisation des variables et des gestionnaires d'événements au niveau de la tâche. Pour plus d’informations, consultez [Gestionnaires d’événements Integration Services &#40;SSIS&#41; ](../../integration-services/integration-services-ssis-event-handlers.md) et [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md).  
  
## <a name="configuration-of-the-task-host"></a>Configuration de l'hôte de tâche  
 Vous pouvez définir les propriétés dans la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou par programmation.  
  
 Pour plus d’informations sur la définition de ces propriétés dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], consultez [Définir les propriétés d’une tâche ou d’un conteneur](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b).  
  
 Pour plus d’informations sur la définition par programmation de ces propriétés, consultez <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="see-also"></a> Voir aussi  
 [Conteneurs Integration Services](../../integration-services/control-flow/integration-services-containers.md)  
  
  
