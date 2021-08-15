---
title: Gestione delle risorse di Azure con Cloud Explorer | Documentazione Microsoft
description: Informazioni su come usare Cloud Explorer per esplorare e gestire le risorse di Azure in Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: 56e54aeb628ab6f80cef6400f48be40d675975df3bc8c87b78d1126a70fa5a99
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121363696"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Gestire le risorse associate agli account di Azure in Visual Studio Cloud Explorer

::: moniker range=">=vs-2022"
> [!Important]
> Cloud Explorer è stato ritirato in Visual Studio 2022. È invece possibile usare le alternative seguenti:
> - Usare [Microsoft Azure Storage Explorer](/azure/vs-azure-tools-storage-manage-with-storage-explorer) è un'app autonoma gratuita di Microsoft. È possibile usarla per rappresentare facilmente dati di Archiviazione di Azure in Windows, macOS e Linux.
> - La [console Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) offre l'accesso diretto da riga di comando con privilegi elevati al server del servizio app e al relativo file system. Oltre a essere un utile strumento di debug, supporta operazioni CLI, come l'installazione dei pacchetti.
>
> Se necessario, è possibile usare il portale di Azure o continuare a usare il nodo azure di Esplora server nelle versioni precedenti di Visual Studio.
>
> Per altre informazioni su Visual Studio 2022, vedere le note [sulla versione](/visualstudio/releases/2022/release-notes-preview/).

::: moniker-end

::: moniker range="<=vs-2019"

Cloud Explorer consente di visualizzare le risorse di Azure e i gruppi di risorse, controllare le relative proprietà ed eseguire azioni di diagnostica fondamentali per gli sviluppatori dall'interno di Visual Studio.

Cloud Explorer è basato sullo stack di Azure Resource Manager, proprio come il [portale di Azure](https://portal.azure.com). Pertanto riconosce risorse, come i gruppi di risorse di Azure e i servizi di Azure, come le app per la logica e le app per le API. Supporta infine il [controllo degli accessi in base al ruolo](/azure/role-based-access-control/role-assignments-portal) (RBAC).

## <a name="prerequisites"></a>Prerequisiti

* Visual Studio 2017 o versione successiva (vedere [Download di Visual Studio](https://visualstudio.microsoft.com/downloads)) con il **carico di lavoro Azure** selezionato. È anche possibile usare una versione precedente di Visual Studio con [Microsoft Azure SDK per .NET 2.9](https://www.microsoft.com/download/details.aspx?id=51657).
* Account di Microsoft Azure: se non si ha un account, è possibile [iscriversi per ottenere una versione di valutazione gratuita](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) oppure [attivare i vantaggi della sottoscrizione di Visual Studio](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).

> [!NOTE]
> Per visualizzare Cloud Explorer, premere **CTRL** + **Q** per attivare la casella di ricerca e quindi **immettere Cloud Explorer**.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Aggiungere un account di Azure a Cloud Explorer

Per visualizzare le risorse associate a un account Azure, è innanzitutto necessario aggiungere l'account **Cloud Explorer**.

1. In **Cloud Explorer** selezionare il pulsante **Gestione** account.

   ![Icona delle impostazioni account di Azure di Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Selezionare **Gestisci account**.

   ![Collegamento per l'aggiunta dell'account di Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Accedere all'account di Azure di cui si vogliono esplorare le risorse.

1. Una volta effettuato l'accesso all'account di Azure, vengono visualizzate le sottoscrizioni associate all'account. Selezionare le caselle di controllo relative alle sottoscrizioni dell'account da esplorare, quindi selezionare **Applica**.

   ![Cloud Explorer: selezionare le sottoscrizioni di Azure da visualizzare](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Dopo aver selezionato le sottoscrizioni di cui si vogliono esplorare le risorse, tali sottoscrizioni e risorse vengono visualizzate nel **Cloud Explorer**.

   ![Elenco delle risorse di Cloud Explorer per un account Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Rimuovere un account di Azure da Cloud Explorer

1. In **Cloud Explorer** scegliere **Gestione account**.

   ![Azure Account settings](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Accanto all'account che si desidera rimuovere, selezionare **Gestisci account**.

   ![Rimozione di un account](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Scegli **Rimuovi** per rimuovere un account.

    ![Finestra di dialogo Gestisci account di Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Visualizzare i tipi o i gruppi di risorse

Per visualizzare le risorse di Azure, è possibile scegliere la visualizzazione **Tipi di risorsa** o **Gruppi di risorse**.

1. In **Cloud Explorer**, selezionare l'elenco a discesa per la visualizzazione delle risorse.

   ![Elenco a discesa di Cloud Explorer per selezionare la visualizzazione di risorse desiderata](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. Dal menu di scelta rapida selezionare la visualizzazione desiderata:

   * Visualizzazione **Tipi di risorsa**: la visualizzazione comune usata nel [portale di Azure](https://portal.azure.com), mostra le risorse di Azure classificate in base al tipo, ad esempio app Web, account di archiviazione e macchine virtuali.
   * Visualizzazione **Gruppi di risorse**: classifica le risorse di Azure in base al gruppo di risorse di Azure a cui sono associate. Un gruppo di risorse è un bundle di risorse di Azure, in genere usate da un'applicazione specifica. Per altre informazioni sui gruppi di risorse di Azure, vedere [Panoramica di Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview).

   L'immagine seguente illustra un confronto tra le visualizzazioni di due risorse:

   ![Confronto tra visualizzazioni delle risorse di Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Visualizzare ed esplorare le risorse in Cloud Explorer

Per passare a una risorsa di Azure e visualizzare le informazioni corrispondenti in Cloud Explorer, espandere il tipo o il gruppo di risorse associato dell'elemento, quindi selezionare la risorsa. Quando si seleziona una risorsa, le informazioni vengono visualizzate nelle due schede: **Azioni** e **Proprietà** nella parte inferiore di Cloud Explorer.

* La scheda **Azioni** mostra le azioni che possono essere eseguite in Cloud per la risorsa selezionata. È inoltre possibile visualizzare queste opzioni facendo clic con pulsante destro del mouse sulla risorsa per visualizzare il menu di scelta rapida.

* La scheda **Proprietà** mostra le proprietà della risorsa, ad esempio il tipo, le impostazioni locali e il gruppo di risorse a cui è associata.

Di seguito viene illustrato un confronto di esempio di ciò che viene visualizzato in ogni scheda per un servizio App:

  ![Screenshot di Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

L'azione **Open in portal** è disponibile per ogni risorsa. Quando si sceglie questa azione, Cloud Explorer mostra la risorsa selezionata nel [portale di Azure](https://portal.azure.com). La funzionalità **Apri nel portale** è particolarmente utile per l'esplorazione di risorse con molti livelli di nidificazione.

È possibile che vengano visualizzate azioni aggiuntive e altri valori di proprietà, in base alla risorsa di Azure. Ad esempio, per le app Web e le app per la logica sono disponibili anche le azioni **Apri nel browser** e **Collega debugger**, oltre ad **Apri nel portale**. Quando si sceglie un BLOB, una coda o una tabella dell'account di archiviazione, vengono visualizzate le azioni per l'apertura di editor. Per le app Azure sono disponibili le proprietà relative a **URL** e **stato**, mentre per le risorse di archiviazione sono disponibili le proprietà relative alle chiavi e alle stringhe di connessione.

## <a name="find-resources-in-cloud-explorer"></a>Cercare risorse in Cloud Explorer

Per individuare le risorse con un nome specifico nelle sottoscrizioni dell'account Azure, immettere il nome nella **casella** Cerca in **Cloud Explorer**.

  ![Ricerca di risorse in Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

Quando si immettono caratteri nella **casella Cerca,** nell'albero delle risorse vengono visualizzate solo le risorse che corrispondono a tali caratteri.

::: moniker-end
