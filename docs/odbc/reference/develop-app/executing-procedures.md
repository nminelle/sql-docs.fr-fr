---
title: "L’exécution de procédures | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], procedures
- procedures [ODBC], executing
ms.assetid: a75e497a-4661-438a-a10e-f598c65f81be
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5faf7f71d56ea6a1f6a8d4de436937dd96c03cec
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="executing-procedures"></a>L’exécution de procédures
ODBC définit une séquence d’échappement standard pour l’exécution de procédures. Pour connaître la syntaxe de cette séquence et un exemple de code qui l’utilise, consultez [les appels de procédure](../../../odbc/reference/develop-app/procedure-calls.md).  
  
 Pour exécuter une procédure, une application effectue les actions suivantes :  
  
1.  Définit les valeurs des paramètres. Pour plus d’informations, consultez [paramètres de l’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.  
  
2.  Appels **SQLExecDirect** et lui passe une chaîne contenant l’instruction SQL qui exécute la procédure. Cette instruction peut utiliser la séquence d’échappement définie par la syntaxe ODBC ou propres au SGBD ; instructions qui utilisent la syntaxe spécifique au SGBD ne sont pas interopérables.  
  
3.  Lorsque **SQLExecDirect** est appelée, le pilote :  
  
    -   Récupère les valeurs de paramètre en cours et les convertit si nécessaire. Pour plus d’informations, consultez [paramètres de l’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.  
  
    -   Appelle la procédure dans la source de données et l’envoie les valeurs de paramètre converti. Comment le pilote appelle la procédure est spécifique au pilote. Par exemple, il peut modifier l’instruction SQL pour utiliser la grammaire SQL de la source de données et d’envoyer cette instruction pour l’exécution, ou il peut appeler la procédure directement à l’aide d’un mécanisme d’appel de procédure distante (RPC) qui est défini dans le protocole de flux de données du SGBD.  
  
    -   Retourne les valeurs de toutes les entrées/sorties ou paramètres de sortie ou la valeur de retour de procédure, en supposant que la procédure réussit. Ces valeurs ne soient pas disponibles tant qu’après le traitement de tous les autres résultats (nombre de lignes et de jeux de résultats) générés par la procédure. Si la procédure échoue, le pilote retourne toutes les erreurs.
