---
title: Fonction SQLWriteFileDSN | Documents Microsoft
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
apiname: SQLWriteFileDSN
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLWriteFileDSN
helpviewer_keywords: SQLWriteFileDSN [ODBC]
ms.assetid: 9e18f56f-1061-416b-83d4-ffeec42ab5a9
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 973c27fb58411e0fd3ddc482a0a8cbee3d929ee8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlwritefiledsn-function"></a>Fonction SQLWriteFileDSN
**Mise en conformité**  
 Version introduite : ODBC 3.0  
  
 **Résumé**  
 **SQLWriteFileDSN** écrit les informations dans un fichier DSN.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL SQLWriteFileDSN(  
     LPCSTR     lpszFileName,  
     LPCSTR     lpszAppName,  
     LPCSTR     lpszKeyName,  
     LPCSTR     lpszString);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszFileName*  
 [Entrée] Pointeur vers le nom de la source de données de fichier. Une extension de source de données est ajoutée à tous les noms de fichiers qui n’ont pas déjà d’une extension de source de données.  
  
 *lpszAppName*  
 [Entrée] Pointeur vers le nom de l’application. C’est la section ODBC « ODBC ».  
  
 *lpszKeyName*  
 [Entrée] Pointeur vers le nom de la clé à lire. Consultez « Commentaires » pour les mots clés réservés.  
  
 *lpszString*  
 [Sortie] Pointe vers la chaîne associée à la clé à écrire. La longueur maximale de la chaîne pointée par cet argument est de 32 767 octets.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne TRUE si l’opération a réussi, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLWriteFileDSN** renvoie la valeur FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournées par **SQLInstallerError** et explique chacune d’elles dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générales|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_PATH|Le chemin d’installation non valide|Le chemin d’accès du nom de fichier spécifié dans le *lpszFileName* argument n’était pas valide.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type de demande non valide|Le *lpszAppName*, *lpszKeyName*, ou *lpszString* argument était NULL.|  
  
## <a name="comments"></a>Commentaires  
 ODBC réserve le nom de la section [ODBC] dans lequel stocker les informations de connexion. Les mots clés réservés pour cette section sont les mêmes que celles réservées pour une chaîne de connexion dans **SQLDriverConnect**. (Pour plus d’informations, consultez la [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) description de fonction.)  
  
 Applications peuvent utiliser ces mots clés réservés d’écrire directement dans un fichier DSN. Si une application veut créer ou modifier la chaîne de connexion sans DSN associée à un fichier DSN, elle peut appeler **SQLWriteFileDSN** pour un des mots clés de chaîne de connexion réservé dans la section [ODBC].  
  
 Si le *lpszString* argument est un pointeur null, le mot clé vers laquelle pointé le *lpszKeyName* argument sera supprimé à partir du fichier .dsn. Si le *lpszString* et *lpszKeyName* arguments sont les deux pointeurs null, la section vers laquelle pointée le *lpszAppName* argument sera supprimé à partir du fichier .dsn.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|La lecture des informations à partir de sources de données fichier|[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|
