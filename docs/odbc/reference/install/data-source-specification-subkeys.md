---
title: "Les sous-clés de spécification de Source de données | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data source specification subkeys [ODBC]
- registry entries for data sources [ODBC], data source specification subkeys
- subkeys [ODBC], data source specification subkeys
ms.assetid: d7e88a07-e6ab-4258-a45d-1ca21234fbec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61b485f55be504e894754f74c4ab779b9ebbaf5a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="data-source-specification-subkeys"></a>Sous-clés de spécification de Source de données
Chaque source de données répertorié dans la sous-clé de Sources de données ODBC a une sous-clé qui lui sont propres. Cette sous-clé a le même nom que la valeur correspondante sous la sous-clé de Sources de données ODBC. Les valeurs sous cette sous-clé doivent répertorier la DLL du pilote et peuvent contenir une description de la source de données. Si le pilote prend en charge des convertisseurs, les valeurs peuvent répertorier le nom d’un convertisseur de valeur par défaut, la DLL de traduction par défaut et l’option de traduction par défaut. Les valeurs peuvent également répertorier les autres informations requises par le pilote pour se connecter à la source de données. Par exemple, le pilote peut nécessiter un nom du serveur, le nom de la base de données ou le nom de schéma.  
  
 Les formats des valeurs sont comme indiqué dans le tableau suivant. Seule la valeur du pilote est requise.  
  
|Nom|Type de données|data|  
|----------|---------------|----------|  
| Description|REG_SZ|*Description*|  
|Pilote|REG_SZ|*chemin de DLL de pilote*|  
|TranslationDLL|REG_SZ|*chemin de DLL de traduction*|  
|TranslationName|REG_SZ|*nom de la traduction*|  
|TranslationOption|REG_SZ|*option de traduction*|  
|*nom de valeur s’abonner*|*type de valeur s’abonner*|*données de valeur opt*|  
  
 Par exemple, supposons que le pilote SQL Server requiert le nom du serveur et un indicateur pour l’OEM pour la conversion ANSI et définit les valeurs de serveur et OEMTOANSI dans ce cas. Supposons également que la source de données d’inventaire utilise le convertisseur de Page de Code Microsoft® pour convertir entre les pages de codes multilingue (850) Windows® Latin 1 (1250). Les valeurs sous la sous-clé de stock peuvent être comme suit :  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```