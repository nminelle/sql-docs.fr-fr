---
title: Gestion des packages et des dossiers par programmation | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: run-manage-packages-programmatically
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4d0213c5ae32099a934daf88c2c60ef12204b86c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="managing-packages-and-folders-programmatically"></a>Gestion des packages et des dossiers par programme
<a name="top"></a> Quand vous travaillez par programmation avec des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez avoir besoin de déterminer si un package ou un dossier individuel existe, ou de gérer les dossiers dans lesquels les packages sont stockés. La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> de l'espace de noms <xref:Microsoft.SqlServer.Dts.Runtime> fournit différentes méthodes pour répondre à ces impératifs.    
    
##  <a name="exists"></a> Détermination de l’existence d’un package ou dossier    
 Pour déterminer par programmation si un package enregistré existe, appelez l’une des méthodes suivantes avant de tenter de le charger et l’exécuter :    
    
|Emplacement de stockage|Méthode à appeler|    
|----------------------|--------------------|    
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|    
    
 Pour déterminer par programme si un dossier existe, appelez l'une des méthodes suivantes avant de tenter de répertorier les packages stockés dans ce dossier :    
    
|Emplacement de stockage|Méthode à appeler|    
|----------------------|--------------------|    
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|    
    
 [Retour au début](#top)    
    
##  <a name="managing"></a> Gestion des packages et des dossiers    
 La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> de l'espace de noms <xref:Microsoft.SqlServer.Dts.Runtime> fournit des méthodes supplémentaires pour gérer les packages et les dossiers dans lesquels ils sont stockés.    
    
###  <a name="managing_rempkg"></a> Suppression d’un package    
 Pour supprimer un package enregistré par programme, appelez l'une des méthodes suivantes :    
    
|Emplacement de stockage|Méthode à appeler|    
|----------------------|--------------------|    
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|    
    
 [Retour au début](#top)    
    
###  <a name="managing_create"></a> Création d’un dossier    
 Pour créer un dossier de stockage par programme, appelez l'une des méthodes suivantes :    
    
|Emplacement de stockage|Méthode à appeler|    
|----------------------|--------------------|    
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|    
    
 [Retour au début](#top)    
    
###  <a name="managing_remfldr"></a> Suppression d’un dossier    
 Pour supprimer un dossier de stockage par programme, appelez l'une des méthodes suivantes :    
    
|Emplacement de stockage|Méthode à appeler|    
|----------------------|--------------------|    
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|    
    
 [Retour au début](#top)    
    
###  <a name="managing_rename"></a> Renommage d’un dossier    
 Pour renommer un dossier de stockage par programme, appelez l'une des méthodes suivantes :    
    
|Emplacement de stockage|Méthode à appeler|    
|----------------------|--------------------|    
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|    
    
 [Retour au début](#top)    
    
## <a name="see-also"></a> Voir aussi    
 [Gestion de packages &#40;Service SSIS&#41;](../../integration-services/service/package-management-ssis-service.md)     
 [Énumération des packages disponibles par programmation](../../integration-services/run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)    
    
  
