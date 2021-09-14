---
title: Aggiungere Azure CosmosDB usando Servizi connessi | Microsoft Docs
description: Aggiungere il supporto di Azure CosmosDB all'app usando il Visual Studio per aggiungere un servizio connesso
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 182e39c3dd1c166b539023427891c8bcd63eb193
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633291"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Aggiungere il database Cosmos Azure all'app usando Visual Studio Servizi connessi

Con Visual Studio, è possibile connettere uno degli elementi seguenti ad Azure Cosmos DB usando **la** Servizi connessi funzionalità:

- .NET Framework app console
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (tra cui app console, WPF, Windows Form, libreria di classi)
- Ruolo di lavoro .NET Core
- Funzioni di Azure
- App Windows Universal Platform
- Xamarin
- Cordova

La funzionalità servizio connesso aggiunge al progetto tutti i riferimenti richiesti e il codice di connessione e modifica i file di configurazione in modo appropriato.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Servizi connessi in Visual Studio per Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Prerequisiti

- Visual Studio con il carico di lavoro di Azure installato.
- Progetto di uno dei tipi supportati

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>Connessione al database Cosmos Azure usando Servizi connessi

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo Servizi connessi **e** scegliere Aggiungi servizio connesso dal menu di **scelta rapida.**

1. Nella scheda **Servizi connessi** selezionare l'icona + per **Dipendenze servizio**.

    ![Aggiungere una dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare Azure **Cosmos DB**.

    ![Aggiungere un database Cosmos Azure](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    Se non è già stato eseguito l'accesso, accedere all'account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita.](https://azure.microsoft.com/account/free)

1. Nella schermata **Azure Cosmos DB** selezionare un database di Azure Cosmos esistente e selezionare **Avanti.**

    Se è necessario creare un database, andare al passaggio successivo. In caso contrario, andare al passaggio 7.

    ![Aggiungere un database Cosmos esistente al progetto](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. Per creare un database Cosmos Azure:

   1. Selezionare **Crea un nuovo database Cosmos Azure** nella parte inferiore della schermata.

   1. Compilare la **schermata Azure Cosmos DB: Crea** nuovo e selezionare **Crea**.

       ![Nuovo database Cosmos Azure](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. Quando viene **visualizzata la finestra di dialogo Configura database** Cosmos Azure, il nuovo database viene visualizzato nell'elenco. Selezionare il nuovo database nell'elenco e selezionare **Avanti.**

1. Immettere un nome di stringa di connessione e scegliere se archiviare la stringa di connessione in un file di segreti locale [o](/azure/key-vault)in Azure Key Vault .

   ![Specificare la stringa di connessione](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. La **schermata Riepilogo delle** modifiche mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sono ok, scegliere **Fine.**

   ![Riepilogo delle modifiche](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. La connessione viene visualizzata nella **sezione Dipendenze** servizio della **scheda** Servizi connessi connessione.

   ![Dipendenze dei servizi](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Vedi anche

- [Pagina del prodotto Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)
- [Documentazione di Azure Cosmos DB](/azure/cosmos-db/)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)
