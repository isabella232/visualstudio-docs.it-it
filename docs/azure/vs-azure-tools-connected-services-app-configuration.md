---
title: Aggiungere app Azure configurazione utilizzando Servizi connessi | Microsoft Docs
description: Aggiungere una dipendenza del servizio di configurazione di Azure all'app usando Visual Studio Servizi connessi
author: ghogen
manager: ''
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 12/11/2020
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 250b89c983da039717982b31873a470172bde0f5
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683297"
---
# <a name="adding-azure-app-configuration-by-using-visual-studio-connected-services"></a>Aggiunta di app Azure configurazione con Visual Studio Servizi connessi

In questa esercitazione si apprenderà come aggiungere facilmente tutti gli elementi necessari per iniziare a usare app Azure configurazione per gestire la configurazione e i flag delle funzionalità per i progetti Web in Visual Studio. Usando la funzionalità Servizi connessi in Visual Studio, è possibile fare in modo che Visual Studio aggiunga automaticamente tutto il codice, i pacchetti NuGet e le impostazioni di configurazione necessari per connettersi alla risorsa di configurazione dell'app in Azure. Per usare questa funzionalità, è necessario usare Visual Studio 2019 versione 16,9 o successiva.

È possibile usare la funzionalità di configurazione delle app Servizi connessi in ASP.NET Core, nella console di .NET Core e nei progetti di .NET Framework.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Servizi connessi in Visual Studio per Mac](/visualstudio/mac/connected-services).

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio con il carico di lavoro di Azure installato.
- Progetto di uno dei tipi supportati

## <a name="connect-to-azure-app-configuration-using-connected-services"></a>Connettersi alla configurazione di app Azure tramite Servizi connessi

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **servizi connessi** e scegliere **Aggiungi servizio connesso** dal menu di scelta rapida.

    ![Aggiunta di un servizio connesso di Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Nella scheda **servizi connessi** selezionare l'icona + per le **dipendenze del servizio**.

    ![Aggiungi dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare **configurazione app Azure**.

    ![Aggiungere la configurazione dell'app](./media/vs-azure-tools-connected-services-app-configuration/add-azure-app-configuration.png)

    Se non è già stato effettuato l'accesso, accedere al proprio account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita](https://azure.microsoft.com/free/dotnet).

1. Nella schermata **configura configurazione app Azure** selezionare la sottoscrizione e un archivio di configurazione esistente. Selezionare quindi **Avanti**.

    Se è necessario creare un archivio di configurazione dell'app, andare al passaggio successivo. In caso contrario, andare al passaggio 6.

    ![Aggiungi account di configurazione esistente al progetto](./media/vs-azure-tools-connected-services-app-configuration/select-config-store.png)

1. Per creare un archivio di configurazione dell'app:

   1. Selezionare l'icona + a destra dell'intestazione **archivi di configurazione dell'app** . 

   1. Compilare la finestra di dialogo **configurazione app Azure: Crea nuovo** e selezionare **Crea**. Si noti che il campo del nome della risorsa deve essere univoco. 

       ![Nuovo archivio di configurazione dell'app di Azure](./media/vs-azure-tools-connected-services-app-configuration/create-new-config-store.png)

   1. Quando viene visualizzata la finestra di dialogo **app Azure Configuration** , il nuovo archivio di configurazione viene visualizzato nell'elenco. Selezionare questo nuovo negozio, quindi fare clic su **Avanti**.

1. Immettere un nome per la stringa di connessione e scegliere se si desidera che la stringa di connessione venga archiviata in un file di segreti locali o in [Azure Key Vault](/azure/key-vault).

   ![Specificare la stringa di connessione](./media/vs-azure-tools-connected-services-app-configuration/connection-string-app-config.png)

1. La schermata **Riepilogo modifiche** Mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sembrano OK, scegliere **fine**.

   ![Riepilogo delle modifiche](./media/vs-azure-tools-connected-services-app-configuration/summary-of-changes-app-config.png)

1. Al termine del **processo di configurazione delle dipendenze** , app Azure configurazione viene ora visualizzata sotto il nodo **dipendenze del servizio** del progetto.

## <a name="next-steps"></a>Passaggi successivi

Informazioni sulla configurazione di app Azure in [app Azure documentazione di configurazione](/azure/azure-app-configuration/overview).

## <a name="see-also"></a>Vedi anche

- [Esercitazione per l'uso della configurazione dinamica in una configurazione di app connessa ASP.NET Core app](/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)