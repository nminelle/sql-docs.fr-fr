---
title: "Paramètres globaux (journalisation) (AccessToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 835b09b5-eb42-47ea-b46e-e115d4d6461f
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 07f20237ec7bdf7e7da927eeeb0b7b15bcb6ad7b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="global-settings-logging-accesstosql"></a>Paramètres globaux (journalisation) (AccessToSQL)
Utilisez le **paramètres globaux** boîte de dialogue pour spécifier les paramètres de journalisation pour SSMA. En règle générale, il faudrait modifier ces paramètres uniquement lorsque vous travaillez avec le support technique.  
  
Pour accéder à cette boîte de dialogue, dans le **outils** menu, sélectionnez **paramètres globaux** puis cliquez sur le **journalisation** situé en bas du volet gauche.  
  
## <a name="options"></a>Options  
**Au niveau des messages**  
Les options suivantes sont disponibles sous **au niveau des Messages**:  
  
|Option|Description|  
|----------|---------------|  
|**[toutes les catégories]**|Utilisé pour définir le niveau de journalisation pour toutes les options suivantes.|  
|**Collecteur**|Collecte des métadonnées sur le schéma source et l’enregistre dans le projet.|  
|**Convertisseur**|Convertit des objets de base de données source, tels que les tables et procédures stockées, des structures de correspondant [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] structures.|  
|**Utilitaire de migration de données**|Migre les données à partir de la base de données source dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|**Formateur**|Sous-composant du convertisseur qui génère des scripts pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schéma.|  
|**Interface utilisateur graphique**|Messages qui s’affichent lorsque vous utilisez l’outil SSMA.|  
|**Éditeur de liens**|Résout les identificateurs SQL et fournit des informations à d’autres composants.|  
|**Autres**|Tous les messages qui ne sont pas dans une autre catégorie.|  
|**Analyseur**|Analyse du schéma source.|  
|**Synchronisateur**|Charge la source des objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|**TreeConverter**|Convertit des objets dans les métadonnées de la source en [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] métadonnées.|  
  
Pour chaque option sous **au niveau des Messages**, configurez l’un des niveaux de journalisation suivants pour SSMA :  
  
|||  
|-|-|  
|**Erreur irrécupérable**|Écrire uniquement les messages d’erreur irrécupérable dans le journal.|  
|**Erreur**|Écrire des messages d’erreur et erreur irrécupérable dans le journal.|  
|**Avertissement**|Écrire des messages d’avertissement, erreur et erreur irrécupérable dans le journal.|  
|**Info**|Écrire des information, avertissement, messages d’erreur et erreur irrécupérable dans le journal.|  
|**Débogage**|Écrire tous les messages, y compris les messages, dans le journal de débogage.|  
  
**Chemin du fichier journal**  
Le chemin d’accès et le nom des fichiers journaux SSMA. Pour spécifier un nom différent, cliquez sur le chemin d’accès actuel, puis cliquez sur le bouton de navigation (**...** ) bouton.  
  
**Taille du fichier journal**  
La taille maximale du fichier journal en Ko. La taille minimale est de 10 Ko. La taille par défaut est 10 240 Ko.  
  
**Nombre total de fichiers journaux**  
Lorsqu’un journal est saturé, SSMA sera renommer le fichier journal et démarrer une nouvelle. À l’aide de ce paramètre, spécifiez le nombre maximal de fichiers journaux à conserver. La valeur minimale est 2.  
  
