---
title: Eseguire il debug di app di Azure ASP.NET attive
description: Informazioni su come impostare punti di acquisizione snapshot e visualizzare gli snapshot con Snapshot Debugger.
ms.custom: ''
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- azure
ms.openlocfilehash: f3dbd175ef5575375c314b942fedff9f77403265
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656440"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Eseguire il debug di app di Azure ASP.NET attive con Snapshot Debugger

Snapshot Debugger crea uno snapshot delle app in produzione quando viene eseguito il codice a cui si è interessati. Per indicare al debugger di creare uno snapshot, impostare punti di ancoraggio e punti di registrazione nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

I punti di acquisizione snapshot e i punti di inserimento istruzione di registrazione sono simili ai punti di interruzione, ma a differenza dei punti di interruzione, l'applicazione non viene interrotta al raggiungimento dei punti di acquisizione snapshot. L'acquisizione di uno snapshot in un punto di acquisizione snapshot richiede in genere 10-20 millisecondi.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Avviare Snapshot Debugger
> * Impostare un punto di acquisizione snapshot e visualizzare uno snapshot
> * Impostare un punto di inserimento istruzione di registrazione

## <a name="prerequisites"></a>Prerequisiti

* Snapshot Debugger è solo disponibile a partire da Visual Studio 2017 Enterprise versione 15.5 o versione successiva con il **carico di lavoro sviluppo di Azure**. (Nella scheda **Singoli componenti** in **Debug e test** > **Snapshot Debugger**.)

    ::: moniker range=">=vs-2019"
    Se non è già installato, installarlo [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Se sta aggiornando un'installazione precedente di Visual Studio, eseguire l'installazione di Visual Studio e verificare il componente Debugger di Snapshot **carico di lavoro sviluppo ASP.NET e web**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se non è già installato, installare [Visual Studio 2017 Enterprise versione 15.5](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) o versione successiva. Se si sta aggiornando un'installazione precedente di Visual Studio 2017, eseguire il programma di installazione di Visual Studio e selezionare il componente Snapshot Debugger nel **carico di lavoro Sviluppo ASP.NET e Web**.
    ::: moniker-end

* Piano di servizio app di Azure Basic o superiore.

* La raccolta di snapshot è disponibile per le seguenti app Web in esecuzione in Servizio app di Azure:
  * Applicazioni ASP.NET in esecuzione in .NET Framework 4.6.1 o versioni successive.
  * Applicazioni ASP.NET Core in esecuzione in .NET Core 2.0 o versioni successive in Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Aprire il progetto e avviare Snapshot Debugger

1. Aprire il progetto di cui si vuole eseguire il debug di snapshot.

    > [!IMPORTANT]
    > Per eseguire il debug di snapshot, è necessario aprire la *stessa versione del codice sorgente* pubblicata nel servizio app di Azure.
::: moniker range="<=vs-2017"

2. In Cloud Explorer (**Visualizza > Cloud Explorer**), fare clic con il pulsante destro del mouse sul servizio app di Azure in cui è distribuito il progetto e scegliere **Collega Snapshot Debugger**.

   ![Avviare Snapshot Debugger](../debugger/media/snapshot-launch.png)

::: moniker-end
::: moniker range=">=vs-2019"
2. Scegliere **Debug > Collega Snapshot Debugger**. Selezionare il servizio app di Azure in cui è distribuito il progetto e un account di archiviazione di Azure, quindi fare clic su **Collega**.

      ![Avviare Snapshot Debugger dal menu Debug](../debugger/media/snapshot-debug-menu-attach.png)

      ![Selezionare la risorsa di Azure](../debugger/media/snapshot-select-azure-resource-appservices.png)

::: moniker-end

  > [!IMPORTANT]
  > La prima volta che si seleziona **Collega Snapshot Debugger**, viene richiesto di installare l'estensione del sito Snapshot Debugger nel servizio app di Azure. Questa installazione richiede un riavvio del servizio app di Azure.

  > [!NOTE]
  > L'estensione del sito Application Insights supporta anche il debug di snapshot. Se viene visualizzato un messaggio di errore "estensione del sito non aggiornata", vedere i [suggerimenti per la risoluzione dei problemi e i problemi noti per il debug di snapshot](../debugger/debug-live-azure-apps-troubleshooting.md) per informazioni dettagliate sull'aggiornamento.

   Visual Studio è ora in modalità debug di snapshot.
   ![Modalità di debug snapshot](../debugger/media/snapshot-message.png)

   Nella finestra **Moduli** viene indicato quando tutti i moduli sono caricati per il servizio app di Azure (scegliere **Debug > Finestre > Moduli** per aprire questa finestra).

   ![Controllare la finestra Moduli](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Impostare un punto di acquisizione snapshot

1. Nell'editor del codice fare clic sul margine sinistro accanto a una riga di codice a cui si è interessati per impostare un punto di acquisizione snapshot. Assicurarsi che si tratti di codice che si è certi verrà eseguito.

   ![Impostare un punto di acquisizione snapshot](../debugger/media/snapshot-set-snappoint.png)

2. Fare clic su **Avvia raccolta** per attivare il punto di acquisizione snapshot.

   ![Attivare il punto di acquisizione snapshot](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Non è possibile eseguire il codice passaggio per passaggio quando si visualizza uno snapshot, ma è possibile inserire più punti di acquisizione snapshot nel codice per seguire l'esecuzione in corrispondenza di righe diverse del codice. Se il codice include più punti di acquisizione snapshot, Snapshot Debugger si assicura che gli snapshot corrispondenti provengano dalla stessa sessione dell'utente finale. Snapshot Debugger esegue questa verifica anche se l'app è usata da molti utenti.

## <a name="take-a-snapshot"></a>Acquisire uno snapshot

Quando viene attivato un punto di acquisizione snapshot, verrà acquisito uno snapshot ogni volta che viene eseguita la riga di codice in cui si trova il punto di acquisizione snapshot. L'esecuzione può essere causata da una richiesta reale nel server. Per forzare il raggiungimento del punto di acquisizione snapshot, passare alla visualizzazione del browser del sito Web ed eseguire le eventuali azioni necessarie per raggiungere il punto di acquisizione snapshot.

## <a name="inspect-snapshot-data"></a>Esaminare i dati dello snapshot

1. Quando viene raggiunto il punto di acquisizione snapshot, nella finestra Strumenti di diagnostica viene visualizzato uno snapshot. Per aprire questa finestra, scegliere **Debug > Finestre > Mostra strumenti di diagnostica**.

   ![Aprire un punto di acquisizione snapshot](../debugger/media/snapshot-diagsession-window.png)

1. Fare doppio clic sul punto di acquisizione snapshot per aprire lo snapshot nell'editor del codice.

   ![Esaminare i dati dello snapshot](../debugger/media/snapshot-inspect-data.png)

   Da questa visualizzazione, è possibile passare il mouse sulle variabili per visualizzare i suggerimenti dati, usare le finestre **Variabili locali**, **Espressioni di controllo** e **Stack di chiamate** e anche valutare le espressioni.

    Il sito Web stesso è ancora attivo e l'operazione non ha effetti sugli utenti finali. Viene acquisito un solo snapshot per ogni punto di acquisizione snapshot per impostazione predefinita. Dopo l'acquisizione, il punto di acquisizione snapshot viene disattivato. Se si vuole acquisire un altro snapshot in corrispondenza del punto di acquisizione snapshot, è possibile riattivare il punto di acquisizione snapshot facendo clic su **Aggiorna raccolta**.

È anche possibile aggiungere ulteriori punti di acquisizione snapshot all'app e attivarli con il pulsante **Aggiorna raccolta**.

**Serve aiuto?** Vedere le pagine [Risoluzione dei problemi e problemi noti](../debugger/debug-live-azure-apps-troubleshooting.md) e [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Impostare un punto di acquisizione snapshot condizionale

Se è difficile ricreare uno stato specifico nell'app, valutare se l'uso di un punto di acquisizione snapshot condizionale può essere d'aiuto. I punti di acquisizione snapshot condizionali consentono di evitare l'esecuzione di uno snapshot fino a quando l'app passa allo stato desiderato, ad esempio quando una variabile ha un valore specifico che si vuole esaminare. È possibile impostare le condizioni usando espressioni, filtri o numeri di passaggi.

#### <a name="to-create-a-conditional-snappoint"></a>Per creare un punto di acquisizione snapshot condizionale

1. Fare clic con il pulsante destro del mouse su un'icona di punto di acquisizione snapshot (la palla vuota) e scegliere **Impostazioni**.

   ![Scegliere le impostazioni](../debugger/media/snapshot-snappoint-settings.png)

1. Digitare un'espressione nella finestra Impostazioni punto di acquisizione snapshot.

   ![Digitare un'espressione](../debugger/media/snapshot-snappoint-conditions.png)

   Nella figura precedente lo snapshot viene acquisito per il punto di acquisizione snapshot solo quando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Impostare un punto di inserimento istruzione di registrazione

Oltre ad acquisire uno snapshot quando viene raggiunto un punto di acquisizione snapshot, è anche possibile configurare un punto di acquisizione snapshot per la registrazione di un messaggio, ovvero per creare un punto di inserimento istruzione di registrazione. È possibile impostare punti di inserimento istruzione di registrazione senza dover ridistribuire l'app. I punti di inserimento istruzione di registrazione vengono eseguiti in modo virtuale senza impatto o effetti collaterali sull'applicazione in esecuzione.

#### <a name="to-create-a-logpoint"></a>Per creare un punto di inserimento istruzione di registrazione

1. Fare clic con il pulsante destro del mouse su un'icona di punto di acquisizione snapshot (esagono blu) e scegliere **Impostazioni**.

1. Selezionare **Azioni** nella finestra Impostazioni punto di acquisizione snapshot.

    ![Creare un punto di inserimento istruzione di registrazione](../debugger/media/snapshot-logpoint.png)

1. Nel campo **Messaggio** è possibile immettere il nuovo messaggio di log che si vuole registrare. È anche possibile valutare le variabili nel messaggio di log, racchiudendole all'interno di parentesi graffe.

    Se si sceglie **Invia alla finestra di output**, quando viene raggiunto il punto di inserimento istruzione di registrazione, il messaggio viene visualizzato nella finestra Strumenti di diagnostica.

    ![Dati del punto di inserimento istruzione di registrazione nella finestra Strumenti di diagnostica](../debugger/media/snapshot-logpoint-output.png)

    Se si sceglie **Invia al log applicazioni**, quando viene raggiunto il punto di inserimento istruzione di registrazione, il messaggio viene visualizzato ovunque sia possibile vedere i messaggi da `System.Diagnostics.Trace` (o `ILogger` in .NET Core), ad esempio [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come usare Snapshot Debugger per i servizi app. Sono disponibili altre informazioni su questa funzionalità.

> [!div class="nextstepaction"]
> [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.md)