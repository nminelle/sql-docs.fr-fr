---
title: Applet de commande Add-RoleMember | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 827c8bbc-d48f-4e49-9ea5-abb1380f7623
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f9aabb7cd07ad5864373e566766c7980dd00f9b0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="add-rolemember-cmdlet"></a>Applet de commande Add-RoleMember
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Ajoutez un membre au rôle spécifié d'une base de données multidimensionnelle ou tabulaire Analysis Services.  

>[!NOTE] 
>Cet article peut contenir des exemples et des informations obsolètes. Utilisez l’applet de commande Get-Help pour la dernière version.
  
## <a name="syntax"></a>Syntaxe  
 `Add-RoleMember [-MemberName] <System.String> [-Database] <System.String> [-RoleName] <System.String> [<CommonParameters>]`  
  
 `Add-RoleMember [-MemberName] <System.String> [-DatabaseRole] <Microsoft.AnalysisServices.Role> [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 L'applet de commande Add-RoleMember ajoute un membre valide à un rôle de base de données existant. Seuls les rôles de base de données sont autorisés. Vous ne pouvez pas utiliser cet applet de commande pour ajouter des membres à un rôle serveur.  
  
 Vous pouvez uniquement ajouter un membre à la fois, qui peut être un compte d'utilisateur ou de groupe.  
  
## <a name="parameters"></a>Paramètres  
  
### <a name="-membername-string"></a>-MemberName \<chaîne >  
 Spécifie l'utilisateur ou le groupe Windows à ajouter au rôle.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-database-string"></a>-De base de données \<chaîne >  
 Spécifie la base de données à laquelle le rôle appartient.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?| 1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-rolename-string"></a>-RoleName \<chaîne >  
 Spécifie le rôle auquel vous ajoutez des membres.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|2|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-databaserole-string"></a>-DatabaseRole \<chaîne >  
 Spécifie l'objet Microsoft.AnalysisServices.Role auquel le membre doit être ajouté. Utilisez ce paramètre comme une alternative aux paramètres –Database et –RoleName, lorsque vous souhaitez fournir le rôle de base de données via le pipeline.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true (ByPropertyName)|  
|Accepter les caractères génériques ?|false|  
  
### <a name="commonparameters"></a>\<Paramètres_courants >  
 La commande cmdlet prend en charge les paramètres communs : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable. Pour plus d’informations, consultez [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun.|  
|Sorties|None|  
  
## <a name="example-1"></a>Exemple 1  
  
```  
PS SQLSERVER:\sqlas\localhost\default> add-rolemember –membername “adventure-works\bobh” –database “AdventureWorks” –rolename “Reader”  
```  
  
 Cette commande ajoute un compte d'utilisateur de domaine Windows au rôle Lecteur pour la base de données AdventureWorks exécutée sur une instance par défaut locale.  
  
## <a name="example-2"></a>Exemple 2  
  
```  
PS SQLSERVER:\sqlas\localhost\default> $roles= dir .\databases\AWTEST\Roles  
PS SQLSERVER:\sqlas\localhost\default> $roles  
PS SQLSERVER:\sqlas\localhost\default> add-rolemember –membername:“adventure-works\bobh” –databaserole:$roles[0]  
```  
  
 La ligne 1 ajoute tous les rôles de la base de données AWTEST au pipeline. La ligne 2, où vous tapez $roles à l'invite, affiche le tableau de rôles. La ligne 3 ajoute l'utilisateur Windows adventure-works\bobh en tant que membre du premier rôle dans le tableau.  
  
## <a name="example-3"></a>Exemple 3  
  
```  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles=dir  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles[0] | Add-rolemember –membername “adventure-works\bobh”  
```  
  
 Cette commande ajoute un compte d'utilisateur de domaine Windows au premier rôle dans un tableau, où le tableau est créé en répertoriant les enfants du dossier Rôles, dans le contexte d'une base de données spécifique (AWTEST).  
  

  
  
