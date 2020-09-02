---
title: Aggiungere spazio di archiviazione di Azure usando Servizi connessi | Microsoft Docs
description: Aggiungere una dipendenza del servizio di archiviazione di Azure all'app usando Visual Studio Servizi connessi
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: f2f55a149420205435d9f64ea1f66c8c6854ec38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800515"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Aggiunta dell’archiviazione di Azure tramite Servizi connessi di Visual Studio

Con Visual Studio, è possibile connettere uno dei seguenti ad archiviazione di Azure usando la funzionalità **servizi connessi** :

- App console .NET Framework
- MVC ASP.NET (.NET Framework)
- ASP.NET Core
- .NET Core (incluse app console, WPF, Windows Forms, libreria di classi)
- Ruolo di lavoro .NET Core
- Funzioni di Azure
- App piattaforma UWP (Universal Windows Platform)
- Xamarin
- Cordova

La funzionalità servizio connesso aggiunge al progetto tutti i riferimenti richiesti e il codice di connessione e modifica i file di configurazione in modo appropriato.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Servizi connessi in Visual Studio per Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Prerequisiti

- Visual Studio con il carico di lavoro di Azure installato.
- Progetto di uno dei tipi supportati

## <a name="connect-to-azure-storage-using-connected-services"></a>Connettersi ad archiviazione di Azure usando Servizi connessi

::: moniker range="vs-2017"

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo **servizi connessi** e scegliere **Aggiungi servizio connesso**dal menu di scelta rapida.

    ![Aggiunta di un servizio connesso di Azure](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

1. Nella pagina **Servizi connessi** selezionare **Archiviazione cloud con Archiviazione di Azure**.

    ![Aggiungi Archiviazione di Azure](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. Nella finestra di dialogo **Archiviazione di Azure** selezionare un account di archiviazione esistente, quindi **Aggiungi**.

    Se è necessario creare un account di archiviazione, andare al passaggio successivo. In caso contrario, andare al passaggio 6.

    ![Aggiungere un account di archiviazione esistente al progetto l'elenco](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Per creare un account di archiviazione:

   1. Nella parte inferiore della finestra di dialogo fare clic su **Crea un nuovo account di archiviazione**.

   1. Compilare la finestra di dialogo **Crea account di archiviazione** e selezionare **Crea**.

       ![Nuovo account di archiviazione di Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Quando viene visualizzata la finestra di dialogo **Archiviazione di Azure**, la nuova risorsa di archiviazione viene visualizzata nell'elenco. Selezionare la nuova risorsa di archiviazione nell'elenco e quindi **Aggiungi**.

1. Il servizio connesso di archiviazione viene visualizzato sotto il nodo **Riferimenti servizio** del progetto.
:::moniker-end

:::moniker range=">=vs-2019"

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo **servizi connessi** e scegliere **Aggiungi servizio connesso**dal menu di scelta rapida.

    ![Aggiunta di un servizio connesso di Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Nella scheda **servizi connessi** selezionare l'icona + per le **dipendenze del servizio**.

    ![Aggiungi dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare archiviazione di **Azure**.

    ![Aggiungi Archiviazione di Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    Se non è già stato effettuato l'accesso, accedere al proprio account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita](https://azure.microsoft.com/account/free).

1. Nella schermata **Configura archiviazione di Azure** selezionare un account di archiviazione esistente e fare clic su **Avanti**.

    Se è necessario creare un account di archiviazione, andare al passaggio successivo. In caso contrario, andare al passaggio 6.

    ![Aggiungere un account di archiviazione esistente al progetto l'elenco](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. Per creare un account di archiviazione:

   1. Selezionare **Crea un account di archiviazione** nella parte inferiore della finestra di dialogo.

   1. Compilare la finestra di dialogo **archiviazione di Azure: Crea nuovo** e selezionare **Crea**.

       ![Nuovo account di archiviazione di Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. Quando viene visualizzata la finestra di dialogo **Archiviazione di Azure**, la nuova risorsa di archiviazione viene visualizzata nell'elenco. Selezionare il nuovo account di archiviazione nell'elenco e fare clic su **Avanti**.

1. Immettere un nome per la stringa di connessione e scegliere se si desidera che la stringa di connessione venga archiviata in un file di segreti locali o in [Azure Key Vault](/azure/key-vault).

   ![Specificare la stringa di connessione](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. La schermata **Riepilogo modifiche** Mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sembrano OK, scegliere **fine**.

   ![Riepilogo delle modifiche](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. Il servizio connesso di archiviazione viene visualizzato sotto il nodo **Riferimenti servizio** del progetto.
:::moniker-end

## <a name="see-also"></a>Vedere anche

- [Forum di Archiviazione di Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Documentazione di Archiviazione di Azure](/azure/storage/)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)
