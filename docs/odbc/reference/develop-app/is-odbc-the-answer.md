---
title: "La réponse est ODBC ? | Microsoft Docs"
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
helpviewer_keywords: interoperability [ODBC], ODBC
ms.assetid: bfa5e6ee-5979-42a9-be6f-a84d1ee7a54c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 390188eb430e51bf0ce27bf2f32f9f82c195d4da
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="is-odbc-the-answer"></a>La réponse est ODBC ?
Avant d’aborder la question de l’interopérabilité, envisagez la question suivante : l’application doit-elle utiliser ODBC du tout ? Cela peut sembler étrange question à poser dans un guide pour ODBC, mais il est en fait, un message légitime. ODBC n’est pas conçu pour remplacer complètement les API de bases de données natif, ni si elle a été conçue pour fournir un accès de base de données dans toutes les circonstances. Il a été conçu pour fournir une interface commune pour les bases de données et a été conçu pour libérer les programmeurs d’applications d’avoir à en savoir plus sur et mettre à jour des liens vers plusieurs bases de données.  
  
 Applications personnalisées sont des candidats idéaux pour l’API de bases de données natif. La principale raison est que les applications personnalisées souvent travailler avec un SGBD unique et n’ont pas besoin pour fonctionner. Base de données native API peut préférables à ODBC d’exposer les fonctionnalités d’un SGBD particulier et peut exposer des fonctionnalités non exposées par ODBC. En outre, étant donné que les développeurs d’applications personnalisées sont généralement familiarisés avec la base de données native API pour leurs SGBD, il est recommandé pour en savoir plus ODBC. Toutefois, il est intéressant de noter que pour certains SGBD, ODBC est l’API de base de données native.  
  
 Par conséquent, les applications qui sont des candidats pour ODBC ? Les meilleures candidates sont des applications qui fonctionnent avec plusieurs SGBD. Cela inclut pratiquement toutes les applications génériques et verticales. Il inclut également un nombre d’applications personnalisées. Par exemple, les applications personnalisées qui utilisent plusieurs SGBD différents sont beaucoup plus facile et plus clair d’écrire avec ODBC à avec plusieurs API natives. Et les applications personnalisées écrites avec ODBC sont beaucoup plus faciles de migrer une société déplace d’un SGBD à l’autre ou déploie la même application sur différents SGBD.
