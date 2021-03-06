---
title: CONCAT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONCAT
- CONCAT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT function
ms.assetid: fce5a8d4-283b-4c47-95e5-4946402550d5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 1f3a1ef2b55b2f67b6b2e01ceb1965a5076e8476
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="concat-transact-sql"></a>CONCAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Retourne une chaîne qui est le résultat de la concaténation de plusieurs valeurs de chaîne. (Pour ajouter une valeur de séparation durant la concaténation, consultez [CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md).)
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CONCAT ( string_value1, string_value2 [, string_valueN ] )  
```  
  
## <a name="arguments"></a>Arguments  
*string_value*  
Valeur de chaîne à concaténer aux autres valeurs.
  
## <a name="return-types"></a>Types de retour
Chaîne, dont la longueur et le type dépendent de l'entrée.
  
## <a name="remarks"></a>Notes   
**CONCAT** accepte un nombre variable d’arguments de chaîne et les concatène en une chaîne unique. Elle nécessite un minimum de deux valeurs d'entrée ; sinon, une erreur est générée. Tous les arguments sont implicitement convertis en types chaîne et ensuite concaténés. Les valeurs NULL sont implicitement converties en chaîne vide. Si tous les arguments sont NULL, une chaîne vide de type **varchar**(1) est renvoyée. La conversion implicite en chaînes respecte les règles existantes de conversion de type de données. Pour plus d’informations sur les conversions de type de données, consultez [CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
Le type de retour dépend du type des arguments. Le tableau ci-dessous illustre le mappage.
  
|Type d'entrée|Type de sortie et longueur|  
|---|---|
|Si un argument est un type système SQL-CLR, un type défini par l'utilisateur SQL-CLR ou `nvarchar(max)`|**nvarchar(max)**|  
|Sinon, si un argument est de type **varbinary(max)** ou **varchar(max)**|**varchar(max)** à moins qu’un des paramètres soit de type **nvarchar** d’une longueur quelconque. Dans ce cas, le résultat est de type **nvarchar(max)**.|  
|Sinon, si un argument est de type **nvarchar**(<= 4000)|**nvarchar**(<= 4000)|  
|Sinon, dans tous les autres cas|**varchar**(<= 8000) à moins qu’un des paramètres soit de type nvarchar d’une longueur quelconque. Dans ce cas, le résultat est de type **nvarchar(max)**.|  
  
Lorsque les arguments sont <= 4000 pour **nvarchar** ou <= 8000 pour **varchar**, les conversions implicites peuvent affecter la longueur du résultat. D'autres types de données ont différentes longueurs lorsqu'ils sont implicitement convertis en chaînes. Par exemple, une valeur **int** (14) a une longueur de chaîne de 12, alors qu’une valeur **float** a une longueur de 32. Par conséquent, le résultat de la concaténation de deux entiers a une longueur non inférieure à 24.
  
Si aucun des arguments d'entrée n'est d'un type d'objet (LOB) pris en charge, le type de retour est tronqué à une longueur de 8000, quel que soit le type de retour. Cette troncation préserve l'espace et prend en charge l'efficacité de la génération du plan.
  
La fonction CONCAT peut être exécutée à distance sur un serveur lié de version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ou ultérieure. Pour les serveurs liés plus anciens, l’opération CONCAT est exécutée localement après le renvoi des valeurs non concaténées à partir du serveur lié.
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-concat"></a>A. Utilisation de CONCAT  
  
```sql
SELECT CONCAT ( 'Happy ', 'Birthday ', 11, '/', '25' ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------  
Happy Birthday 11/25  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-concat-with-null-values"></a>B. Utilisation de CONCAT avec des valeurs NULL  
  
```sql
CREATE TABLE #temp (  
    emp_name nvarchar(200) NOT NULL,  
    emp_middlename nvarchar(200) NULL,  
    emp_lastname nvarchar(200) NOT NULL  
);  
INSERT INTO #temp VALUES( 'Name', NULL, 'Lastname' );  
SELECT CONCAT( emp_name, emp_middlename, emp_lastname ) AS Result  
FROM #temp;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
------------------  
NameLastname  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)   
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  


