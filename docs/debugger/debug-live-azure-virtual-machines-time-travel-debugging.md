---
title: Debug di time travel live ASP.NET in una macchina virtuale di Azure
description: Informazioni su come registrare e riprodurre app live ASP.NET in macchine virtuali di Azure usando il Snapshot Debugger.
ms.custom: SEO-VS-2020
ms.date: 04/11/2019
ms.topic: how-to
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: f8aabb109de02a1beec326407472a841fe16425a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626556"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Registrare e riprodurre app ASP.NET live in macchine virtuali di Azure usando il Snapshot Debugger

L'anteprima di Time Travel Debugging (TTD) in Visual Studio Enterprise offre la possibilità di registrare un'app Web in esecuzione in una macchina virtuale di Azure e quindi ricostruire e riprodurre in modo accurato il percorso di esecuzione. TTD si integra con il Snapshot Debugger e consente di riavvolgere e riprodurre ogni riga di codice in qualsiasi numero di volte desiderato, consentendo di isolare e identificare i problemi che potrebbero verificarsi solo negli ambienti di produzione.

L'acquisizione di una registrazione TTD non arresterà l'applicazione. Tuttavia, la registrazione TDD aggiunge un sovraccarico significativo al processo in esecuzione, rallentando la registrazione in base a fattori che includono le dimensioni del processo e il numero di thread attivi.

Questa funzionalità è disponibile in anteprima per il rilascio di Visual Studio 2019 con licenza go live.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Avviare l'Snapshot Debugger con Il debug di Time Travel abilitato
> * Impostare un punto di allineamento e raccogliere una registrazione dei viaggi nel tempo
> * Avviare il debug di una registrazione dei viaggi nel tempo

## <a name="prerequisites"></a>Prerequisiti

* Il debug dei viaggi nel tempo per macchine virtuali di Azure è disponibile solo per Visual Studio 2019 Enterprise o versione successiva con il carico di lavoro sviluppo **di Azure**. (Nella scheda **Singoli componenti** in **Debug e test** > **Snapshot Debugger**.)

    Se non è già installato, installare Visual Studio [2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Il debug dei viaggi nel tempo è disponibile per le app Web delle macchine virtuali di Azure seguenti:
  * ASP.NET applicazioni (AMD64) in esecuzione in .NET Framework 4.8 o versione successiva.

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Avviare l'Snapshot Debugger con Il debug di Time Travel abilitato

1. Aprire il progetto per cui si vuole raccogliere una registrazione dei viaggi nel tempo.

    > [!IMPORTANT]
    > Per avviare TTD, è necessario aprire la *stessa versione* del codice sorgente pubblicata nel servizio VM di Azure.

1. Scegliere **Debug > Collega Snapshot Debugger...**. Selezionare la macchina virtuale di Azure in cui è distribuita l'app Web e un account di archiviazione di Azure. Selezionare **l'opzione Enable the Time Travel Debugging** preview (Abilita l'anteprima di Time Travel Debugging) e quindi fare clic su Attach **(Collega).**

      ![Selezionare la risorsa di Azure](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > La prima volta che si seleziona **Collega Snapshot Debugger** per la macchina virtuale, viene automaticamente riavviato IIS.

    I metadati per **i moduli non** vengono attivati inizialmente. Passare all'app Web e quindi **il pulsante Avvia** raccolta diventa attivo. Visual Studio è ora in modalità debug di snapshot.

   ![Modalità debug di snapshot](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > L'estensione del sito Application Insights supporta anche il debug di snapshot. Se viene visualizzato un messaggio di errore "estensione del sito non aggiornata", vedere i [suggerimenti per la risoluzione dei problemi e i problemi noti per il debug di snapshot](../debugger/debug-live-azure-apps-troubleshooting.md) per informazioni dettagliate sull'aggiornamento.

   La **finestra** Moduli mostra quando vengono caricati tutti i moduli per la macchina virtuale di Azure (scegliere Debug > Windows > **moduli** per aprire questa finestra).

   ![Controllare la finestra Moduli](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Impostare un punto di allineamento e raccogliere una registrazione dei viaggi nel tempo

1. Nell'editor di codice fare clic sul margine sinistro in un metodo a cui si è interessati per impostare un punto di allineamento. Assicurarsi che si tratti di codice che si è certi verrà eseguito.

   ![Impostare un punto di acquisizione snapshot](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Fare clic con il pulsante destro del mouse sull'icona del punto di agganciato (la palla vuota) e scegliere **Azioni**. Nella finestra **Snapshot Impostazioni** fare clic sulla casella **di controllo** Azione. Fare quindi clic sulla casella di controllo Collect a time travel trace to the end of this method (Raccogli una traccia di viaggio temporale fino **alla fine di questo metodo).**

   ![Raccogliere una traccia di viaggio temporale fino alla fine del metodo](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Fare clic su **Avvia raccolta** per attivare il punto di acquisizione snapshot.

   ![Attivare il punto di acquisizione snapshot](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Creare uno snapshot

Quando un punto di agganciato è attivato, acquisisce uno snapshot ogni volta che viene eseguita la riga di codice in cui è posizionato. Questa esecuzione può essere causata da una richiesta reale nel server. Per forzare il raggiungimento del punto di acquisizione snapshot, passare alla visualizzazione del browser del sito Web ed eseguire le eventuali azioni necessarie per raggiungere il punto di acquisizione snapshot.

## <a name="start-debugging-a-time-travel-recording"></a>Avviare il debug di una registrazione dei viaggi nel tempo

1. Quando viene raggiunto il punto di acquisizione snapshot, nella finestra Strumenti di diagnostica viene visualizzato uno snapshot. Per aprire questa finestra, scegliere **Debug > Finestre > Mostra strumenti di diagnostica**.

   ![Aprire un punto di acquisizione snapshot](../debugger/media/snapshot-diagsession-window.png)

1. Fare clic sul collegamento Visualizza snapshot per aprire la registrazione dei viaggi nel tempo nell'editor di codice.
  
   È possibile eseguire ogni riga di codice registrata dal TTD usando i pulsanti **Continua** **e Inverti continuazione.** Inoltre, la barra degli strumenti **Debug** può essere usata per visualizzare l'istruzione  **successiva,** Esegui **istruzione,** Esegui istruzione/ **Indietro.**

   ![Avvia debug](../debugger/media/time-travel-debugging-step-commands.png)

   È anche possibile usare le **finestre Variabili** locali , **Espressioni di** controllo e Stack **di** chiamate e valutare anche le espressioni.

   ![Esaminare i dati dello snapshot](../debugger/media/time-travel-debugging-start-debugging.png)

    Il sito Web stesso è ancora in tempo reale e gli utenti finali non sono influenzati da alcuna attività TTD successiva. Viene acquisito un solo snapshot per ogni punto di acquisizione snapshot per impostazione predefinita. Dopo l'acquisizione, il punto di acquisizione snapshot viene disattivato. Se si vuole acquisire un altro snapshot in corrispondenza del punto di acquisizione snapshot, è possibile riattivare il punto di acquisizione snapshot facendo clic su **Aggiorna raccolta**.

**Richiesta di assistenza** Vedere le pagine [Risoluzione dei problemi e problemi noti](../debugger/debug-live-azure-apps-troubleshooting.md) e [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.yml).

## <a name="set-a-conditional-snappoint"></a>Impostare un punto di acquisizione snapshot condizionale

Se è difficile ricreare uno stato specifico nell'app, valutare se l'uso di un punto di acquisizione snapshot condizionale può essere d'aiuto. Gli snappoint condizionali consentono di evitare di raccogliere una registrazione del viaggio temporale fino a quando l'app non entra nello stato desiderato, ad esempio quando una variabile ha un valore specifico che si vuole controllare. [È possibile impostare le condizioni usando espressioni, filtri o conteggi dei risultati.](../debugger/debug-live-azure-apps-troubleshooting.md)

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come raccogliere una registrazione dei viaggi nel tempo per macchine virtuali di Azure. È possibile leggere altre informazioni su Snapshot Debugger.

> [!div class="nextstepaction"]
> [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.yml)