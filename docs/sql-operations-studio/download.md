---
title: "Téléchargez et installez Microsoft SQL Studio Operations (version préliminaire) | Documents Microsoft"
description: "Téléchargez et installez Microsoft SQL opérations Studio (version préliminaire) pour Windows, Mac OS ou Linux"
ms.custom: tools|sos
ms.date: 03/05/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1cb41e1824fc157932e2cb08292608bb97e46712
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="download-and-install-sql-operations-studio-preview"></a>Téléchargez et installez Studio des opérations SQL (version préliminaire)

[!INCLUDE[name-sos](../includes/name-sos.md)] s’exécute sur Windows, Mac OS et Linux.

Téléchargez et installez la dernière version, le *Public Preview de février*:

|Plateforme|Télécharger|Date de publication| Version |
|:---|:---|:---|:---|
|Windows|[Programme d’installation](https://go.microsoft.com/fwlink/?linkid=867998)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=867997)|15 février 2018 |0.26.7|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=867999)|15 février 2018 |0.26.7|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=868002)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=868001)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=868000)|15 février 2018|0.26.7|

Pour plus d’informations sur la dernière version, consultez le [notes de publication](release-notes.md).

## <a name="get-sql-operations-studio-preview-for-windows"></a>Obtenir des opérations de SQL Studio (version préliminaire) pour Windows

Cette version de [!INCLUDE[name-sos](../includes/name-sos-short.md)] inclut une expérience de programme d’installation Windows standard et un fichier zip : 

**Programme d’installation**

1. Téléchargez et exécutez le [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] programme d’installation de Windows](https://go.microsoft.com/fwlink/?linkid=867998).
1. Démarrer le [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] application.


**fichier .zip**

1. Télécharger [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] .zip pour Windows](https://go.microsoft.com/fwlink/?linkid=867997).
2. Recherchez le fichier téléchargé et extrayez-le.
3. Exécutez `\sqlops-windows\sqlops.exe`


## <a name="get-sql-operations-studio-preview-for-macos"></a>Obtenir des opérations de SQL Studio (version préliminaire) pour Mac OS

1. Télécharger [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour macOS](https://go.microsoft.com/fwlink/?linkid=867999).
2. Pour développer le contenu du fichier zip, double-cliquez dessus.
3. Pour rendre [!INCLUDE[name-sos](../includes/name-sos-short.md)] disponibles dans le *Launchpad*, faites glisser *sqlops.app* à la *Applications* dossier.


## <a name="get-sql-operations-studio-preview-for-linux"></a>Obtenir des opérations de SQL Studio (version préliminaire) pour Linux

1. Télécharger [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour Linux](https://go.microsoft.com/fwlink/?linkid=868000).
1. Pour extraire le fichier et le lancement [!INCLUDE[name-sos](../includes/name-sos-short.md)], ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   ```bash
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
   ```

   > [!NOTE]
   > Pour Debian, Redhat et Ubuntu, vous pouvez avoir de dépendances manquantes. Pour installer ces dépendances selon votre version de Linux, utilisez les commandes suivantes :
   

   **Debian :** 
   ```bash
   sudo apt-get install libuwind8
   ```

   **Redhat :** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu :** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```


## <a name="uninstall-sql-operations-studio-preview"></a>Désinstaller SQL opérations Studio (version préliminaire)

Si vous avez installé [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] à l’aide de Windows installer, désinstaller puis de la même manière que n’importe quelle application Windows.

Si vous avez installé [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] avec un fichier ZIP ou autre archive, puis supprimez simplement les fichiers.

## <a name="supported-operating-systems"></a>Systèmes d'exploitation pris en charge

[!INCLUDE[name-sos](../includes/name-sos-short.md)] s’exécute sur Windows, Mac OS et Linux et est pris en charge sur les plateformes suivantes :

### <a name="windows"></a>Windows
- Windows 10 (64 bits)
- Windows 8.1 (64 bits)
- Windows 8 (64 bits)
- Windows 7 (SP1) (64 bits) - nécessite [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64 bits)
- Windows Server 2012 (64 bits)
- Windows Server 2008 R2 (64 bits)

### <a name="macos"></a>macOS
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="check-for-updates"></a>Rechercher des mises à jour
Pour vérifier les dernières mises à jour, cliquez sur l’icône d’engrenage en bas à gauche de la fenêtre et cliquez sur **vérifier les mises à jour**

## <a name="next-steps"></a>Étapes suivantes

Consultez une des Démarrages rapides suivants pour commencer :
- [Se connecter et de requêtes SQL Server](quickstart-sql-server.md)
- [Se connecter et interroger la base de données SQL Azure](quickstart-sql-database.md)
- [Connecter la re & quête d’entrepôt de données Azure](quickstart-sql-dw.md)

Contribuer à [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) et [collecte des données d’utilisation](usage-data-collection.md).
