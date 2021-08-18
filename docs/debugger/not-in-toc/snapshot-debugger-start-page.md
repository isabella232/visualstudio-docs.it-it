---
description: La Visual Studio Snapshot Debugger è ora connessa al servizio ed è possibile iniziare a raccogliere snapshot per facilitare il debug.
title: Pagina iniziale per il Snapshot Debugger
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2aa185a0f9bb59661670bb80970ec967dc9ea30e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090577"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Attività iniziali con il Snapshot Debugger

La Visual Studio Snapshot Debugger è ora connessa al servizio ed è possibile iniziare a raccogliere snapshot per facilitare il debug.

Per usare il Snapshot Debugger, impostare alcuni punti di allineamento nel codice, fare clic sul pulsante per iniziare a raccogliere gli snapshot e quindi eseguire lo scenario. Quando viene eseguito il codice in cui è stato impostato un punto di allineamento, viene creato uno snapshot dell'applicazione. Aprire quindi lo snapshot facendo clic su di esso Visual Studio nella finestra Strumenti di diagnostica. È ora possibile eseguire il debug dello snapshot dal servizio come se fosse locale. Per istruzioni dettagliate, continuare a leggere.

## <a name="collect-and-view-snapshots"></a>Raccogliere e visualizzare gli snapshot

Il Snapshot Debugger raccoglie snapshot dall'applicazione. Gli snapshot sono come immagini dell'appication in un momento nel tempo. È possibile Visual Studio quando e dove raccogliere uno snapshot impostando un punto di allineamento nel codice. Nel punto di allineamento è possibile impostare tutte le condizioni necessarie per assicurarsi di ottenere uno snapshot del problema che si sta analizzando.

### <a name="set-a-snappoint"></a>Impostare un punto di allineamento

1. Nell'editor di codice fare clic sul margine sinistro accanto a una riga di codice a cui si è interessati per impostare un punto di allineamento. Assicurarsi che sia il codice che si sa che verrà eseguito.

    ![Impostazione di un punto di allineamento nell'editor](../media/snapshot-startpage-set-snappoint.png)

    Nel punto in cui si fa clic a sinistra viene visualizzato un esagono viola.

2. Fare clic su **Avvia raccolta** per attivare il punto di acquisizione snapshot.

### <a name="open-a-snapshot"></a>Aprire uno snapshot

1. Quando viene raggiunto il punto di agganciato, nella finestra Strumenti di diagnostica a destra viene visualizzato uno snapshot. Se la finestra non si apre, è possibile aprirla scegliendo Debug Windows  >    >  **Mostra Strumenti di diagnostica**.

    ![Snapshot nella finestra Strumenti di diagnostica](../media/snapshot-startpage-diagsession-window.png)

2. Fare doppio clic su uno snapshot per aprirlo.

### <a name="inspect-snapshot-data"></a>Esaminare i dati dello snapshot

Da questa visualizzazione, è possibile passare il mouse sulle variabili per visualizzare i suggerimenti dati, usare le finestre Variabili locali, Espressioni di controllo e Stack di chiamate e anche valutare le espressioni.

Il sito Web stesso è ancora attivo e l'operazione non ha effetti sugli utenti finali. Per impostazione predefinita, viene acquisito un solo snapshot per ogni punto di snap. Ciò significa che, dopo l'acquisizione di uno snapshot, il punto di agganciamento si disattiva. Se si vuole acquisire un altro snapshot in corrispondenza del punto di acquisizione snapshot, è possibile riattivare il punto di acquisizione snapshot facendo clic su **Aggiorna raccolta**.

### <a name="set-a-logpoint"></a>Impostare un punto di log

1. Fare clic con il pulsante destro del mouse sull'icona di un punto di allineamento (l'esagono viola) e **scegliere Impostazioni**.

2. Nella finestra **Snappoint Impostazioni** selezionare **Azioni**.

    ![Condizioni del punto di allineamento](../media/snapshot-startpage-logpoint.png)

3. Nel campo **Messaggio** immettere un messaggio di log da registrare. È anche possibile valutare le variabili nel messaggio di log, racchiudendole all'interno di parentesi graffe.

    Se si sceglie **Invia a Finestra di output**, il messaggio viene visualizzato nella finestra Strumenti di diagnostica quando viene raggiunto il punto di log.

    Se si sceglie Invia al **log** applicazioni , il messaggio viene visualizzato ovunque sia possibile visualizzare i messaggi da `System.Diagnostics.Trace` (o in .NET Core), ad esempio App Insights, quando viene raggiunto il `ILogger` punto di log.

## <a name="learn-more"></a>Altre informazioni

È possibile trovare altre informazioni sulla Snapshot Debugger nella [pagina della documentazione](../debug-live-azure-applications.md). Altre informazioni sull'impostazione delle condizioni per semplificare l'individuazione dei bug.

## <a name="dont-show-me-this-again"></a>Non visualizzare più questo messaggio

Per non visualizzare mai più la pagina start Snapshot Debugger quando si connette il Snapshot Debugger, modificare l'opzione Mostra **pagina "Attività iniziali"** all'avvio della sessione **in** Strumenti Opzioni  >    >  **Snapshot Debugger**.

![Snapshot Debugger opzione Strumento di configurazione](../media/snapshot-startpage-tools-options.png)
