---
title: Tempo di esecuzione del debug di macchine virtuali ASP.NET di Azure in tempo reale
description: Informazioni su come registrare e riprodurre app ASP.NET in tempo reale in macchine virtuali di Azure usando il Snapshot Debugger.
ms.custom: ''
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
ms.openlocfilehash: a44ecd7faeb3ec4cea7665678050580d7e4063a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350628"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Registrare e riprodurre app ASP.NET in tempo reale in macchine virtuali di Azure usando il Snapshot Debugger

L'anteprima TTD (Time Travel Debugging) in Visual Studio Enterprise offre la possibilità di registrare un'app Web in esecuzione in una macchina virtuale (VM) di Azure e quindi di ricostruire e riprodurre accuratamente il percorso di esecuzione. TTD si integra con il Snapshot Debugger e consente di riavvolgere e riprodurre ogni riga di codice un numero qualsiasi di volte, consentendo di isolare e identificare i problemi che potrebbero verificarsi solo negli ambienti di produzione.

L'acquisizione di una registrazione TTD non interrompe l'applicazione. Tuttavia, la registrazione TDD aggiunge un sovraccarico significativo al processo in esecuzione, rallentando in base ai fattori che includono le dimensioni del processo e il numero di thread attivi.

Questa funzionalità è disponibile in anteprima per il rilascio di Visual Studio 2019 con una licenza Go Live.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Avviare il Snapshot Debugger con il debug Time Travel abilitato
> * Impostare un ancoraggio e raccogliere una registrazione del viaggio temporale
> * Avviare il debug di una registrazione del viaggio temporale

## <a name="prerequisites"></a>Prerequisiti

* Il debug del viaggio in tempo per le macchine virtuali di Azure è disponibile solo per Visual Studio 2019 Enterprise o versione successiva con il **carico di lavoro sviluppo di Azure**. (Nella scheda **Singoli componenti** in **Debug e test** > **Snapshot Debugger**.)

    Se non è già installato, installare [Visual Studio 2019 Enterprise Edition](https://visualstudio.microsoft.com/vs/).

* Il debug di Travel Time è disponibile per le app Web della macchina virtuale di Azure seguenti:
  * ASP.NET Applications (AMD64) in esecuzione in .NET Framework 4,8 o versione successiva.

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Avviare il Snapshot Debugger con il debug Time Travel abilitato

1. Aprire il progetto per cui si vuole raccogliere una registrazione del viaggio temporale.

    > [!IMPORTANT]
    > Per avviare TTD, è necessario aprire la *stessa versione del codice sorgente* pubblicata nel servizio VM di Azure.

1. Scegliere **Debug > connetti snapshot debugger...**. Selezionare la macchina virtuale di Azure in cui viene distribuita l'app Web e un account di archiviazione di Azure. Selezionare l'opzione **Abilita l'anteprima del debug in fase di spostamento** e quindi fare clic su **Connetti**.

      ![Selezionare la risorsa di Azure](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > La prima volta che si seleziona **Collega Snapshot Debugger** per la macchina virtuale, viene automaticamente riavviato IIS.

    I metadati per i **moduli** non vengono inizialmente attivati. Passare all'app Web e il pulsante **Avvia raccolta** diventa attivo. Visual Studio è ora in modalità debug di snapshot.

   ![Modalità debug di snapshot](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > L'estensione del sito Application Insights supporta anche il debug di snapshot. Se viene visualizzato un messaggio di errore "estensione del sito non aggiornata", vedere i [suggerimenti per la risoluzione dei problemi e i problemi noti per il debug di snapshot](../debugger/debug-live-azure-apps-troubleshooting.md) per informazioni dettagliate sull'aggiornamento.

   La finestra **moduli** indica quando vengono caricati tutti i moduli per la macchina virtuale di Azure. scegliere **debug > moduli di Windows >** per aprire questa finestra.

   ![Controllare la finestra Moduli](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Impostare un ancoraggio e raccogliere una registrazione del viaggio temporale

1. Nell'editor di codice fare clic sulla barra di navigazione a sinistra in un metodo a cui si è interessati per impostare un ancoraggio. Assicurarsi che si tratti di codice che si è certi verrà eseguito.

   ![Impostare un punto di acquisizione snapshot](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Fare clic con il pulsante destro del mouse sull'icona ancoraggio (la palla vuota) e scegliere **azioni**. Nella finestra **Impostazioni snapshot** fare clic sulla casella di controllo **azione** . Fare quindi clic sulla casella di controllo **Collect a Time Travel Trace fino alla fine di questo metodo** .

   ![Raccogliere una traccia di spostamento temporale alla fine del metodo](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Fare clic su **Avvia raccolta** per attivare il punto di acquisizione snapshot.

   ![Attivare il punto di acquisizione snapshot](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Creare uno snapshot

Quando un ancoraggio è attivato, acquisisce uno snapshot ogni volta che viene eseguita la riga di codice in cui viene inserito il ancoraggio. Questa esecuzione può essere causata da una reale richiesta sul server. Per forzare il raggiungimento del punto di acquisizione snapshot, passare alla visualizzazione del browser del sito Web ed eseguire le eventuali azioni necessarie per raggiungere il punto di acquisizione snapshot.

## <a name="start-debugging-a-time-travel-recording"></a>Avviare il debug di una registrazione del viaggio temporale

1. Quando viene raggiunto il punto di acquisizione snapshot, nella finestra Strumenti di diagnostica viene visualizzato uno snapshot. Per aprire questa finestra, scegliere **Debug > Finestre > Mostra strumenti di diagnostica**.

   ![Aprire un punto di acquisizione snapshot](../debugger/media/snapshot-diagsession-window.png)

1. Fare clic sul collegamento Visualizza snapshot per aprire la registrazione dell'ora di spostamento nell'editor di codice.
  
   È possibile eseguire tutte le righe di codice registrate da TTD usando i pulsanti **continua** e **continua** . Inoltre, è possibile usare la barra degli strumenti **debug** per **visualizzare l'istruzione successiva**, **Esegui**istruzione, **Esegui istruzione/** routine, Esci **da**istruzione/routine **, Esegui istruzione** **/routine**, Esegui il **backup.**

   ![Avvia debug](../debugger/media/time-travel-debugging-step-commands.png)

   È anche possibile usare le finestre **variabili locali**, **orologi**e **stack di chiamate** e valutare anche le espressioni.

   ![Esaminare i dati dello snapshot](../debugger/media/time-travel-debugging-start-debugging.png)

    Il sito Web stesso è ancora Live e gli utenti finali non sono interessati da alcuna attività TTD successiva. Viene acquisito un solo snapshot per ogni punto di acquisizione snapshot per impostazione predefinita. Dopo l'acquisizione, il punto di acquisizione snapshot viene disattivato. Se si vuole acquisire un altro snapshot in corrispondenza del punto di acquisizione snapshot, è possibile riattivare il punto di acquisizione snapshot facendo clic su **Aggiorna raccolta**.

**Richiesta di assistenza** Vedere le pagine [Risoluzione dei problemi e problemi noti](../debugger/debug-live-azure-apps-troubleshooting.md) e [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Impostare un punto di acquisizione snapshot condizionale

Se è difficile ricreare uno stato specifico nell'app, valutare se l'uso di un punto di acquisizione snapshot condizionale può essere d'aiuto. Ancoraggio condizionali consentono di evitare la raccolta di una registrazione del viaggio temporale fino a quando l'app entra in uno stato desiderato, ad esempio quando una variabile ha un determinato valore che si vuole ispezionare. [È possibile impostare condizioni usando espressioni, filtri o conteggi di passaggi](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come raccogliere una registrazione del viaggio temporale per le macchine virtuali di Azure. È possibile leggere altre informazioni su Snapshot Debugger.

> [!div class="nextstepaction"]
> [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.md)