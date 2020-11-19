---
title: Aggiungere applicazione Azure Insights utilizzando Servizi connessi | Microsoft Docs
description: Aggiungere applicazione Azure Insights all'app usando Visual Studio per aggiungere un servizio connesso
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 1317f41c9463ab645e6dd3ba281f11b9246720a8
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901934"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>Aggiungere applicazione Azure Insights tramite Visual Studio Servizi connessi

Con Visual Studio, è possibile connettere uno dei seguenti elementi a applicazione Azure Insights usando la funzionalità **servizi connessi** :

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

## <a name="connect-to-azure-application-insights-using-connected-services"></a>Connettersi a applicazione Azure Insights utilizzando Servizi connessi

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **servizi connessi** e scegliere **Aggiungi servizio connesso** dal menu di scelta rapida.

1. Nella scheda **servizi connessi** selezionare l'icona + per le **dipendenze del servizio**.

    ![Aggiungi dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare **applicazione Azure Insights**.

    ![Aggiungi applicazione Azure Insights](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    Se non è già stato effettuato l'accesso, accedere al proprio account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita](https://azure.microsoft.com/account/free).

1. Nella schermata **Configure applicazione Azure Insights** selezionare un componente di applicazione Azure Insights esistente e fare clic su Next ( **Avanti**).

    Se è necessario creare un nuovo componente, andare al passaggio successivo. In caso contrario, andare al passaggio 7.

    ![Connetti a componente Application Insights esistente](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. Per creare un componente Application Insights:

   1. Selezionare **Crea nuovo componente Application Insights** nella parte inferiore della schermata.

   1. Compilare il **Application Insights: Crea nuova** schermata e selezionare **Crea**.

       ![Nuovo componente app Azure Insights](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. Quando viene visualizzata la schermata **configura applicazione Azure Insights** , il nuovo componente viene visualizzato nell'elenco. Selezionare il nuovo componente nell'elenco e fare clic su **Avanti**.

1. Immettere un nome per la chiave di strumentazione o scegliere l'impostazione predefinita e scegliere se si desidera che la stringa di connessione venga archiviata in un file di segreti locale o in [Azure Key Vault](/azure/key-vault).

   ![Specificare la stringa di connessione](./media/azure-app-insights-add-connected-service/connection-string.png)

1. La schermata **Riepilogo modifiche** Mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sembrano OK, scegliere **fine**.

   ![Riepilogo delle modifiche](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. La connessione viene visualizzata nella sezione **dipendenze del servizio** della scheda **servizi connessi** .

   ![Dipendenze dei servizi](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Vedere anche

- [Pagina del prodotto monitoraggio di Azure](https://azure.microsoft.com/services/monitor/)
- [Documentazione di app Azure Insights](/azure/azure-monitor/app/app-insights-overview/)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)
