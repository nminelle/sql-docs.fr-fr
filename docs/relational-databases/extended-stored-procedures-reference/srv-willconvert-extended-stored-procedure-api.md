---
title: "srv_willconvert (API de procédure stockée étendue) | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- srv_willconvert
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_willconvert
ms.assetid: 6f4db5fd-215a-461c-95e4-17697852733e
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e4a39602f8e7e75dabacbac405758aee6879b0b2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="srvwillconvert-extended-stored-procedure-api"></a>srv_willconvert (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez plutôt l'intégration du CLR.  
  
 Détermine si une conversion de type de données spécifique est disponible au sein de la bibliothèque ODS.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL srv_willconvert (  
int  
srctype  
,  
int  
desttype   
);  
```  
  
## <a name="arguments"></a>Arguments  
 *srctype*  
 Indique le type de données des données à convertir. Ce paramètre peut être n'importe lequel des types de données des API de procédure stockée étendue.  
  
 *desttype*  
 Indique le type de données vers lequel les données sources sont converties. Ce paramètre peut être n'importe lequel des types de données des API de procédure stockée étendue.  
  
## <a name="returns"></a>Valeur renvoyée  
 TRUE si la conversion de type de données est prise en charge ; FALSE, dans le cas contraire.  
  
## <a name="remarks"></a>Notes   
 Pour obtenir une description de chaque type de données, consultez [Types de données &#40;API de procédure stockée étendue&#41;](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md).  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a> Voir aussi  
 [srv_convert &#40;API de procédure stockée étendue&#41;](../../relational-databases/extended-stored-procedures-reference/srv-convert-extended-stored-procedure-api.md)  
  
  
