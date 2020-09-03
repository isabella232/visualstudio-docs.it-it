---
title: Aggiungere Azure SignalR usando Servizi connessi | Microsoft Docs
description: Aggiungere Azure SignalR all'app usando Visual Studio per aggiungere un servizio connesso
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 0e44416bd6a55796b62a7590856caab8466a6401
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88643506"
---
# <a name="add-azure-signalr-by-using-visual-studio-connected-services"></a>Aggiungere Azure SignalR usando Visual Studio Servizi connessi

Con Visual Studio, è possibile connettere uno dei seguenti al servizio Azure SignalR usando la funzionalità **servizi connessi** :

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

## <a name="connect-to-azure-signalr-using-connected-services"></a>Connettersi ad Azure SignalR usando Servizi connessi

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo **servizi connessi** e scegliere **Aggiungi servizio connesso**dal menu di scelta rapida.

1. Nella scheda **servizi connessi** selezionare l'icona + per le **dipendenze del servizio**.

    ![Aggiungi dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare **servizio Azure SignalR**.

    ![Aggiungi servizio Azure SignalR](./media/azure-signalr-add-connected-service/add-signalr-service.png)

    Se non è già stato effettuato l'accesso, accedere al proprio account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita](https://azure.microsoft.com/account/free).

1. Nella schermata **Configura Azure SignalR** selezionare un componente di Azure SignalR esistente e fare clic su **Avanti**.

    Se è necessario creare un nuovo componente, andare al passaggio successivo. In caso contrario, andare al passaggio 7.

    ![Connettersi a un componente di Azure SignalR esistente](./media/azure-signalr-add-connected-service/created-signalr.png)

1. Per creare un'istanza del servizio Azure SignalR:

   1. Selezionare **Crea una nuova istanza del servizio SignalR di Azure** nella parte inferiore della schermata.

   1. Compilare il **servizio Azure SignalR: Crea nuova** schermata e selezionare **Crea**.

       ![Nuova istanza del servizio Azure SignalR](./media/azure-signalr-add-connected-service/create-new-signalr.png)

   1. Quando viene visualizzata la schermata **Configura servizio Azure SignalR** , la nuova istanza viene visualizzata nell'elenco. Selezionare la nuova istanza nell'elenco e fare clic su **Avanti**.

1. Immettere un nome per la stringa di connessione o scegliere l'impostazione predefinita e scegliere se si desidera che la stringa di connessione venga archiviata in un file dei segreti locali o in [Azure Key Vault](/azure/key-vault).

   ![Specificare la stringa di connessione](./media/azure-signalr-add-connected-service/connection-string.png)

1. La schermata **Riepilogo modifiche** Mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sembrano OK, scegliere **fine**.

   ![Riepilogo delle modifiche](./media/azure-signalr-add-connected-service/summary-of-changes.png)

1. La connessione viene visualizzata nella sezione **dipendenze del servizio** della scheda **servizi connessi** .

   ![Dipendenze dei servizi](./media/azure-signalr-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Vedere anche

- [Pagina del prodotto Azure SignalR](https://azure.microsoft.com/services/signalr-service/)
- [Documentazione relativa al Servizio Azure SignalR](/azure/azure-signalr)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)
