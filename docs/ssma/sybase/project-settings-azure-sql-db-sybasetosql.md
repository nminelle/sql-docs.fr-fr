---
title: "Paramètres (base de données SQL Azure) du projet (SybaseToSQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 57002374-0d4d-43c1-b4e9-cbec02355a9c
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c6d39a4ceb167746ffe1f47528ac8e042f45715a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="project-settings-azure-sql-db--sybasetosql"></a>Paramètres (base de données SQL Azure) du projet (SybaseToSQL)
Les paramètres de projet de base de données SQL Azure vous permettent de configurer le suffixe de base de données de base de données SQL Azure à ajouter dans la boîte de dialogue de connexion et permettent également à implémenter un mécanisme de pulsation dans la connexion de base de données SQL Azure.  
  
Le volet de la base de données SQL Azure est disponible dans le **les paramètres de projet** et **les paramètres de projet par défaut** boîtes de dialogue.  
  
-   Utilisez la boîte de dialogue Paramètres du projet pour définir les options de configuration pour le projet actuel. Pour accéder aux paramètres de base de données SQL Azure, sur le **outils** menu, sélectionnez **les paramètres de projet**, cliquez sur **général** en bas du volet gauche, puis **base de données SQL Azure**.  
  
-   Utilisez la boîte de dialogue Paramètres du projet par défaut pour définir les options de configuration pour tous les projets. Pour accéder aux paramètres de base de données SQL Azure, sur le **outils** menu, sélectionnez **DefaultProject paramètres**, cliquez sur **général** en bas du volet gauche, puis **base de données SQL Azure**.  
  
## <a name="connectivity"></a>Connectivité  
**Intervalle de pulsation**  
  
Spécifie un intervalle de temps à utiliser pour le mécanisme de pulsation afin de maintenir la connexion de base de données SQL Azure dans ' minutes : format des secondes.  
  
**Valeur par défaut**:' 4:45 '  
  
La valeur doit être spécifiée dans suis : format des ss (par exemple, ' 4:45 ' ou ' 0:50 ').  
  
**Suffixe de serveur de base de données SQL Azure**  
  
Spécifie un suffixe de serveur de base de données SQL Azure  
  
**Valeur par défaut**: 'database.windows.net'.  
  
