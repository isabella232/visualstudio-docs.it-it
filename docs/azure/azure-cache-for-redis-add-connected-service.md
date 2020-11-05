---
title: Aggiungere la cache di Azure per Redis usando Servizi connessi | Microsoft Docs
description: Aggiungere la cache di Azure per il supporto di redis all'app usando Visual Studio per aggiungere un servizio connesso
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 48554484781cca46ba96f8a075d18ea55ec3ef43
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398618"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>Aggiungere la cache di Azure per Redis usando Visual Studio Servizi connessi

Con Visual Studio, è possibile connettere una delle seguenti opzioni alla cache di Azure per Redis usando la funzionalità **servizi connessi** :

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

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>Connettersi alla cache di Azure per Redis usando Servizi connessi

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **servizi connessi** e scegliere **Aggiungi servizio connesso** dal menu di scelta rapida.

1. Nella scheda **servizi connessi** selezionare l'icona + per le **dipendenze del servizio**.

    ![Aggiungi dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare **cache di Azure per Redis**.

    ![Aggiungere la cache di Azure per Redis](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    Se non è già stato effettuato l'accesso, accedere al proprio account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita](https://azure.microsoft.com/account/free).

1. Nella schermata **configura cache di Azure per Redis** selezionare una cache di Azure esistente per Redis e quindi fare clic su **Avanti**.

    Se è necessario creare un nuovo componente, andare al passaggio successivo. In caso contrario, andare al passaggio 7.

    ![Connettersi alla cache di Azure esistente per Redis](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

1. Per creare una cache Redis di Azure:

   1. Selezionare **Crea una nuova cache Redis di Azure** nella parte inferiore della schermata.

   1. Compilare il **cache di Azure per redis: Crea nuova** schermata e selezionare **Crea**.

       ![Nuova cache di Azure per Redis](./media/azure-redis-cache-add-connected-service/create-new-azure-redis-cache.png)

   1. Quando viene visualizzata la schermata **configura cache di Azure per Redis** , la nuova cache viene visualizzata nell'elenco. Selezionare il nuovo database nell'elenco e fare clic su **Avanti**.

1. Immettere un nome per la stringa di connessione o scegliere l'impostazione predefinita e scegliere se si desidera che la stringa di connessione venga archiviata in un file dei segreti locali o in [Azure Key Vault](/azure/key-vault).

   ![Specificare la stringa di connessione](./media/azure-redis-cache-add-connected-service/connection-string.png)

1. La schermata **Riepilogo modifiche** Mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sembrano OK, scegliere **fine**.

   ![Riepilogo delle modifiche](./media/azure-redis-cache-add-connected-service/summary-of-changes.png)

1. La connessione viene visualizzata nella sezione **dipendenze del servizio** della scheda **servizi connessi** .

   ![Dipendenze dei servizi](./media/azure-redis-cache-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Vedere anche

- [Pagina del prodotto cache di Azure per Redis](https://azure.microsoft.com/services/cache)
- [Documentazione di cache di Azure per Redis](/azure/azure-cache-for-redis/)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)