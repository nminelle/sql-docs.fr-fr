﻿---
title: "Étape 3 : Preuve de concept pour la connexion à SQL à l’aide de Node.js | Documents Microsoft"
ms.custom: 
ms.date: 08/08/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: node-js
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d5b41b6-129a-40b1-af8b-7e8fbd4a84bb
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 664c786e36fc9938fca34f71cffb9b50d3c2e1c5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT

ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-nodejs"></a>Étape 3 : Preuve de concept pour la connexion à SQL à l’aide de Node.js

![Téléchargement-bas encerclé](../../ssdt/media/download.png)[pour télécharger le pilote SQL Node.js](../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Cet exemple doit être considéré comme une preuve de concept uniquement.  L’exemple de code est simplifié par souci de clarté et ne représente pas nécessairement les meilleures pratiques recommandées par Microsoft. D'autres exemples qui utilisent les mêmes fonctions essentielles sont disponibles sur Github :

- [https://github.com/tediousjs/tedious/BLOB/Master/Examples/](https://github.com/tediousjs/tedious/blob/master/examples/)
  
## <a name="step-1-connect"></a>Étape 1 : se connecter  
  
La fonction **new Connection** est utilisée pour se connecter à SQL Database.   
  
```javascript  
    var Connection = require('tedious').Connection;  
    var config = {  
        userName: 'yourusername',  
        password: 'yourpassword',  
        server: 'yourserver.database.windows.net',  
        // If you are on Microsoft Azure, you need this:  
        options: {encrypt: true, database: 'AdventureWorks'}  
    };  
    var connection = new Connection(config);  
    connection.on('connect', function(err) {  
    // If no error, then good to proceed.  
        console.log("Connected");  
    });  
```  
  
## <a name="step-2--execute-a-query"></a>Étape 2 : Exécuter une requête  
  
  
Toutes les instructions SQL sont exécutées à l’aide de la function **new Request()**. Si l’instruction retourne des lignes, par exemple une instruction select, vous pouvez les récupérer à l’aide de la fonction **request.on()**. S’il n’y a aucune ligne retourné la fonction request.on() retourne des listes vides.   
  
  
```javascript  
    var Connection = require('tedious').Connection;  
    var config = {  
        userName: 'yourusername',  
        password: 'yourpassword',  
        server: 'yourserver.database.windows.net',  
        // When you connect to Azure SQL Database, you need these next options.  
        options: {encrypt: true, database: 'AdventureWorks'}  
    };  
    var connection = new Connection(config);  
    connection.on('connect', function(err) {  
        // If no error, then good to proceed.  
        console.log("Connected");  
        executeStatement();  
    });  
  
    var Request = require('tedious').Request;  
    var TYPES = require('tedious').TYPES;  
  
    function executeStatement() {  
        request = new Request("SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC;", function(err) {  
        if (err) {  
            console.log(err);}  
        });  
        var result = "";  
        request.on('row', function(columns) {  
            columns.forEach(function(column) {  
              if (column.value === null) {  
                console.log('NULL');  
              } else {  
                result+= column.value + " ";  
              }  
            });  
            console.log(result);  
            result ="";  
        });  
  
        request.on('done', function(rowCount, more) {  
        console.log(rowCount + ' rows returned');  
        });  
        connection.execSql(request);  
    }  
```  
  
## <a name="step-3-insert-a-row"></a>Étape 3 : Insérer une ligne  
  
Dans cet exemple, vous allez apprendre à passer en toute sécurité une commande [INSERT](../../t-sql/statements/insert-transact-sql.md), en passant des valeurs en paramètres qui protègeront votre application à partir des tentatives [d'injection SQL](../../relational-databases/tables/primary-and-foreign-key-constraints.md).    
  
  
```javascript  
    var Connection = require('tedious').Connection;  
    var config = {  
        userName: 'yourusername',  
        password: 'yourpassword',  
        server: 'yourserver.database.windows.net',  
        // If you are on Azure SQL Database, you need these next options.  
        options: {encrypt: true, database: 'AdventureWorks'}  
    };  
    var connection = new Connection(config);  
    connection.on('connect', function(err) {  
        // If no error, then good to proceed.  
        console.log("Connected");  
        executeStatement1();  
    });  
  
    var Request = require('tedious').Request  
    var TYPES = require('tedious').TYPES;  
  
    function executeStatement1() {  
        request = new Request("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES (@Name, @Number, @Cost, @Price, CURRENT_TIMESTAMP);", function(err) {  
         if (err) {  
            console.log(err);}  
        });  
        request.addParameter('Name', TYPES.NVarChar,'SQL Server Express 2014');  
        request.addParameter('Number', TYPES.NVarChar , 'SQLEXPRESS2014');  
        request.addParameter('Cost', TYPES.Int, 11);  
        request.addParameter('Price', TYPES.Int,11);  
        request.on('row', function(columns) {  
            columns.forEach(function(column) {  
              if (column.value === null) {  
                console.log('NULL');  
              } else {  
                console.log("Product id of inserted item is " + column.value);  
              }  
            });  
        });       
        connection.execSql(request);  
    }  
```  

