---
title: Aggiungere spazio di archiviazione di Azure usando Servizi connessi | Microsoft Docs
description: Aggiungere una Archiviazione di Azure di servizio all'app usando il Visual Studio Servizi connessi
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: 76a886002bb8b8d7aaeca60690e83847087bf42cb5d54e9cee7922c714e61a29
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121348896"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Aggiunta dell’archiviazione di Azure tramite Servizi connessi di Visual Studio

Con Visual Studio, è possibile connettere uno degli elementi seguenti a Archiviazione di Azure usando la **Servizi connessi** funzionalità:

- .NET Framework app console
- ASP.NET MVC (.NET Framework)
- ASP.NET Core
- .NET Core (tra cui app console, WPF, Windows Form, libreria di classi)
- Ruolo di lavoro .NET Core
- Funzioni di Azure
- App Windows universali
- Xamarin
- Cordova

La funzionalità servizio connesso aggiunge al progetto tutti i riferimenti richiesti e il codice di connessione e modifica i file di configurazione in modo appropriato.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Servizi connessi in Visual Studio per Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Prerequisiti

- Visual Studio con il carico di lavoro di Azure installato.
- Progetto di uno dei tipi supportati

## <a name="connect-to-azure-storage-using-connected-services"></a>Connessione usare Archiviazione di Azure Servizi connessi

::: moniker range="vs-2017"

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni** fare clic con  il pulsante destro del mouse sul nodo Servizi connessi e scegliere Aggiungi servizio connesso dal menu **di scelta rapida.**

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

1. In **Esplora soluzioni** fare clic con il pulsante destro **del** mouse sul nodo Servizi connessi e scegliere Aggiungi servizio connesso dal menu di **scelta rapida.**

    ![Aggiunta di un servizio connesso di Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Nella scheda **Servizi connessi** selezionare l'icona + per **Dipendenze servizio**.

    ![Aggiungere una dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare **Archiviazione di Azure**.

    ![Aggiungi Archiviazione di Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    Se non è già stato eseguito l'accesso, accedere all'account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita.](https://azure.microsoft.com/account/free)

1. Nella schermata **Configura Archiviazione di Azure** selezionare un account di archiviazione esistente e selezionare **Avanti.**

    Se è necessario creare un account di archiviazione, andare al passaggio successivo. In caso contrario, andare al passaggio 6.

    ![Aggiungere un account di archiviazione esistente al progetto l'elenco](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. Per creare un account di archiviazione:

   1. Selezionare **Crea un account di archiviazione** nella parte inferiore della finestra di dialogo.

   1. Compilare la finestra **Archiviazione di Azure: Crea nuovo** e selezionare **Crea**.

       ![Nuovo account di archiviazione di Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. Quando viene visualizzata la finestra di dialogo **Archiviazione di Azure**, la nuova risorsa di archiviazione viene visualizzata nell'elenco. Selezionare il nuovo account di archiviazione nell'elenco e selezionare **Avanti.**

1. Immettere un nome di stringa di connessione e scegliere se archiviare la stringa di connessione in un file di segreti locale [o](/azure/key-vault)in Azure Key Vault .

   ![Specificare la stringa di connessione](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. La **schermata Riepilogo delle** modifiche mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sono ok, scegliere **Fine.**

   ![Riepilogo delle modifiche](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. Il servizio connesso di archiviazione viene visualizzato sotto il nodo **Riferimenti servizio** del progetto.
:::moniker-end

## <a name="see-also"></a>Vedi anche

- [Forum di Archiviazione di Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Documentazione di Archiviazione di Azure](/azure/storage/)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)
