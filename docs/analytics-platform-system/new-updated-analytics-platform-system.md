---
title: "Mise à jour - système de plateforme d’Analytique des documents de SQL Server | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié, pour le système de plateforme Analytique pour Microsoft SQL Server."
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: aps-pdw
ms.date: 02/03/2018
ms.openlocfilehash: 2ae6339897b52cd16ad3417cc218afe1df95ba2a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-analytics-platform-system-for-sql-server"></a>Nouveaux et mis à jour récemment : système de plateforme d’Analytique pour SQL Server



Presque tous les jours Microsoft met à jour certains de ses articles existants sur son [Docs.Microsoft.com](http://docs.microsoft.com/) site Web de documentation. Cet article affiche des extraits d’articles récemment mis à jour. Des liens vers nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme est exécuté à nouveau régulièrement. Parfois un extrait peut apparaître avec mise en forme imparfait, ou en tant que markdown de l’article de la source. Les images ne sont jamais affichés ici.

Mises à jour récentes sont signalés pour la plage de dates suivante et l’objet :



- *Plage de dates de mises à jour :* &nbsp; **2017-12-03** &nbsp; - à - &nbsp; **2018-02-03**
- *Zone de sujet :* &nbsp; **système de plateforme d’Analytique pour SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux Articles vient d’être créés

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


***Il n’y a aucun nouvel article.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés à partir de leur contexte sémantique spécifique. En outre, parfois un extrait est séparé à partir de la syntaxe markdown important qui l’entoure dans l’article. Par conséquent, ces extraits sont pour des conseils généraux. Les extraits permettent uniquement de savoir si votre intérêt justifie pris le temps de cliquer sur et consultez l’article.

Pour celles-ci et d’autres raisons, ne pas copier le code à partir de ces extraits et ne prennent pas en tant que vérité exacte tout extrait de texte. Au lieu de cela, consultez l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’Articles récemment mis à jour

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Configurer la connectivité PolyBase pour données externes](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-polybase-connectivity-to-external-dataconfigure-polybase-connectivity-to-external-datamd"></a>1. &nbsp;[Configurer la connectivité PolyBase pour données externes](configure-polybase-connectivity-to-external-data.md)

*Mise à jour : 2018-01-29* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 132.  ms.author= "barbkess".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 947f789480da66b9f636f39b30caec6be60d8c4d d4d4d45fbbb8e10ed6f26fe12f9a25d2e8e4f068  (PR=4741  ,  Filename=configure-polybase-connectivity-to-external-data.md  ,  Dirpath=docs\analytics-platform-system\  ,  MergeCommitSha40=0a44ce9993ebf61f86e409255a1d58d47993951a) -->



**Configuration de Kerberos**

Notez que lorsque PolyBase s’authentifie auprès d’un cluster sécurisé Kerberos, le paramètre hadoop.rpc.protection doit être défini à l’authentification. Cette opération laisse la communication de données entre les nœuds Hadoop non chiffrés.

 Pour se connecter à un cluster Hadoop sécurisé Kerberos [à l’aide de MIT KDC] :


1.  Rechercher le répertoire de configuration Hadoop dans le chemin d’accès de l’installation sur le nœud de contrôle :

    ```
    C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf
    ```

2.  Recherchez la valeur de configuration côté Hadoop des clés de configuration répertoriées dans le tableau. Sur l’ordinateur Hadoop, recherchez les fichiers dans le répertoire de configuration Hadoop.

3.  Copiez les valeurs de configuration dans la propriété de valeur dans les fichiers correspondants sur le nœud de contrôle.

    |**#**|**Fichier de configuration**|**Clé de configuration**|**Action**|
    |------------|----------------|---------------------|----------|
    |1|core-site.xml|polybase.kerberos.kdchost|Spécifiez le nom d’hôte KDC. Par exemple : kerberos.votre-domaine.com.|
    |2|core-site.xml|polybase.kerberos.realm|Spécifiez le domaine Kerberos. Par exemple : VOTRE-DOMAINE.COM|
    |3|core-site.xml|hadoop.security.authentication|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : KERBEROS<br></br>**Note de sécurité :** KERBEROS doit être écrit en majuscules. Dans le cas contraire, il pourrait ne pas être activé.|
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : hdfs/_HOST@YOUR-REALM.COM|
    |5|mapred-site.xml|mapreduce.jobhistory.principal|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : mapred/_HOST@YOUR-REALM.COM|
    |6|mapred-site.xml|mapreduce.jobhistory.address|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : 10.193.26.174:10020|
    |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Recherchez la configuration côté Hadoop et copiez-la sur l’ordinateur SQL Server. Par exemple : yarn/_HOST@YOUR-REALM.COM|







## <a name="similar-articles-about-new-or-updated-articles"></a>Articles similaires sur les articles nouveaux ou mis à jour

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Zones de sujet qui *faire* ont nouveaux ou récemment mis à jour articles


- [Nouveau + mis à jour (1 + 3) :&nbsp; **avancées d’Analytique pour SQL** documents](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveau + mis à jour (0 + 1) :&nbsp; **système de plateforme d’Analytique pour SQL** documents](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveau + mis à jour (0 + 1) :&nbsp; **se connecter à SQL** documents](../connect/new-updated-connect.md)
- [Nouveau + mis à jour (0 + 1) :&nbsp; **moteur de base de données pour SQL** documents](../database-engine/new-updated-database-engine.md)
- [Nouveau + mis à jour (12 + 1) : **Integration Services pour SQL** documents](../integration-services/new-updated-integration-services.md)
- [Nouveau + mis à jour (6 + 2) :&nbsp; **Linux pour SQL** documents](../linux/new-updated-linux.md)
- [Nouveau + mis à jour (15 + 0) : **PowerShell pour SQL** documents](../powershell/new-updated-powershell.md)
- [Nouveau + mis à jour (2 + 9) :&nbsp; **des bases de données relationnelles pour SQL** documents](../relational-databases/new-updated-relational-databases.md)
- [Nouveau + mis à jour (1 + 0) :&nbsp; **Reporting Services pour SQL** documents](../reporting-services/new-updated-reporting-services.md)
- [Nouveau + mis à jour (1 + 1) :&nbsp; **SQL opérations Studio** documents](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveau + mis à jour (1 + 1) :&nbsp; **Microsoft SQL Server** documents](../sql-server/new-updated-sql-server.md)
- [Nouveau + mis à jour (0 + 1) :&nbsp; **SQL Server Data Tools (SSDT)** documents](../ssdt/new-updated-ssdt.md)
- [Nouveau + mis à jour (1 + 2) :&nbsp; **SQL Server Management Studio (SSMS)** documents](../ssms/new-updated-ssms.md)
- [Nouveau + mis à jour (0 + 2) :&nbsp; **Transact-SQL** documents](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Zones de font l’objet *pas* ont tous nouveaux ou récemment mis à jour articles


- [Nouveaux + Mis à jour (0 + 0) : **Data Migration Assistant (DMA) pour SQL** (documentation)](../dma/new-updated-dma.md)
- [Nouveau + mis à jour (0 0 +) : **ActiveX Data Objects (ADO) pour SQL** documents](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveau + mis à jour (0 0 +) : **Data Quality Services pour SQL** documents](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveau + mis à jour (0 0 +) : **Extensions DMX (Data Mining) pour SQL** documents](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveau + mis à jour (0 0 +) : **MDX (Multidimensional Expressions) pour SQL** documents](../mdx/new-updated-mdx.md)
- [Nouveau + mis à jour (0 0 +) : **ODBC (Open Database Connectivity) pour SQL** documents](../odbc/new-updated-odbc.md)
- [Nouveau + mis à jour (0 0 +) : **exemples pour SQL** documents](../sample/new-updated-sample.md)
- [Nouveau + mis à jour (0 0 +) : **SQL Server Migration Assistant (SSMA)** documents](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveau + mis à jour (0 0 +) : **XQuery pour SQL** documents](../xquery/new-updated-xquery.md)


