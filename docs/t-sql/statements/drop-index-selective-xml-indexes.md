---
title: "DROP INDEX (index XML sélectifs) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP XML INDEX statement
dev_langs:
- TSQL
ms.assetid: 4779ae84-e5f4-4d04-8fc1-e24a6631b428
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 23cac56c86855978442dd971d69abe1323423d0b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="drop-index-selective-xml-indexes"></a>DROP INDEX (index XML sélectifs)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Supprime un index XML sélectif existant ou l'index XML secondaire sélectif dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Index XML sélectifs &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DROP INDEX index_name ON <object>  
    [ WITH ( <drop_index_option> [ ,...n ] ) ]  
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
        table_or_view_name  
}  
  
<drop_index_option> ::=  
{  
    MAXDOP = max_degree_of_parallelism  
    | ONLINE = { ON | OFF }  
}  
```  
  
##  <a name="Arguments"></a> Arguments  
 *index_name*  
 Nom de l'index existant à supprimer.  
  
 *\<objet >* est la table qui contient la colonne XML indexée. Utilisez l'un des éléments suivants :  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
-   `table_name`  
  
 *\<drop_index_option >* pour plus d’informations sur les options d’index de liste, consultez [DROP INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/drop-index-transact-sql.md).  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 L'exécution de DROP INDEX nécessite une autorisation ALTER sur la table ou la vue. L'autorisation est accordée par défaut au rôle serveur fixe sysadmin et aux rôles de base de données fixes db_ddladmin et db_owner.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre une instruction DROP INDEX.  
  
```  
DROP INDEX sxi_index ON tbl;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Index XML sélectifs &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [Créer, modifier ou supprimer des index XML sélectifs](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)  
  
  

