---
title: "Création de fichiers de la valeur de la Variable (OracleToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Variable Value File Creation
- Variable Value File, Variable Value File Validation
ms.assetid: f583d81a-8e34-41b1-8100-ee3a6a82213b
caps.latest.revision: "26"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 5a311dfe5be380a1e4b5fc7cf65eb84fe942d872
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="creating-variable-value-files-oracletosql"></a>Création de fichiers de la valeur de la Variable (OracleToSQL)
Fichier de la valeur de variable est un fichier XML contenant les valeurs de paramètre de commandes, comme le nom du serveur source ou de destination qui changent fréquemment à partir de la migration d’un serveur vers un autre. En cas d’un grand nombre de migrations de la base de données, plusieurs fichiers de variables pour stocker la valeur de chaque serveur source seront créés et référencés dans un fichier de script principal avec le **– v** passer à la ligne de commande. Cela permet de conserver des valeurs statiques dans plusieurs fichiers de script avec les valeurs des variables dans plusieurs fichiers de variable.  
  
> [!NOTE]  
> 1.  Les noms de variables ont le préfixe et suffixe avec un symbole $ (dollar). Si les variables ne sont pas attribués une valeur dans le fichier de la valeur de la variable, vous rencontrerez une erreur lors de l’analyse du fichier de script résultant de bloquer le processus d’exécution de console.  
> 2.  The escape character for **$** is **$$**. Si la valeur d’une valeur d’un paramètre de variable ou statique contient  **$**  symbole (dollar), puis  **$$**  doit être spécifié pour le traiter comme un caractère au lieu d’une variable.  
> 3.  À des fins de facilité de maintenance, les variables peuvent être déclarées à l’intérieur de `‘variable-group’` variables définies par des éléments pour une séparation logique de l’utilisateur.  L’utilisation de cet élément n’est pas obligatoire.  
  
**Exemples :**  
  
**Exemple 1 :**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<project-folder>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**Exemple 2 :**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
      <variable name="$TargetPassword$" value="<password>"/>  
  
      <variable name="$TrustedConnection$" value="<true/false>"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="<object-name>"/>  
  
      <variable name="$ObjectName2$" value="<object-name>"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante d’exploitation de la console est [créer les fichiers de connexion de serveur &#40; OracleToSQL &#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Création des fichiers de serveur (Oracle)](http://msdn.microsoft.com/en-us/002f129e-0868-48ad-a4b4-c68b5007e12e)  
  
