---
title: Aggiungere Configurazione app di Azure usando Servizi connessi | Microsoft Docs
description: Aggiungere una dipendenza del servizio Di configurazione di Azure all'app usando il Visual Studio Servizi connessi
author: ghogen
manager: ''
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 12/11/2020
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 250b89c983da039717982b31873a470172bde0f5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633163"
---
# <a name="adding-azure-app-configuration-by-using-visual-studio-connected-services"></a>Aggiunta Configurazione app di Azure tramite Visual Studio Servizi connessi

In questa esercitazione si apprenderà come aggiungere facilmente tutto il necessario per iniziare a usare Configurazione app di Azure per gestire la configurazione e i flag di funzionalità per i progetti Web in Visual Studio. Usando la funzionalità Servizi connessi in Visual Studio, è possibile fare in modo che Visual Studio abiliti automaticamente tutto il codice, i pacchetti NuGet e le impostazioni di configurazione necessari per connettersi alla risorsa di Configurazione app in Azure. Per usare questa funzionalità, è necessario usare Visual Studio 2019 versione 16.9 o successiva.

È possibile usare la funzionalità Configurazione app Servizi connessi in ASP.NET Core, nella console di .NET Core .NET Framework progetti.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Servizi connessi in Visual Studio per Mac](/visualstudio/mac/connected-services).

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio con il carico di lavoro di Azure installato.
- Un progetto di uno dei tipi supportati

## <a name="connect-to-azure-app-configuration-using-connected-services"></a>Connessione per Configurazione app di Azure usando Servizi connessi

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse sul** nodo Servizi connessi e scegliere Aggiungi servizio connesso dal menu di **scelta rapida.**

    ![Aggiunta di un servizio connesso di Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Nella scheda **Servizi connessi** selezionare l'icona + per **Dipendenze servizio**.

    ![Aggiungere una dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare **Configurazione app di Azure**.

    ![Aggiungere la configurazione dell'app](./media/vs-azure-tools-connected-services-app-configuration/add-azure-app-configuration.png)

    Se non è già stato eseguito l'accesso, accedere al proprio account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita.](https://azure.microsoft.com/free/dotnet)

1. Nella schermata **Configura Configurazione app di Azure** selezionare la sottoscrizione e un archivio di configurazione esistente. Selezionare quindi **Avanti**.

    Se è necessario creare un archivio di Configurazione app, andare al passaggio successivo. In caso contrario, andare al passaggio 6.

    ![Aggiungere un account di configurazione esistente al progetto](./media/vs-azure-tools-connected-services-app-configuration/select-config-store.png)

1. Per creare un archivio di configurazione app:

   1. Selezionare l'icona + a destra dell'intestazione **store di Configurazione** app. 

   1. Compilare la **Configurazione app di Azure: Crea nuovo** e selezionare **Crea.** Si noti che il campo Nome risorsa deve essere univoco. 

       ![Nuovo archivio di configurazione app di Azure](./media/vs-azure-tools-connected-services-app-configuration/create-new-config-store.png)

   1. Quando viene **Configurazione app di Azure** finestra di dialogo, il nuovo archivio di configurazione viene visualizzato nell'elenco. Selezionare questo nuovo archivio, quindi selezionare **Avanti.**

1. Immettere un nome per la stringa di connessione e scegliere se archiviare la stringa di connessione in un file di segreti locale o in [Azure Key Vault](/azure/key-vault).

   ![Specificare la stringa di connessione](./media/vs-azure-tools-connected-services-app-configuration/connection-string-app-config.png)

1. La **schermata Riepilogo delle** modifiche mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sono ok, scegliere **Fine.**

   ![Riepilogo delle modifiche](./media/vs-azure-tools-connected-services-app-configuration/summary-of-changes-app-config.png)

1. Al termine **del processo di configurazione** delle dipendenze, Configurazione app di Azure nel nodo **Dipendenze** del servizio del progetto.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni Configurazione app di Azure, [vedere Configurazione app di Azure documentazione di](/azure/azure-app-configuration/overview).

## <a name="see-also"></a>Vedi anche

- [Esercitazione per l'uso della configurazione dinamica in un'app ASP.NET Core app connessa](/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)