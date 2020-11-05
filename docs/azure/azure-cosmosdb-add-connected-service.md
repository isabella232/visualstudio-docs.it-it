---
title: Aggiungere CosmosDB di Azure usando Servizi connessi | Microsoft Docs
description: Aggiungere il supporto di Azure CosmosDB all'app usando Visual Studio per aggiungere un servizio connesso
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 7bdf07824c7a06a692a81a93eaa5a0fd0536705d
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398371"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Aggiungere Azure Cosmos DB all'app usando Visual Studio Servizi connessi

Con Visual Studio, è possibile connettere uno dei seguenti elementi a Azure Cosmos DB usando la funzionalità **servizi connessi** :

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

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>Connettersi a Azure Cosmos DB tramite Servizi connessi

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **servizi connessi** e scegliere **Aggiungi servizio connesso** dal menu di scelta rapida.

1. Nella scheda **servizi connessi** selezionare l'icona + per le **dipendenze del servizio**.

    ![Aggiungi dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare **Azure Cosmos DB**.

    ![Aggiungi Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    Se non è già stato effettuato l'accesso, accedere al proprio account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita](https://azure.microsoft.com/account/free).

1. Nella schermata **Azure Cosmos DB** selezionare una Azure Cosmos DB esistente e quindi fare clic su **Avanti**.

    Se è necessario creare un database, andare al passaggio successivo. In caso contrario, andare al passaggio 7.

    ![Aggiungi Cosmos DB esistente al progetto](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. Per creare un Azure Cosmos DB:

   1. Selezionare **Crea nuovo Azure Cosmos DB** nella parte inferiore della schermata.

   1. Compilare il **Azure Cosmos DB: Crea nuova** schermata e selezionare **Crea**.

       ![Nuovo Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. Quando viene visualizzata la finestra di dialogo **configura Azure Cosmos DB** , il nuovo database viene visualizzato nell'elenco. Selezionare il nuovo database nell'elenco e fare clic su **Avanti**.

1. Immettere un nome per la stringa di connessione e scegliere se si desidera che la stringa di connessione venga archiviata in un file di segreti locali o in [Azure Key Vault](/azure/key-vault).

   ![Specificare la stringa di connessione](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. La schermata **Riepilogo modifiche** Mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sembrano OK, scegliere **fine**.

   ![Riepilogo delle modifiche](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. La connessione viene visualizzata nella sezione **dipendenze del servizio** della scheda **servizi connessi** .

   ![Dipendenze dei servizi](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Vedere anche

- [Pagina del prodotto Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)
- [Documentazione di Azure Cosmos DB](/azure/cosmos-db/)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)
