---
title: Aggiungere Azure SignalR usando Servizi connessi | Microsoft Docs
description: Aggiungere Azure SignalR all'app usando il Visual Studio per aggiungere un servizio connesso
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: a6fe465c064239c66fe88b9e49b8950604f614ec
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129430573"
---
# <a name="add-azure-signalr-by-using-visual-studio-connected-services"></a>Aggiungere Azure SignalR usando Visual Studio Servizi connessi

Con Visual Studio, è possibile connettere uno degli elementi seguenti al servizio Azure SignalR usando la **Servizi connessi** seguente:

- .NET Framework app console
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (inclusi app console, WPF, Windows Form, libreria di classi)
- Ruolo di lavoro .NET Core
- Funzioni di Azure
- App universal Windows platform
- Xamarin
- Cordova

La funzionalità servizio connesso aggiunge al progetto tutti i riferimenti richiesti e il codice di connessione e modifica i file di configurazione in modo appropriato.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Servizi connessi in Visual Studio per Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Prerequisiti

- Visual Studio con il carico di lavoro di Azure installato.
- Un progetto di uno dei tipi supportati

## <a name="connect-to-azure-signalr-using-connected-services"></a>Connessione ad Azure SignalR usando Servizi connessi

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni** fare clic con il pulsante destro **del** mouse sul nodo Servizi connessi e scegliere Aggiungi servizio connesso dal menu di **scelta rapida.**

1. Nella scheda **Servizi connessi** selezionare l'icona + per **Dipendenze servizio**.

    ![Aggiungere una dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare **Servizio Azure SignalR**.

    ![Aggiungere Servizio Azure SignalR](./media/azure-signalr-add-connected-service/add-signalr-service.png)

    Se non è già stato eseguito l'accesso, accedere al proprio account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita.](https://azure.microsoft.com/free/)

1. Nella schermata **Configura Azure SignalR** selezionare un componente Azure SignalR esistente e selezionare **Avanti.**

    Se è necessario creare un nuovo componente, andare al passaggio successivo. In caso contrario, andare al passaggio 7.

    ![Connessione al componente Azure SignalR esistente](./media/azure-signalr-add-connected-service/created-signalr.png)

1. Per creare un'istanza del servizio Azure SignalR:

   1. Selezionare **Crea una nuova Servizio Azure SignalR istanza** nella parte inferiore della schermata.

   1. Compilare la **Servizio Azure SignalR: Crea nuova** schermata e selezionare **Crea.**

       ![Nuova Servizio Azure SignalR istanza](./media/azure-signalr-add-connected-service/create-new-signalr.png)

   1. Quando viene **visualizzata la Servizio Azure SignalR** configurazione, la nuova istanza viene visualizzata nell'elenco. Selezionare la nuova istanza nell'elenco e selezionare **Avanti.**

1. Immettere un nome di stringa di connessione o scegliere il valore predefinito e scegliere se si vuole archiviare la stringa di connessione in un file di segreti locale o in [Azure Key Vault](/azure/key-vault).

   ![Specificare la stringa di connessione](./media/azure-signalr-add-connected-service/connection-string.png)

1. La **schermata Riepilogo delle** modifiche mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sono ok, scegliere **Fine.**

   ![Riepilogo delle modifiche](./media/azure-signalr-add-connected-service/summary-of-changes.png)

1. La connessione viene visualizzata nella **sezione Dipendenze servizio** della **scheda Servizi connessi** servizio.

   ![Dipendenze dei servizi](./media/azure-signalr-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Vedi anche

- [Pagina del prodotto Azure SignalR](https://azure.microsoft.com/services/signalr-service/)
- [Documentazione relativa al Servizio Azure SignalR](/azure/azure-signalr)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)
