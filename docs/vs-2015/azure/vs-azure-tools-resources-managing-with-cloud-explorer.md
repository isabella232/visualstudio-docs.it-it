---
title: Gestione delle risorse di Azure con Cloud Explorer | Microsoft Docs
description: Informazioni su come usare Cloud Explorer per esplorare e gestire le risorse di Azure all'interno di Visual Studio.
author: ghogen
manager: douge
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: a5b75aa5e1310e02befe162199472eef987d7cd9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002361"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Gestire le risorse associate agli account di Azure in Visual Studio Cloud Explorer

Cloud Explorer consente di visualizzare le risorse di Azure e i gruppi di risorse, controllare le relative proprietà ed eseguire azioni di diagnostica fondamentali per gli sviluppatori dall'interno di Visual Studio. 

Ad esempio la [portale di Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040), Cloud Explorer è basato sullo stack di Azure Resource Manager. Pertanto riconosce risorse, ad esempio gruppi di risorse di Azure e servizi di Azure come App per le API e App per la logica e supporta [controllo degli accessi in base al ruolo](/azure/role-based-access-control/role-assignments-portal.md) (RBAC). 

## <a name="prerequisites"></a>Prerequisiti

* Visual Studio 2015 con la [Microsoft Azure SDK per .NET 2.9](https://www.microsoft.com/en-us/download/details.aspx?id=51657).
* Account di Microsoft Azure: se non hai un account, è possibile [iscriversi a una versione di valutazione gratuita](http://go.microsoft.com/fwlink/?LinkId=623901) oppure [attivare i benefici della sottoscrizione Visual Studio](http://go.microsoft.com/fwlink/?LinkId=623901).

> [!NOTE]
> Per visualizzare Cloud Explorer, selezionare **View** > **Cloud Explorer** nella barra dei menu.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Aggiungere un'istanza di Azure dell'account a Cloud Explorer

Per visualizzare le risorse associate a un account Azure, è innanzitutto necessario aggiungere l'account a Cloud Explorer. 

1. Nelle **Cloud Explorer**, selezionare **impostazioni account Azure**.

   ![Icona delle impostazioni di cloud Explorer Azure account](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Selezionare **gestire gli account**. 

   ![Collegamento Aggiungi-account di cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Accedere all'account Azure di cui si vogliono esplorare le risorse. 

1. Una volta effettuato l'accesso a un account Azure, visualizzare le sottoscrizioni associate a quell'account. Selezionare le caselle di controllo per le sottoscrizioni di account si vuole cercare e quindi selezionare **applica**. 

   ![Cloud Explorer: selezionare le sottoscrizioni di Azure per visualizzare](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Dopo aver selezionato le sottoscrizioni di cui si vogliono esplorare le risorse, tali sottoscrizioni e risorse visualizzati in Cloud Explorer.

   ![Risorse di cloud Explorer listato per un account di Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Rimuovere un account di Azure da Cloud Explorer 

1. Nelle **Cloud Explorer**, selezionare **gestione degli Account**.

   ![Icona delle impostazioni di cloud Explorer Azure account](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Accanto all'account che si desidera rimuovere, selezionare **Manage Accounts**.

   ![Icona delle impostazioni di cloud Explorer Azure account](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Scegli **rimuovere** per rimuovere un account.

    ![Finestra di dialogo account di gestione di soluzioni cloud](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Visualizzare i tipi di risorse o gruppi di risorse

Per visualizzare le risorse di Azure, è possibile scegliere **tipi di risorse** oppure **gruppi di risorse** visualizzazione.

1. Nelle **Cloud Explorer**, selezionare l'elenco a discesa la visualizzazione di risorse.

   ![Elenco a discesa di soluzioni cloud per selezionare la visualizzazione di risorse desiderata](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. Dal menu di scelta rapida, selezionare la visualizzazione desiderata: 

   * **Tipi di risorse** visualizzare - la visualizzazione comune usata nel [portale di Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040), Mostra le risorse di Azure classificate in base al tipo, ad esempio App web, gli account di archiviazione e macchine virtuali. 
   * **Gruppi di risorse** visualizzare - le risorse di Azure vengono suddivisi in categorie per il gruppo di risorse di Azure con cui sono associate. Un gruppo di risorse è un bundle di risorse di Azure, in genere usate da un'applicazione specifica. Per altre informazioni sui gruppi di risorse di Azure, vedere [Panoramica di Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview).

   L'immagine seguente mostra un confronto tra le visualizzazioni di due risorse:

   ![Confronto tra visualizzazioni di Esplora risorse cloud](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Visualizzare ed esplorare le risorse in Cloud Explorer

Per passare a una risorsa di Azure e visualizzare le informazioni relative in Cloud Explorer, espandere tipo o il gruppo di risorse associato dell'elemento e quindi selezionare la risorsa. Quando si seleziona una risorsa, informazioni vengono visualizzate in due schede: **azioni** e **proprietà** : nella parte inferiore di Cloud Explorer.

* **Azioni** scheda - Elenca le azioni da intraprendere in Cloud Explorer per la risorsa selezionata. È anche possibile visualizzare queste opzioni facendo clic su risorsa per visualizzare il menu di scelta rapida.

* **Proprietà** scheda - Mostra le proprietà della risorsa, ad esempio il gruppo di risorse, delle impostazioni locali e tipo a cui è associato.

L'immagine seguente mostra un confronto di esempio di ciò che viene visualizzato in ogni scheda per un servizio App:

  ![Schermata di Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Ogni risorsa ha l'azione **Apri nel portale**. Quando si sceglie questa azione, Cloud Explorer consente di visualizzare la risorsa selezionata nel [portale di Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040). Il **Apri nel portale** funzionalità è utile per lo spostamento alle risorse eccessivamente annidate.

Azioni aggiuntive e i valori delle proprietà può essere visualizzato anche in base alle risorse di Azure. Ad esempio, le app web e App per la logica anche disponibili le azioni **Apri nel browser** e **collega debugger** oltre ai **Apri nel portale**. Le azioni per aprire gli editor vengono visualizzate quando si sceglie un blob dell'account di archiviazione, coda o tabella. Le app di Azure hanno **URL** e **stato** proprietà, mentre le risorse di archiviazione hanno proprietà della stringa di connessione e chiave.

## <a name="find-resources-in-cloud-explorer"></a>Trovare le risorse in Cloud Explorer

Per individuare le risorse con un nome specifico nelle sottoscrizioni dell'account Azure, immettere il nome nella **ricerca** casella in Cloud Explorer.

  ![Ricerca di risorse in Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

Quando si immettono caratteri nella **ricerca** casella, solo le risorse corrispondenti ai caratteri vengono visualizzati nell'albero delle risorse.
