---
title: REPLACENULL (expression SSIS) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70db7832-b5a0-4db5-a8ad-42ad8630d8e8
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f8ce8999c06fae17636000d7931dd2267687b8cb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="replacenull-ssis-expression"></a>REPLACENULL (expression SSIS)
  Retourne la valeur du paramètre de la seconde expression si la valeur du paramètre de la première expression est NULL ; sinon, retourne la valeur de la première expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
REPLACENULL(expression 1,expression 2)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression 1*  
 Le résultat de cette expression est comparé à NULL.  
  
 *expression 2*  
 Le résultat de cette expression est retourné si la première expression renvoie la valeur NULL.  
  
## <a name="result-types"></a>Types des résultats  
 DT_WSTR  
  
## <a name="remarks"></a>Notes   
  
-   La longueur de l'argument *expression 2* peut être égale à zéro.  
  
-   La fonction REPLACENULL renvoie un résultat NULL si un argument est NULL.  
  
-   Les colonnes BLOB (DT_TEXT, DT_NTEXT, DT_IMAGE) ne sont pas prises en charge pour l'un ou l'autre paramètre.  
  
-   Il est prévu que les deux expressions aient le même type de retour. Dans le cas contraire, la fonction tente d'effectuer un cast de la seconde expression en type de retour de la première expression, ce qui peut se traduire par une erreur si les types de données sont incompatibles.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant remplace toute valeur NULL dans une colonne de base de données par une chaîne (1900-01-01). Cette fonction est particulièrement utilisée dans les modèles de colonne dérivée courants où vous souhaitez remplacer les valeurs NULL par autre chose.  
  
```  
REPLACENULL(MyColumn, "1900-01-01")  
```  
  
> [!NOTE]  
>  Vous trouverez ci-après un exemple d’utilisation dans [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]/[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)].  
  
```  
(DT_DBTIMESTAMP) (ISNULL(MyColumn) ? “1900-01-01” : MyColumn)   
```  
  
  
