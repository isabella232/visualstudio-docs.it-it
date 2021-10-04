---
title: Aggiungere applicazione Azure Insights usando Servizi connessi | Microsoft Docs
description: Aggiungere applicazione Azure Insights all'app usando il Visual Studio per aggiungere un servizio connesso
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 0f7cf3bd3166d4051dd100ca3d3a4d7a94b2b207
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129430700"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>Aggiungere applicazione Azure Insights usando Visual Studio Servizi connessi

Con Visual Studio, è possibile connettere uno degli elementi seguenti a applicazione Azure Insights usando la **Servizi connessi** seguente:

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

## <a name="connect-to-azure-application-insights-using-connected-services"></a>Connessione per applicazione Azure Insights usando Servizi connessi

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni** fare clic con il pulsante destro **del** mouse sul nodo Servizi connessi e scegliere Aggiungi servizio connesso dal menu di **scelta rapida.**

1. Nella scheda **Servizi connessi** selezionare l'icona + per **Dipendenze servizio**.

    ![Aggiungere una dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare **applicazione Azure Insights**.

    ![Aggiungere applicazione Azure Insights](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    Se non è già stato eseguito l'accesso, accedere al proprio account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita.](https://azure.microsoft.com/free/)

1. Nella schermata **Configura applicazione Azure Insights** selezionare un componente applicazione Azure Insights esistente e selezionare **Avanti.**

    Se è necessario creare un nuovo componente, andare al passaggio successivo. In caso contrario, andare al passaggio 7.

    ![Connessione al componente application Insights esistente](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. Per creare un componente application Insights:

   1. Selezionare **Crea una nuova applicazione Insights componente** nella parte inferiore della schermata.

   1. Compilare la **schermata Insights: Crea nuovo** e selezionare **Crea.**

       ![Nuovo app Azure Insights componente](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. Quando viene **visualizzata la applicazione Azure Insights** configurazione, il nuovo componente viene visualizzato nell'elenco. Selezionare il nuovo componente nell'elenco e selezionare **Avanti.**

1. Immettere un nome di chiave di strumentazione o scegliere il valore predefinito e scegliere se si vuole archiviare la stringa di connessione in un file di segreti locale o in [Azure Key Vault](/azure/key-vault).

   ![Specificare la stringa di connessione](./media/azure-app-insights-add-connected-service/connection-string.png)

1. La **schermata Riepilogo delle** modifiche mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sono ok, scegliere **Fine.**

   ![Riepilogo delle modifiche](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. La connessione viene visualizzata nella **sezione Dipendenze servizio** della **scheda Servizi connessi** servizio.

   ![Dipendenze dei servizi](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Vedi anche

- [Monitoraggio di Azure pagina del prodotto](https://azure.microsoft.com/services/monitor/)
- [app Azure Insights documentazione](/azure/azure-monitor/app/app-insights-overview/)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)
