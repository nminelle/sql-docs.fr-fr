---
title: "Activer une base de données pour la réplication (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6f729536b8f538c4b19ea76b7454b2899e2ffdfc
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>Activer une base de données pour la réplication (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Une base de données est activée implicitement pour la réplication lorsqu'un membre du rôle serveur fixe **sysadmin** crée une publication à l'aide de l'Assistant Nouvelle publication. Un membre du rôle serveur fixe **sysadmin** peut également activer une base de données de manière explicite, afin qu'un membre du rôle de base de données fixe **db_owner** puisse créer une ou plusieurs publications dans la base de données. Pour activer une base de données de manière explicite, utilisez la page **Bases de données de publication** de la boîte de dialogue **Propriétés du serveur de publication - \<Serveur_de_publication>**. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
### <a name="to-enable-a-database-for-replication"></a>Pour activer une base de données pour la réplication  
  
1.  Dans la page **Bases de données de publication** de la boîte de dialogue **Propriétés du serveur de publication - \<Serveur_de_publication>**, cochez la case **Transactionnelle** et/ou **Fusionner** pour chaque base de données à répliquer. Sélectionnez **Transactionnel** pour activer la base de données pour la réplication d'instantané.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
