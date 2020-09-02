---
title: Pagina iniziale per il Snapshot Debugger
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf2aba33089623dc98a90c23166291bb2d6e7123
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62905260"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Introduzione con il Snapshot Debugger

Il Visual Studio Snapshot Debugger è ora connesso al servizio ed è possibile iniziare a raccogliere gli snapshot per facilitare il debug.

Per usare la Snapshot Debugger, impostare alcuni ancoraggio nel codice, fare clic sul pulsante per iniziare a raccogliere gli snapshot, quindi eseguire lo scenario. Quando viene eseguito il codice in cui è stato impostato un ancoraggio, viene creato uno snapshot dell'applicazione. Quindi aprire lo snapshot facendo clic su di esso in Visual Studio nella finestra Strumenti di diagnostica. È ora possibile eseguire il debug dello snapshot dal servizio esattamente come in locale. Per istruzioni dettagliate, continuare a leggere.

## <a name="collect-and-view-snapshots"></a>Raccogliere e visualizzare gli snapshot

Il Snapshot Debugger raccoglie gli snapshot dall'applicazione. Gli snapshot sono simili a immagini dei Application in un determinato momento. Si indica a Visual Studio quando e dove raccogliere uno snapshot impostando un ancoraggio nel codice. In ancoraggio è possibile impostare le condizioni necessarie per assicurarsi di ottenere uno snapshot del problema che si sta esaminando.

### <a name="set-a-snappoint"></a>Impostare un ancoraggio

1. Nell'editor di codice fare clic sulla barra di navigazione a sinistra accanto a una riga di codice a cui si è interessati per impostare un ancoraggio. Verificare che il codice che si conosce verrà eseguito.

    ![Impostazione di un ancoraggio nell'editor](../media/snapshot-startpage-set-snappoint.png)

    Viene visualizzato un esagono viola quando si fa clic sulla sinistra.

2. Fare clic su **Avvia raccolta** per attivare il punto di acquisizione snapshot.

### <a name="open-a-snapshot"></a>Aprire uno snapshot

1. Quando viene raggiunto il valore di ancoraggio, nella finestra Strumenti di diagnostica a destra viene visualizzato uno snapshot. Se la finestra non viene aperta, è possibile aprirla scegliendo **debug**  >  **Windows**  >  **Mostra strumenti di diagnostica**.

    ![Snapshot nella finestra di Strumenti di diagnostica](../media/snapshot-startpage-diagsession-window.png)

2. Fare doppio clic sullo snapshot per aprirlo.

### <a name="inspect-snapshot-data"></a>Controllare i dati dello snapshot

Da questa visualizzazione, è possibile passare il mouse sulle variabili per visualizzare i suggerimenti dati, usare le finestre Variabili locali, Espressioni di controllo e Stack di chiamate e anche valutare le espressioni.

Il sito Web stesso è ancora attivo e l'operazione non ha effetti sugli utenti finali. Per impostazione predefinita, viene acquisito un solo snapshot per ogni ancoraggio. Ovvero, dopo l'acquisizione di uno snapshot, il ancoraggio viene disattivato. Se si vuole acquisire un altro snapshot in corrispondenza del punto di acquisizione snapshot, è possibile riattivare il punto di acquisizione snapshot facendo clic su **Aggiorna raccolta**.

### <a name="set-a-logpoint"></a>Impostare un punto

1. Fare clic con il pulsante destro del mouse su un'icona ancoraggio (esagono viola) e scegliere **Impostazioni**.

2. Nella finestra **delle impostazioni di ancoraggio** selezionare **Actions (azioni**).

    ![Condizioni di ancoraggio](../media/snapshot-startpage-logpoint.png)

3. Nel campo **messaggio** immettere un messaggio di log che si desidera registrare. È anche possibile valutare le variabili nel messaggio di log, racchiudendole all'interno di parentesi graffe.

    Se si sceglie **Invia a finestra di output**, il messaggio viene visualizzato nella finestra di strumenti di diagnostica quando viene raggiunto il punto.

    Se si sceglie **Invia al registro applicazioni**, il messaggio viene visualizzato in qualsiasi punto in cui è possibile visualizzare i messaggi `System.Diagnostics.Trace` (o `ILogger` in .NET Core), ad esempio Application Insights, quando viene raggiunto il punto.

## <a name="learn-more"></a>Altre informazioni

Altre informazioni sul Snapshot Debugger sono disponibili nella [pagina docs](../debug-live-azure-applications.md). Altre informazioni sull'impostazione delle condizioni per semplificare la ricerca di bug.

## <a name="dont-show-me-this-again"></a>Non visualizzare più questo messaggio

Per non visualizzare più la snapshot debugger pagina iniziale quando si connette il snapshot debugger, modificare la **pagina mostra ' introduzione ' all'avvio della sessione** in **strumenti**  >  **Opzioni**  >  **snapshot debugger**.

![Pagina delle opzioni dello strumento Snapshot Debugger](../media/snapshot-startpage-tools-options.png)
