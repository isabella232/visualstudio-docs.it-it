---
title: Pagina iniziale per il Debugger di Snapshot
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf2aba33089623dc98a90c23166291bb2d6e7123
ms.sourcegitcommit: cdcbf254db737d42275e95de4ffc4f8c14e87e00
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57428648"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Getting Started With The Debugger Snapshot

Snapshot Debugger di Visual Studio è ora connessa al servizio, è possibile iniziare la raccolta di snapshot per facilitare il debug.

Per usare il Debugger di Snapshot, impostare alcuni punti di ancoraggio nel codice, fare clic sul pulsante per avviare la raccolta di snapshot e quindi eseguire lo scenario. Quando il codice viene eseguito in cui è stato impostato un punto di ancoraggio, viene creato uno snapshot dell'applicazione. Aprire lo snapshot, facendo clic su di essa nella finestra Strumenti di diagnostica di Visual Studio. È ora possibile eseguire il debug dello snapshot dal servizio come era locale. Per istruzioni dettagliate, continuare a leggere.

## <a name="collect-and-view-snapshots"></a>Raccogliere e visualizzare gli snapshot

Il Debugger di Snapshot raccoglie gli snapshot dall'applicazione. Gli snapshot sono come le immagini dell'Application in un punto nel tempo. Indicare a Visual Studio quando e dove raccogliere uno snapshot impostando un punto di ancoraggio nel codice. Il punto di ancoraggio, consente di impostare tutte le condizioni che è necessario assicurarsi di che ottenere uno snapshot del problema che si sta esaminando.

### <a name="set-a-snappoint"></a>Impostare un punto di ancoraggio

1. Nell'editor del codice, fare clic sulla barra di navigazione a sinistra accanto a una riga di codice che si è interessati per impostare un punto di ancoraggio. Assicurarsi che sia codice che già conosci verrà eseguito.

    ![Impostazione di un punto di ancoraggio nell'Editor](../media/snapshot-startpage-set-snappoint.png)

    Un esagono viola viene visualizzato in cui si fa clic sulla sinistra.

2. Fare clic su **Avvia raccolta** per attivare il punto di ancoraggio.

### <a name="open-a-snapshot"></a>Aprire uno Snapshot

1. Quando viene raggiunto il punto di ancoraggio, uno snapshot viene visualizzato nella finestra Strumenti di diagnostica a destra. Se non si apre la finestra, è possibile aprirlo scegliendo **Debug** > **Windows** > **Mostra strumenti di diagnostica**.

    ![Snapshot nella finestra Strumenti di diagnostica](../media/snapshot-startpage-diagsession-window.png)

2. Fare doppio clic lo snapshot per aprirlo.

### <a name="inspect-snapshot-data"></a>Esaminare i dati dello Snapshot

Da questa visualizzazione, è possibile passare il mouse sulle variabili per visualizzare i suggerimenti dati, usare le variabili locali, espressioni di controllo e chiamare Stack windows e anche valutare le espressioni.

Il sito Web stesso è ancora in tempo reale e gli utenti finali non sono interessati. Per impostazione predefinita, un solo snapshot viene acquisito per ogni punto di ancoraggio. Vale a dire, dopo che venga acquisito uno snapshot, il punto di ancoraggio viene disattivata. Se si desidera acquisire snapshot di un altro al punto di ancoraggio, è possibile attivare il punto di ancoraggio indietro facendo **Aggiorna raccolta**.

### <a name="set-a-logpoint"></a>Impostare un punto di registrazione

1. Fare doppio clic su un'icona di punto di ancoraggio (esagono viola) e scegliere **impostazioni**.

2. Nel **impostazioni punto di ancoraggio** finestra, seleziona **azioni**.

    ![Condizioni punto di ancoraggio](../media/snapshot-startpage-logpoint.png)

3. Nel **messaggio** immettere un messaggio di log che si desidera accedere. È inoltre possibile valutare le variabili nel messaggio di log, posizionandoli all'interno di parentesi graffe.

    Se si sceglie **inviare alla finestra di Output**, viene visualizzato il messaggio nella finestra Strumenti di diagnostica quando viene raggiunto il punto di registrazione.

    Se si sceglie **invia al log applicazioni**, il messaggio viene visualizzato in qualsiasi punto che è possibile visualizzare i messaggi dal `System.Diagnostics.Trace` (o `ILogger` in .NET Core), ad esempio Application Insights, quando viene raggiunto il punto di registrazione.

## <a name="learn-more"></a>Ulteriori informazioni

È possibile trovare altre informazioni sul Debugger di Snapshot sul [pagina di docs](../debug-live-azure-applications.md). Altre informazioni sull'impostazione delle condizioni per renderne più semplice individuare i bug.

## <a name="dont-show-me-this-again"></a>Non visualizzare più questo messaggio

Per non visualizzare la pagina iniziale di Debugger Snapshot nuovamente quando ci si connette il Debugger di Snapshot, modificare il **Mostra 'Attività iniziali' pagina all'avvio delle sessioni** opzione **Tools**  >   **Le opzioni** > **Snapshot Debugger**.

![Pagina delle opzioni dello strumento Debugger snapshot](../media/snapshot-startpage-tools-options.png)
