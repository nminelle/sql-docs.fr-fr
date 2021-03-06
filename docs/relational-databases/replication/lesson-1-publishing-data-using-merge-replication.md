---
title: "Leçon 1 : Publication de données à l’aide de la réplication de fusion | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
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
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: c3c6e0b6-54cd-4b7d-8efb-2cefe14fcd7f
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8d2ca2d6dc4c638b38ca353612cef1bda70e457
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="lesson-1-publishing-data-using-merge-replication"></a>Leçon 1 : publication de données à l'aide de la réplication de fusion
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Dans cette leçon, vous créez une publication de fusion à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour publier un sous-ensemble des tables **Employee**, **SalesOrderHeader**et **SalesOrderDetail** de l’exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Ces tables sont filtrées avec des filtres de lignes paramétrables pour que chaque abonnement contienne une partition unique des données. Vous ajoutez également la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée par l’Agent de fusion à la liste d’accès à la publication. Pour suivre ce didacticiel, vous devez avoir terminé le didacticiel précédent, [Préparation du serveur pour la réplication](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
### <a name="to-create-a-publication-and-define-articles"></a>Pour créer une publication et définir des articles  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , cliquez avec le bouton droit sur le dossier **Publications locales**, puis cliquez sur **Nouvelle publication**.  
  
    L'Assistant Configuration de la publication démarre.  
  
3.  Dans la page Base de données de publication, sélectionnez [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], puis cliquez sur **Suivant**.  
  
4.  Dans la page Type de publication, sélectionnez **Publication de fusion**, puis cliquez sur **Suivant**.  
  
5.  Dans la page Types d’Abonnés, vérifiez que seul [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou version ultérieure est sélectionné, puis cliquez sur **Suivant**.  
  
6.  Dans la page Articles, développez le nœud **Tables** , sélectionnez **SalesOrderHeader** et **SalesOrderDetail**, puis développez **Employee**, sélectionnez **EmployeeID** ou **LoginID**, puis cliquez sur **Suivant**.  
  
    > [!TIP]  
    > Les colonnes supplémentaires requises sont sélectionnées automatiquement. Choisissez une des colonnes sélectionnées automatiquement et affichez la remarque sous la liste **Objets à publier** pour savoir pourquoi cette colonne est nécessaire.  
  
7.  Dans la page Filtrer les lignes de la table, cliquez sur **Ajouter** , puis sur **Ajouter un filtre**.  
  
8.  Dans la boîte de dialogue **Ajouter un filtre** , sélectionnez **Employee (HumanResources)** dans **Sélectionnez la table à filtrer**, cliquez sur la colonne **LoginID** , cliquez sur la flèche droite pour ajouter la colonne à la clause WHERE de la requête de filtre et modifiez la clause WHERE comme suit :  
  
    ```  
    WHERE [LoginID] = HOST_NAME()  
    ```  
  
9. Cliquez sur **Une ligne de cette table ira à un seul abonnement**, puis sur **OK**.  
  
10. Dans la page **Filtrer les lignes de la table** , cliquez sur **Employee (Human Resources)**, cliquez sur **Ajouter** , puis sur **Ajouter une jointure pour étendre le filtre sélectionné**.  
  
11. Dans la boîte de dialogue **Ajouter une jointure** , sélectionnez **Sales.SalesOrderHeader** sous **Table jointe**, cliquez sur **Créer manuellement l’instruction de jointure**et complétez l’instruction de jointure comme suit :  
  
    ```  
    ON Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
    ```  
  
12. Dans **Spécifiez les options de jointure**, sélectionnez **Clé unique**, puis cliquez sur **OK**.  
  
13. Dans la page Filtrer les lignes de la table, cliquez sur **SalesOrderHeader**, cliquez sur **Ajouter**, puis sur **Ajouter une jointure pour étendre le filtre sélectionné**.  
  
14. Dans la boîte de dialogue **Ajouter une jointure** , sélectionnez **Sales.SalesOrderDetail** sous **Table jointe**.  
  
15. Cliquez sur **Créer manuellement l’instruction de jointure**.  
  
16. Dans **Colonnes de table filtrée**, sélectionnez **BusinessEntityID**, puis cliquez sur le bouton Flèche pour copier le nom de colonne dans l’instruction de jointure.  
  
17. Dans la zone **Instruction de jointure** , complétez l’instruction de jointure comme suit :  
  
    ```  
    ON Employee.BusinessEntityID = SalesOrderHeader.SalesPersonID  
    ```  
  
18. Dans **Spécifiez les options de jointure**, sélectionnez **Clé unique**, puis cliquez sur **OK**.  
  
19. Dans la page **Filtrer les lignes de la table** , cliquez sur **SalesOrderHeader (Sales)**, sur **Ajouter**, puis sur **Ajouter une jointure pour étendre le filtre sélectionné**.  
  
20. Dans la boîte de dialogue **Ajouter une jointure** , sélectionnez **Sales.SalesOrderDetail** sous **Table jointe**, cliquez sur **OK**, puis sur **Suivant**.  
  
21. Sélectionnez **Créer un instantané immédiatement**, décochez **Planifier l’exécution de l’Agent d’instantané aux heures suivantes**, puis cliquez sur **Suivant**.  
  
22. Dans la page Sécurité de l’agent, cliquez sur **Paramètres de sécurité**, tapez \<*nom_ordinateur>***\repl_snapshot** dans la zone **Compte de processus**, fournissez le mot de passe du compte et cliquez sur **OK**. Cliquez sur **Terminer**.  
  
23. Dans la page Terminer l’Assistant, entrez **AdvWorksSalesOrdersMerge** dans la zone **Nom de la publication** , puis cliquez sur **Terminer**.  
  
24. Une fois la publication créée, cliquez sur **Fermer**.  
  
### <a name="to-view-the-status-of-snapshot-generation"></a>Pour afficher l'état d'une génération d'instantané  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier Publications locales, cliquez avec le bouton droit sur **AdvWorksSalesOrdersMerge**, puis cliquez sur **Afficher l’état de l’Agent d’instantané**.  
  
3.  L'état en cours du travail de l'Agent d'instantané pour la publication s'affiche. Vérifiez que le travail d'instantané a bien réussi avant de passer à la leçon suivante.  
  
### <a name="to-add-the-merge-agent-login-to-the-pal"></a>Pour ajouter la connexion de l'Agent de fusion à la liste d'accès à la publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier Publications locales, cliquez avec le bouton droit sur **AdvWorksSalesOrdersMerge**, puis cliquez sur **Propriétés**.  
  
    La boîte de dialogue **Propriétés de la publication** s’affiche.  
  
3.  Sélectionnez la page **Liste d’accès à la publication** , puis cliquez sur **Ajouter**.  
  
4.  Dans la boîte de dialogue Ajouter un accès à une publication, sélectionnez *<nom_ordinateur>***\repl_merge* et cliquez sur **OK**. Cliquez sur **OK**.  
  
## <a name="next-steps"></a>Next Steps  
Vous avez créé avec succès la publication de fusion. Ensuite, vous allez créer l'abonnement à cette publication. Consultez [Leçon 2 : Création d’un abonnement à la publication de fusion](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
## <a name="see-also"></a> Voir aussi  
[Filtrer des données publiées](../../relational-databases/replication/publish/filter-published-data.md)  
[Filtres de lignes paramétrés](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
[Définir un article](../../relational-databases/replication/publish/define-an-article.md)  
  
  
  
