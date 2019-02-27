---
title: Il debug in tempo reale delle app di Azure ASP.NET
description: Informazioni su come impostare punti di ancoraggio e visualizzare gli snapshot con il Debugger di Snapshot.
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
ms.openlocfilehash: 89c66d0ce71a77dcfcaa6364cba6d31cf5707c4a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613375"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Il debug in tempo reale delle app di Azure ASP.NET usando il Debugger di Snapshot

Quando viene eseguito codice che si è interessati, il Debugger di Snapshot crea uno snapshot delle App nell'ambiente di produzione. Per indicare al debugger di creare uno snapshot, impostare punti di ancoraggio e punti di registrazione nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

Punti di ancoraggio e punti di registrazione sono simili ai punti di interruzione, ma a differenza dei punti di interruzione, i punti di ancoraggio non interrompere l'applicazione quando raggiunto. Acquisizione dello snapshot in un punto di ancoraggio richiede in genere, 10-20 millisecondi.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Avviare il Debugger di Snapshot
> * Impostare un punto di ancoraggio e visualizzare uno snapshot
> * Impostare un punto di registrazione

## <a name="prerequisites"></a>Prerequisiti

* Debugger di snapshot è disponibile solo per Visual Studio 2017 Enterprise versione 15.5 o versione successiva con il **carico di lavoro sviluppo di Azure**. (Sotto la **singoli componenti** scheda, disponibile in **debug e test** > **Snapshot debugger**.)

    Se non è già installato, installarlo [Visual Studio 2017 Enterprise versione 15.5](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) o versione successiva. Se sta aggiornando un'installazione precedente di Visual Studio 2017, eseguire l'installazione di Visual Studio e verificare il componente Debugger di Snapshot **carico di lavoro sviluppo ASP.NET e web**.

* Piano di servizio App di Azure Basic o superiore.

* La raccolta di snapshot è disponibile per le seguenti app Web in esecuzione in Servizio app di Azure:
  * Applicazioni ASP.NET in esecuzione in .NET Framework 4.6.1 o versioni successive.
  * Applicazioni ASP.NET Core in esecuzione in .NET Core 2.0 o versioni successive in Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Aprire il progetto e avviare il Debugger di Snapshot

1. Aprire il progetto che desidera eseguire il debug di snapshot.

    > [!IMPORTANT]
    > Eseguire il debug di snapshot, è necessario aprire la *stessa versione del codice sorgente* che viene pubblicato in servizio App di Azure.
::: moniker range="< vs-2019"

2. In Cloud Explorer (**Visualizza > Cloud Explorer**), il progetto viene distribuito il servizio App di Azure e scegliere **collegare Snapshot Debugger**.

   ![Avviare il debugger di snapshot](../debugger/media/snapshot-launch.png)

    La prima volta che si seleziona **collegare Snapshot Debugger**, viene chiesto di installare l'estensione del sito Snapshot Debugger in servizio App di Azure. Questa installazione richiede un riavvio del servizio App di Azure.

::: moniker-end
::: moniker range=">= vs-2019"
2. Collegare il Debugger di Snapshot. È possibile usare uno dei diversi metodi:

    * Scegliere **Debug > Collega Snapshot Debugger...** . Selezionare il progetto viene distribuito il servizio App di Azure e un account di archiviazione di Azure e quindi fare clic su **Attach**.

      ![Avviare il debugger di snapshot dal menu Debug](../debugger/media/snapshot-debug-menu-attach.png)

    * Fare clic con il pulsante destro sul progetto, quindi scegliere **Publish**, quindi nella pagina di pubblicazione fare clic su **collegare Snapshot Debugger**. Selezionare il progetto viene distribuito il servizio App di Azure e un account di archiviazione di Azure e quindi fare clic su **Attach**.
    ![Avviare il debugger di snapshot dalla pagina di pubblicazione](../debugger/media/snapshot-publish-attach.png)

    * In modalità di Debug dal menu a discesa di destinazione **Snapshot Debugger**, fare clic su **F5** e, se necessario seleziona il progetto viene distribuito il servizio App di Azure e un'archiviazione di Azure dell'account e quindi fare clic su  **Collegare**.
    ![Avviare il debugger di snapshot dal menu a discesa scegliere F5](../debugger/media/snapshot-F5-dropdown-attach.png)

    * Con Cloud Explorer (**Visualizza > Cloud Explorer**), fare doppio clic il progetto viene distribuito il servizio App di Azure e selezionare un account di archiviazione di Azure e quindi fare clic su **collegare Snapshot Debugger**.

      ![Avviare il debugger di snapshot di Cloud Explorer](../debugger/media/snapshot-launch.png)

    La prima volta che si seleziona **collegare Snapshot Debugger**, viene chiesto di installare l'estensione del sito Snapshot Debugger in servizio App di Azure. Questa installazione richiede un riavvio del servizio App di Azure.
::: moniker-end

   Visual Studio è ora in modalità di debug snapshot.

  > [!NOTE]
  > L'estensione del sito Application Insights supporta anche il debug di Snapshot. Se viene visualizzato un messaggio di errore "estensione aggiornata del sito", vedere [risoluzione dei problemi di suggerimenti e problemi noti per il debug di snapshot](../debugger/debug-live-azure-apps-troubleshooting.md) per l'aggiornamento dei dettagli.

   ![Modalità di debug snapshot](../debugger/media/snapshot-message.png)

   Il **moduli** finestra viene visualizzato quando tutti i moduli sono caricati per il servizio App di Azure (sceglie **Debug > Windows > moduli** per aprire questa finestra).

   ![Controllare la finestra moduli](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Impostare un punto di ancoraggio

1. Nell'editor del codice, fare clic sulla barra di navigazione a sinistra accanto a una riga di codice che si è interessati per impostare un punto di ancoraggio. Assicurarsi che sia codice che già conosci verrà eseguita.

   ![Impostare un punto di ancoraggio](../debugger/media/snapshot-set-snappoint.png)

2. Fare clic su **Avvia raccolta** per attivare il punto di ancoraggio.

   ![Attivare il punto di ancoraggio](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Non è possibile eseguire quando si visualizza un'istantanea, ma è possibile inserire più punti di ancoraggio nel codice per seguire l'esecuzione in diverse righe di codice. Se si dispone di più punti di ancoraggio nel codice, il Debugger di Snapshot garantisce che gli snapshot corrispondenti siano dalla stessa sessione dell'utente finale. Il Debugger di Snapshot avviene anche se sono presenti molti utenti raggiungere l'app.

## <a name="take-a-snapshot"></a>Acquisire uno snapshot

Quando un punto di ancoraggio è attivata, consente di acquisire uno snapshot ogni volta che viene eseguita la riga di codice in cui si trova il punto di ancoraggio. L'esecuzione può essere causata da una richiesta reale sul server. Per forzare il punto di ancoraggio per raggiungere, passare alla visualizzazione esplorazione del sito web e intraprendere eventuali azioni necessarie che provocano il punto di ancoraggio da sottoporre a hit.

## <a name="inspect-snapshot-data"></a>Esaminare i dati dello snapshot

1. Quando viene raggiunto il punto di ancoraggio, uno snapshot viene visualizzato nella finestra Strumenti di diagnostica. Per aprire questa finestra, scegliere **Debug > Windows > Mostra strumenti di diagnostica**.

   ![Aprire un punto di ancoraggio](../debugger/media/snapshot-diagsession-window.png)

1. Fare doppio clic sul punto di ancoraggio per aprire lo snapshot nell'editor del codice.

   ![Esaminare i dati dello snapshot](../debugger/media/snapshot-inspect-data.png)

   Da questa visualizzazione, è possibile passare il mouse sulle variabili per visualizzare i suggerimenti dati, utilizzare il **variabili locali**, **controlla**, e **Stack di chiamate** windows e anche valutare le espressioni.

    Il sito Web stesso è ancora in tempo reale e gli utenti finali non sono interessati. Un solo snapshot viene acquisito per ogni punto di ancoraggio per impostazione predefinita: dopo uno snapshot viene acquisito il punto di ancoraggio viene disattivata. Se si desidera acquisire snapshot di un altro al punto di ancoraggio, è possibile attivare il punto di ancoraggio indietro facendo **Aggiorna raccolta**.

È anche possibile aggiungere ulteriori punti di ancoraggio all'App e attivarli con il **Aggiorna raccolta** pulsante.

**Serve aiuto?** Vedere le [problemi noti e risoluzione dei problemi](../debugger/debug-live-azure-apps-troubleshooting.md) e [domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.md) pagine.

## <a name="set-a-conditional-snappoint"></a>Impostare un punto di ancoraggio condizionale

Se è difficile da ricreare uno stato specifico nell'app, prendere in considerazione se l'utilizzo di un punto di ancoraggio condizionale può aiutare. Punti di ancoraggio condizionale consentono di che evitare l'esecuzione di uno snapshot fino a quando l'app passa allo stato desiderato, ad esempio quando una variabile ha un valore specifico che si desidera esaminare. È possibile impostare le condizioni di utilizzo delle espressioni, filtri, o conteggio.

#### <a name="to-create-a-conditional-snappoint"></a>Per creare un punto di ancoraggio condizionale

1. Fare doppio clic su un'icona di punto di ancoraggio (la palla vuota) e scegliere **impostazioni**.

   ![Scegliere le impostazioni](../debugger/media/snapshot-snappoint-settings.png)

1. Nella finestra Impostazioni punto di ancoraggio, digitare un'espressione.

   ![Digitare un'espressione](../debugger/media/snapshot-snappoint-conditions.png)

   Nella figura precedente, viene creato lo snapshot solo per il punto di ancoraggio quando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Impostare un punto di registrazione

Oltre a eseguire uno snapshot quando viene raggiunto un punto di ancoraggio, è anche possibile configurare un punto di ancoraggio per un messaggio di log (vale a dire, creare un punto di registrazione). È possibile impostare punti di registrazione senza dover ridistribuire l'app. Punti di registrazione vengono eseguite praticamente e non causare alcun impatto o effetti collaterali all'applicazione in esecuzione.

#### <a name="to-create-a-logpoint"></a>Per creare un punto di registrazione

1. Fare doppio clic su un'icona di punto di ancoraggio (esagono blu) e scegliere **impostazioni**.

1. Nella finestra Impostazioni punto di ancoraggio, selezionare **azioni**.

    ![Creare un punto di registrazione](../debugger/media/snapshot-logpoint.png)

1. Nel **messaggio** campo, è possibile immettere il nuovo messaggio di log che si desidera registrare. È inoltre possibile valutare le variabili nel messaggio di log, posizionandoli all'interno di parentesi graffe.

    Se si sceglie **inviare alla finestra di Output**, quando viene raggiunto il punto di registrazione, verrà visualizzato il messaggio nella finestra Strumenti di diagnostica.

    ![Punto di registrazione dati nella finestra di diagsession](../debugger/media/snapshot-logpoint-output.png)

    Se si sceglie **invia al log applicazioni**, quando viene raggiunto il punto di registrazione, il messaggio viene visualizzato in qualsiasi punto che è possibile visualizzare i messaggi dal `System.Diagnostics.Trace` (o `ILogger` in .NET Core), ad esempio [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come usare il Debugger di Snapshot per i servizi App. È possibile leggere altre informazioni su questa funzionalità.

> [!div class="nextstepaction"]
> [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.md)