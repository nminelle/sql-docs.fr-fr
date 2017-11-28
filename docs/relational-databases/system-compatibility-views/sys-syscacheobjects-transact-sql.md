---
title: Sys.syscacheobjects (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.syscacheobjects_TSQL
- sys.syscacheobjects
- syscacheobjects
- syscacheobjects_TSQL
dev_langs: TSQL
helpviewer_keywords:
- syscacheobjects system table
- sys.syscacheobjects compatibility view
ms.assetid: 9b14f37c-b7f5-4f71-b070-cce89a83f69e
caps.latest.revision: "37"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9925669bec972d543b6dc688d19a5dab25db032c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syssyscacheobjects-transact-sql"></a>sys.syscacheobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des informations sur l'utilisation du cache.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**ID du paquet**|**int**|ID du compartiment. La valeur est comprise entre 0 et (taille du répertoire -1). La taille du répertoire est la taille de la table de hachage.|  
|**cacheobjtype**|**nvarchar(17)**|Type de l'objet dans le cache :<br /><br /> Plan compilé<br /><br /> Plan exécutable<br /><br /> Arborescence d'analyse<br /><br /> Curseur<br /><br /> Procédure stockée étendue|  
|**type de l’objet**|**nvarchar (8)**|Type d’objet :<br /><br /> Procédure stockée<br /><br /> Instruction préparée<br /><br /> Requête ad hoc ([!INCLUDE[tsql](../../includes/tsql-md.md)] soumis en tant qu’événements de langage à partir de la **sqlcmd** ou **osql** utilitaires, au lieu d’appels de procédure distante)<br /><br /> ReplProc (procédure de réplication)<br /><br /> Déclencheur<br /><br /> Affichage<br /><br /> Valeur par défaut<br /><br /> Table utilisateur<br /><br /> Table système<br /><br /> Vérifier<br /><br /> Règle|  
|**ID d’objet**|**int**|Une des clés principales servant à rechercher un objet dans le cache. Il s’agit d’ID d’objet stocké dans **sysobjects** pour les objets de base de données (procédures, vues, déclencheurs, etc.). Pour les objets du cache, tel que SQL ad hoc ou préparée, **objid** est une valeur générée en interne.|  
|**dbid**|**smallint**|ID de la base de données dans laquelle a été compilé l'objet contenu dans le cache|  
|**dbidexec**|**smallint**|ID de la base de données à partir de laquelle la requête est exécutée.<br /><br /> Pour la plupart des objets, **dbidexec** a la même valeur que **dbid**.<br /><br /> Pour les vues système, **dbidexec** est l’ID de base de données à partir de laquelle la requête est exécutée.<br /><br /> Pour les requêtes ad hoc, **dbidexec** est 0. Cela signifie que **dbidexec** a la même valeur que **dbid**.|  
|**UID**|**smallint**|Indique le créateur du plan pour les plans de requête ad hoc et les plans préparés.<br /><br /> –2 = le traitement soumis ne dépend pas de la résolution implicite des noms et peut être partagé entre différents utilisateurs. Cette méthode est recommandée. Toute autre valeur représente l'ID de l'utilisateur soumettant la requête dans la base de données.<br /><br /> Déborde ou retourne la valeur NULL si le nombre d'utilisateurs et de rôles dépasse 32 767.|  
|**refCounts**|**int**|Nombre d'autres objets dans le cache faisant référence à cet objet. Un nombre de 1 est la base.|  
|**usecounts**|**int**|Nombre d'utilisations de l'objet dans le cache depuis le début|  
|**pagesused**|**int**|Nombre de pages consommées par l'objet dans le cache.|  
|**setopts**|**int**|Valeurs de l'option SET qui affectent un plan compilé. Elles font partie de la clé du cache. Des modifications de cette colonne indiquent que des utilisateurs ont modifié les options SET. Il s'agit des options suivantes :<br /><br /> **ANSI_PADDING**<br /><br /> **FORCEPLAN**<br /><br /> **CONCAT_NULL_YIELDS_NULL**<br /><br /> **ANSI_WARNINGS**<br /><br /> **ANSI_NULLS**<br /><br /> **QUOTED_IDENTIFIER**<br /><br /> **ANSI_NULL_DFLT_ON**<br /><br /> **ANSI_NULL_DFLT_OFF**|  
|**ID de langue**|**smallint**|ID de langue. ID de la langue de la connexion qui a créé l'objet dans le cache.|  
|**DateFormat**|**smallint**|Format de date de la connexion qui a créé l'objet dans le cache|  
|**status**|**int**|Indique si l'objet dans le cache est un plan de curseur ou non. Seul le bit de poids faible est actuellement utilisé.|  
|**LastTime**|**bigint**|Pour compatibilité descendante uniquement. Retourne toujours 0.|  
|**maxexectime**|**bigint**|Pour compatibilité descendante uniquement. Retourne toujours 0.|  
|**avgexectime**|**bigint**|Pour compatibilité descendante uniquement. Retourne toujours 0.|  
|**lastreads**|**bigint**|Pour compatibilité descendante uniquement. Retourne toujours 0.|  
|**lastwrites**|**bigint**|Pour compatibilité descendante uniquement. Retourne toujours 0.|  
|**SqlBytes**|**int**|Longueur en octets de la définition de procédure ou du traitement soumis.|  
|**SQL**|**nvarchar(3900)**|Définition du module ou les 3 900 premiers caractères du traitement soumis.|  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
