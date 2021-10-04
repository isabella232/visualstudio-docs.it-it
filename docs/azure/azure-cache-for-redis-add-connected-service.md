---
title: Aggiungere cache di Azure per Redis usando Servizi connessi | Microsoft Docs
description: Aggiungere cache di Azure per Redis all'app usando il Visual Studio per aggiungere un servizio connesso
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: a8c234db5d9b0f003fa269def46b8c3fcc3da164
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129430713"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>Aggiungere cache di Azure per Redis usando Visual Studio Servizi connessi

Con Visual Studio, è possibile connettere uno degli elementi seguenti a cache di Azure per Redis usando la **Servizi connessi** funzionalità:

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

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>Connessione usare cache di Azure per Redis Servizi connessi

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni** fare clic con il pulsante destro **del** mouse sul nodo Servizi connessi e scegliere Aggiungi servizio connesso dal menu di **scelta rapida.**

1. Nella scheda **Servizi connessi** selezionare l'icona + per **Dipendenze servizio**.

    ![Aggiungere una dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare **cache di Azure per Redis**.

    ![Aggiungere la cache di Azure per Redis](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    Se non è già stato eseguito l'accesso, accedere all'account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita.](https://azure.microsoft.com/free/)

1. Nella schermata **Configura cache di Azure per Redis** selezionare un'cache di Azure per Redis esistente e selezionare **Avanti.**

    Se è necessario creare un nuovo componente, andare al passaggio successivo. In caso contrario, andare al passaggio 7.

    ![Connessione alle impostazioni cache di Azure per Redis](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

1. Per creare una Cache Redis di Azure:

   1. Selezionare **Crea una nuova cache Redis** di Azure nella parte inferiore della schermata.

   1. Compilare la **cache di Azure per Redis: Crea nuova** schermata e selezionare **Crea**.

       ![Nuovo cache di Azure per Redis](./media/azure-redis-cache-add-connected-service/create-new-azure-redis-cache.png)

   1. Quando viene **visualizzata la schermata Configura** cache di Azure per Redis, la nuova cache viene visualizzata nell'elenco. Selezionare il nuovo database nell'elenco e selezionare **Avanti.**

1. Immettere un nome di stringa di connessione o scegliere il valore predefinito e scegliere se archiviare la stringa di connessione in un file di segreti locale o in [Azure Key Vault](/azure/key-vault).

   ![Specificare la stringa di connessione](./media/azure-redis-cache-add-connected-service/connection-string.png)

1. La **schermata Riepilogo delle** modifiche mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sembrano OK, scegliere **Fine**.

   ![Riepilogo delle modifiche](./media/azure-redis-cache-add-connected-service/summary-of-changes.png)

1. La connessione viene visualizzata nella **sezione Dipendenze** servizio della **scheda** Servizi connessi connessione.

   ![Dipendenze dei servizi](./media/azure-redis-cache-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Vedi anche

- [cache di Azure per Redis prodotto](https://azure.microsoft.com/services/cache)
- [cache di Azure per Redis documentazione](/azure/azure-cache-for-redis/)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)
