---
title: "Utiliser des données JSON dans SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 02/19/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- JSON
- JSON, built-in support
ms.assetid: c9a4e145-33c3-42b2-a510-79813e67806a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 92bac08a5168cb60477f8d253a9fee1f0fb5caef
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2018
---
# <a name="json-data-in-sql-server"></a>Données JSON dans SQL Server
[!INCLUDE[appliesto-ss2016-asdb-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

JSON est un format de données textuelles répandu qui est utilisé pour échanger des données dans des applications mobiles et web modernes. JSON est aussi utilisé pour stocker des données non structurées dans des fichiers journaux ou des bases de données NoSQL telles que Microsoft Azure Cosmos DB. Nombreux sont les services web REST qui retournent des résultats sous forme de texte JSON ou qui acceptent des données au format JSON. Par exemple, la plupart des services Azure, tels que Recherche Azure, Stockage Azure et Azure Cosmos DB, ont des points de terminaison REST qui retournent ou utilisent des données JSON. JSON est aussi le principal format d’échange de données entre les pages web et les serveurs web en utilisant des appels AJAX. 

Les fonctions JSON dans SQL Server vous permettent de combiner des concepts relationnels et NoSQL dans la même base de données. Vous pouvez maintenant combiner des colonnes relationnelles standard avec des colonnes qui contiennent des documents formatés comme du texte JSON dans la même table, analyser et importer des documents JSON dans des structures relationnelles ou appliquer à des données relationnelles le format de texte JSON. Vous pouvez voir comment les fonctions JSON connectent les concepts relationnels et NoSQL dans SQL Server et Azure SQL Database dans la vidéo suivante :

*JSON : un pont entre les mondes relationnel et NoSQL*
> [!VIDEO https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds/player]
 
Voici un exemple de texte JSON : 
 
```json 
[{
    "name": "John",
    "skills": ["SQL", "C#", "Azure"]
}, {
    "name": "Jane",
    "surname": "Doe"
}]
``` 
 
À l’aide des fonctions et des opérateurs SQL Server intégrés, vous pouvez effectuer les opérations suivantes avec le texte JSON : 
 
- Analyser du texte JSON et lire ou modifier des valeurs  
- Transformer des tableaux d’objets JSON au format table  
- Exécuter une requête Transact SQL sur les objets JSON convertis  
- Mettre en forme les résultats des requêtes Transact-SQL au format JSON  
  
![Vue d’ensemble de la prise en charge intégrée de JSON](../../relational-databases/json/media/jsonslides1overview.png "Vue d’ensemble de la prise en charge intégrée de JSON")  
  
## <a name="key-json-capabilities-of-sql-server-and-sql-database"></a>Principales fonctionnalités JSON de SQL Server et de SQL Database
Les sections suivantes abordent les fonctionnalités clés fournies par SQL Server avec sa prise en charge intégrée de JSON. Vous pouvez voir comment utiliser des opérateurs et fonctions JSON dans la vidéo suivante :

*SQL Server 2016 et prise en charge de JSON*
> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support/player]

### <a name="extract-values-from-json-text-and-use-them-in-queries"></a>Extraire les valeurs de texte JSON et les utiliser dans les requêtes
Si vous avez stocké du texte JSON dans des tables de base de données, vous pouvez lire ou modifier les valeurs présentes dans le texte JSON à l’aide des fonctions intégrées suivantes :  
  
-   **JSON_VALUE** extrait une valeur scalaire à partir d’une chaîne JSON.
-   **JSON_QUERY** extrait un objet ou un tableau à partir d’une chaîne JSON.
-   **ISJSON** teste si une chaîne contient un JSON valide.
-   **JSON_MODIFY** change une valeur dans une chaîne JSON.

**Exemple**
  
Dans l’exemple suivant, la requête utilise à la fois les données relationnelles et les données JSON (stockées dans une colonne nommée `jsonCol`) dans une table :  
  
```sql  
SELECT Name,Surname,
 JSON_VALUE(jsonCol,'$.info.address.PostCode') AS PostCode,
 JSON_VALUE(jsonCol,'$.info.address."Address Line 1"')+' '
  +JSON_VALUE(jsonCol,'$.info.address."Address Line 2"') AS Address,
 JSON_QUERY(jsonCol,'$.info.skills') AS Skills
FROM People
WHERE ISJSON(jsonCol)>0
 AND JSON_VALUE(jsonCol,'$.info.address.Town')='Belgrade'
 AND Status='Active'
ORDER BY JSON_VALUE(jsonCol,'$.info.address.PostCode')
```  
  
Les applications et les outils ne font aucune différence entre les valeurs tirées de colonnes de table scalaire et les valeurs tirées de colonnes JSON. Vous pouvez utiliser des valeurs de texte JSON dans n’importe quelle partie de requête Transact-SQL (notamment les clauses WHERE, ORDER BY ou GROUP BY, les agrégats de fenêtre, etc.). Les fonctions JSON utilisent une syntaxe de type JavaScript pour faire référence aux valeurs contenues dans du texte JSON.

Pour plus d’informations, consultez [Valider, interroger et modifier les données JSON avec des fonctions intégrées (SQL Server)](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md), [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md) et [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md).  
  
### <a name="change-json-values"></a>Modifier les valeurs JSON
Si vous devez modifier des parties de texte JSON, vous pouvez utiliser la fonction **JSON_MODIFY** pour mettre à jour une valeur de propriété de chaîne JSON et retourner la chaîne JSON mise à jour. L’exemple suivant met à jour la valeur d’une propriété dans une variable contenant du texte JSON :  
  
```sql  
DECLARE @jsonInfo NVARCHAR(MAX)

SET @jsonInfo=JSON_MODIFY(@jsonInfo,'$.info.address[0].town','London') 
```  
  
### <a name="convert-json-collections-to-a-rowset"></a>Convertir des collections JSON en ensemble de lignes
Vous n’avez pas besoin d’un langage de requête personnalisé pour interroger les données JSON dans SQL Server. Pour interroger des données JSON, vous pouvez utiliser le langage T-SQL standard. Si vous devez créer une requête ou un rapport sur des données JSON, vous pouvez facilement convertir les données JSON en lignes et colonnes en appelant la fonction d’ensemble de lignes **OPENJSON**. Pour plus d’informations, consultez [Convertir des données JSON en lignes et colonnes avec OPENJSON (SQL Server)](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md).  
  
L’exemple suivant appelle **OPENJSON** et transforme le tableau d’objets stocké dans la variable `@json` en un ensemble de lignes qui peut être interrogé à l’aide de l’instruction SQL **SELECT** standard :  
  
```sql  
DECLARE @json NVARCHAR(MAX)
SET @json =  
N'[  
       { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },  
       { "id" : 5,"info": { "name": "Jane", "surname": "Smith" }, "dob": "2005-11-04T12:00:00" }  
 ]'  
   
SELECT *  
FROM OPENJSON(@json)  
  WITH (id int 'strict $.id',  
        firstName nvarchar(50) '$.info.name', lastName nvarchar(50) '$.info.surname',  
        age int, dateOfBirth datetime2 '$.dob')  
```  
  
**Résultats**  
  
|id|firstName|lastName|age|dateOfBirth|  
|--------|---------------|--------------|---------|-----------------|  
|2|John|Smith|25||  
|5|Jane|Smith||2005-11-04T12:00:00|  
  
**OPENJSON** transforme le tableau d’objets JSON en table dans laquelle chaque objet est représenté par une ligne, et des paires clé-valeur sont retournées sous forme de cellules. La sortie respecte les règles suivantes :
- **OPENJSON** convertit les valeurs JSON aux types spécifiés dans la clause **WITH**.
- **OPENJSON** peut gérer à la fois les paires clé-valeur plates et les objets imbriqués organisés en hiérarchie.
- Vous n’êtes pas obligé de retourner tous les champs contenus dans le texte JSON.
- S’il n’existe pas de valeurs JSON, **OPENJSON** retourne des valeurs NULL.
- Vous pouvez éventuellement spécifier un chemin après la spécification du type pour référencer une propriété imbriquée ou une propriété avec un autre nom.
- Le préfixe facultatif **strict** figurant dans le chemin indique que des valeurs doivent exister dans le texte JSON pour les propriétés spécifiées.

Pour plus d’informations, consultez [Convertir des données JSON en lignes et colonnes avec OPENJSON (SQL Server)](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md) et [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md).  
  
### <a name="convert-sql-server-data-to-json-or-export-json"></a>Convertir des données SQL Server au format JSON ou exporter des données JSON
Mettez les données SQL Server ou les résultats des requêtes au format JSON en ajoutant la clause **FOR JSON** à une instruction **SELECT** . Utilisez **FOR JSON** pour déléguer la mise en forme de la sortie JSON produite par vos applications clientes à SQL Server. Pour plus d’informations, consultez [Mettre les résultats de requête au format JSON avec FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
L’exemple suivant utilise le mode PATH avec la clause **FOR JSON** :  
  
```sql  
SELECT id, firstName AS "info.name", lastName AS "info.surname", age, dateOfBirth as dob  
FROM People  
FOR JSON PATH  
```  
  
La **FOR JSON** met les résultats SQL sous forme de texte JSON qui peut être fourni à n’importe quelle application capable de comprendre JSON. L’option PATH utilise des alias séparés par des points dans la clause SELECT pour imbriquer des objets dans les résultats de requête.  
  
**Résultats**  
  
```json  
[{
    "id": 2,
    "info": {
        "name": "John",
        "surname": "Smith"
    },
    "age": 25
}, {
    "id": 5,
    "info": {
        "name": "Jane",
        "surname": "Smith"
    },
    "dob": "2005-11-04T12:00:00"
}] 
```  
  
Pour plus d’informations, consultez [Mettre les résultats de requête au format JSON avec FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md) et [Clause FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md).  
  
## <a name="combine-relational-and-json-data"></a>Combiner des données relationnelles et des données JSON
SQL Server met à disposition un modèle hybride pour stocker et traiter les données relationnelles et JSON en utilisant le langage Transact-SQL standard. Vous pouvez organiser des regroupements de vos documents JSON dans des tables, établir des relations entre eux, combiner des colonnes scalaires fortement typées stockées dans des tables contenant des paires clé-valeur flexibles dans des colonnes JSON, et interroger les valeurs scalaires et JSON dans une ou plusieurs tables en utilisant la syntaxe Transact-SQL complète.
 
Le texte JSON est stocké dans des colonnes varchar ou nvarchar et est indexé sous forme de texte brut. Sachant qu’une fonctionnalité ou un composant SQL Server qui prend en charge le texte prend aussi en charge JSON, il n’y a quasiment aucune contrainte dans l’interaction entre JSON et les autres fonctionnalités SQL Server. Vous pouvez stocker du texte JSON dans des tables en mémoire ou temporelles, appliquer des prédicats de sécurité au niveau des lignes sur du texte JSON, et ainsi de suite.

Si vous avez des charges de travail JSON pures dans lesquelles vous voulez utiliser un langage de requête personnalisé pour le traitement des documents JSON, songez à Microsoft Azure [Cosmos DB](https://azure.microsoft.com/services/cosmos-db/).  
  
Voici quelques cas d’utilisation qui vous montrent comment utiliser la prise en charge JSON intégrée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

## <a name="store-and-index-json-data-in-sql-server"></a>Stocker et indexer des données JSON dans SQL Server

Pour plus d’informations sur les options de stockage, d’indexation et d’optimisation des données JSON dans SQL Server, consultez les articles suivants :
-   [Stocker des documents JSON dans SQL Server ou SQL Database](store-json-documents-in-sql-tables.md)
-   [Indexer des données JSON](index-json-data.md)
-   [Optimiser le traitement JSON avec OLTP en mémoire](optimize-json-processing-with-in-memory-oltp.md)

### <a name="load-json-files-into-sql-server"></a>Charger de fichiers JSON dans SQL Server  
Vous pouvez mettre les informations stockées dans les fichiers au format JSON standard ou JSON délimité par des lignes. SQL Server peut importer le contenu de fichiers JSON, l’analyser à l’aide des fonctions **OPENJSON** ou **JSON_VALUE**, puis le charger dans des tables.  
  
-   Si vos documents JSON sont stockés dans des fichiers locaux, sur des lecteurs réseau partagés ou à des emplacements Azure Files accessibles par SQL Server, vous pouvez recourir à l’importation en bloc pour charger vos données JSON dans SQL Server. Pour plus d’informations sur ce scénario, consultez [Importing JSON files into SQL Server using OPENROWSET (BULK)](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2015/10/07/importing-json-files-into-sql-server-using-openrowset-bulk.aspx)[Importation de fichiers JSON dans SQL Server à l’aide de OPENROWSET (BULK)].  
  
-   Si vos fichiers au format JSON délimité par des lignes sont stockés dans le stockage blob Azure ou le système de fichiers Hadoop, vous pouvez utiliser PolyBase pour charger le texte JSON, l’analyser dans du code Transact-SQL et le charger dans des tables.  

### <a name="import-json-data-into-sql-server-tables"></a>Importer des données JSON dans des tables SQL Server  
Si vous devez charger des données JSON dans SQL Server à partir d’un service externe, vous pouvez utiliser **OPENJSON** pour importer les données dans SQL Server au lieu d’analyser les données dans la couche application.  
  
```sql  
DECLARE @jsonVariable NVARCHAR(MAX)

SET @jsonVariable = N'[  
        {  
          "Order": {  
            "Number":"SO43659",  
            "Date":"2011-05-31T00:00:00"  
          },  
          "AccountNumber":"AW29825",  
          "Item": {  
            "Price":2024.9940,  
            "Quantity":1  
          }  
        },  
        {  
          "Order": {  
            "Number":"SO43661",  
            "Date":"2011-06-01T00:00:00"  
          },  
          "AccountNumber":"AW73565",  
          "Item": {  
            "Price":2024.9940,  
            "Quantity":3  
          }  
       }  
  ]'
  
INSERT INTO SalesReport  
SELECT SalesOrderJsonData.*  
FROM OPENJSON (@jsonVariable, N'$.Orders.OrdersArray')  
           WITH (  
              Number   varchar(200) N'$.Order.Number',   
              Date     datetime     N'$.Order.Date',  
              Customer varchar(200) N'$.AccountNumber',   
              Quantity int          N'$.Item.Quantity'  
           )  
  AS SalesOrderJsonData;  
```  
  
Vous pouvez fournir le contenu de la variable JSON par le biais d’un service REST externe, l’envoyer en tant que paramètre à partir d’un framework JavaScript côté client ou le charger à partir de fichiers externes. Vous pouvez facilement insérer, mettre à jour ou fusionner les résultats du texte JSON dans une table SQL Server. Pour plus d’informations sur ce scénario, consultez les billets de blog suivants :
-   [Import JSON data in SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/09/22/openjson-the-easiest-way-to-import-json-text-into-table/) (Importer des données JSON dans SQL Server)
-   [Upsert JSON documents in SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/03/upsert-json-documents-in-sql-server-2016)
-   [Load GeoJSON data into SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/loading-geojson-data-into-sql-server/) (Charger des données GeoJSON dans SQL Server 2016)  

## <a name="analyze-json-data-with-sql-queries"></a>Analyser des données JSON à l’aide de requêtes SQL  
Si vous devez filtrer ou agréger des données JSON pour générer des rapports, vous pouvez utiliser **OPENJSON** pour transformer les données JSON au format relationnel. Vous pouvez ensuite utiliser le langage et les fonctions intégrées [!INCLUDE[tsql](../../includes/tsql-md.md)] standard pour préparer les rapports.  
  
```sql  
SELECT Tab.Id, SalesOrderJsonData.Customer, SalesOrderJsonData.Date  
FROM   SalesOrderRecord AS Tab  
          CROSS APPLY  
     OPENJSON (Tab.json, N'$.Orders.OrdersArray')  
           WITH (  
              Number   varchar(200) N'$.Order.Number',   
              Date     datetime     N'$.Order.Date',  
              Customer varchar(200) N'$.AccountNumber',   
              Quantity int          N'$.Item.Quantity'  
           )  
  AS SalesOrderJsonData  
WHERE JSON_VALUE(Tab.json, '$.Status') = N'Closed'  
ORDER BY JSON_VALUE(Tab.json, '$.Group'), Tab.DateModified  
```  
  
Vous pouvez utiliser des colonnes de table standard et des valeurs de texte JSON dans une même requête. Vous pouvez ajouter des index dans l’expression `JSON_VALUE(Tab.json, '$.Status')` pour améliorer les performances de la requête. Pour plus d’informations, consultez [Indexer des données JSON](../../relational-databases/json/index-json-data.md).
 
## <a name="return-data-from-a-sql-server-table-formatted-as-json"></a>Retourner les données d’une table SQL Server au format JSON  
Si vous avez un service web qui tire des données de la couche Base de données et les retourne au format JSON, ou que vous disposez de frameworks ou de bibliothèques JavaScript qui acceptent des données au format JSON, vous pouvez mettre en forme la sortie JSON directement dans une requête SQL. Au lieu d’écrire du code ou d’inclure une bibliothèque pour convertir des résultats de requêtes tabulaires et sérialiser ensuite des objets au format JSON, vous pouvez utiliser **FOR JSON** pour déléguer la mise en forme des données JSON à SQL Server.  
  
Par exemple, vous pouvez générer une sortie JSON conforme à la spécification OData. Le service web attend une demande et une réponse dans le format suivant : 
  
-   Demande : `/Northwind/Northwind.svc/Products(1)?$select=ProductID,ProductName`  
  
-   Réponse : `{"@odata.context":"http://services.odata.org/V4/Northwind/Northwind.svc/$metadata#Products(ProductID,ProductName)/$entity","ProductID":1,"ProductName":"Chai"}`  
  
Cette URL OData représente une demande pour les colonnes ProductID et ProductName pour le produit avec comme `id` la valeur 1. Vous pouvez utiliser **FOR JSON** pour mettre en forme la sortie comme prévu dans SQL Server.  
  
```sql  
SELECT 'http://services.odata.org/V4/Northwind/Northwind.svc/$metadata#Products(ProductID,ProductName)/$entity'
 AS '@odata.context',   
 ProductID, Name as ProductName   
FROM Production.Product  
WHERE ProductID = 1  
FOR JSON AUTO  
```  
  
La sortie de cette requête est un texte JSON entièrement conforme à la spécification OData. La mise en forme et l’échappement sont gérés par SQL Server. SQL Server peut également mettre en forme les résultats de requêtes dans n’importe quel format, notamment OData JSON ou GeoJSON. Pour plus d’informations, consultez [Returning spatial data in GeoJSON format](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/returning-spatial-data-in-geojson-format-part-1) (Retourner des données spatiales au format GeoJSON).  
  
## <a name="test-drive-built-in-json-support-with-the-adventureworks-sample-database"></a>Tester la prise en charge de JSON à partir de l’exemple de base de données AdventureWorks
Pour obtenir l’exemple de base de données AdventureWorks, téléchargez au minimum le fichier de base de données et le fichier d’exemples et de scripts à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=49502). 
 
Après avoir restauré l’exemple de base de données dans une instance de SQL Server 2016, extrayez le fichier d’exemples, puis ouvrez le fichier *JSON Sample Queries procedures views and indexes.sql* à partir du dossier JSON. Exécutez les scripts de ce fichier pour remettre certaines données existantes au format JSON, testez des exemples de rapports et de requêtes sur les données JSON, indexez les données JSON, puis importez et exportez les données JSON.  
  
Voici ce que vous pouvez faire avec les scripts inclus dans le fichier :  
  
* Dénormaliser le schéma existant pour créer des colonnes de données JSON.
  
    * Stockez les informations de SalesReasons, SalesOrderDetails, SalesPerson, Customer et des autres tables contenant des informations relatives aux commandes dans les colonnes JSON de la table SalesOrder_json.  
  
    * Stockez les informations des tables EmailAddresses/PersonPhone dans la table Person_json en tant que tableaux d’objets JSON.  
  
* Créer des procédures et des vues qui interrogent les données JSON.  
  
* Indexer des données JSON. Créez des index sur les propriétés JSON et des index de recherche en texte intégral.  
  
* Importer et exporter les données JSON. Créez et exécutez des procédures qui exportent le contenu des tables Person et SalesOrder sous forme de résultats JSON, puis importez et mettez à jour les tables Person et SalesOrder à l’aide de l’entrée JSON.  
  
* Exécuter des exemples de requêtes. Exécutez des requêtes qui appellent les procédures stockées et les vues que vous avez créées aux étapes 2 et 4.  
  
* Nettoyer les scripts. N’exécutez pas cette partie si vous voulez conserver les procédures stockées et les vues que vous avez créées aux étapes 2 et 4.  
  
## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>En savoir plus sur JSON dans SQL Server et Azure SQL Database  
  
### <a name="microsoft-blog-posts"></a>Billets de blog Microsoft  
  
Pour accéder à un grand nombre de solutions spécifiques, de cas d’usage et de recommandations, consultez ces [billets de blog](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) sur la prise en charge intégrée de JSON dans SQL Server et Azure SQL Database.  

### <a name="microsoft-videos"></a>Vidéos Microsoft

Pour une présentation visuelle de la prise en charge intégrée de JSON dans SQL Server et Azure SQL Database, consultez la vidéo suivante :

*Utilisation de JSON dans SQL Server 2016 et Azure SQL Database*
> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database/player]

*Building REST API with SQL Server using JSON functions*
> [!VIDEO https://www.youtube.com/embed/0m6GXF3-5WI]

### <a name="reference-articles"></a>Articles de référence  
  
-   [Clause FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md) (FOR JSON)  
-   [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md)  
-   [JSON Functions (Transact-SQL)](../../t-sql/functions/json-functions-transact-sql.md)  
    -   [ISJSON (Transact-SQL)](../../t-sql/functions/isjson-transact-sql.md)  
    -   [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md)  
    -   [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md)  
    -   [JSON_MODIFY (Transact-SQL)](../../t-sql/functions/json-modify-transact-sql.md)  
