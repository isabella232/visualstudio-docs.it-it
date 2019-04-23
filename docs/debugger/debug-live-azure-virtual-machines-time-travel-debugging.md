---
title: Ora il debug di viaggio in tempo reale ASP.NET macchine virtuali di Azure
description: Informazioni su come registrare e riprodurre le app ASP.NET in tempo reale su macchine virtuali di Azure usando il Debugger di Snapshot.
ms.custom: ''
ms.date: 04/11/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: d392e19bb51cd981cc833535556eb083e8e5ba07
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672504"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Registrare e riprodurre in tempo reale delle App ASP.NET in macchine virtuali di Azure usando il Debugger di Snapshot

L'anteprima di debug Travel ora (TTD) in Visual Studio Enterprise offre la possibilità di registrare un'app Web in esecuzione in una macchina virtuale di Azure (VM) in modo accurato ricostruire e riprodurre il percorso di esecuzione. TTD si integra con il Debugger di Snapshot di offerta e consente di riavvolgere e riprodurre ogni riga di codice tuttavia molte volte si desidera, consentono di isolare e identificare i problemi che potrebbero verificarsi solo in ambienti di produzione.

Acquisire una registrazione TTD non interromperà l'applicazione, tuttavia, la registrazione verrà aggiunto un overhead significativo per il processo in esecuzione, rallentano le prestazioni base fattori che includono la dimensione del processo e il numero di thread attivi.

Questa funzionalità è disponibile in anteprima per la versione di Visual Studio 2019 con una licenza di andare in tempo reale.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Avviare il Debugger di Snapshot con il tempo Travel debug abilitato
> * Impostare un punto di ancoraggio e raccogliere una registrazione cronologicamente
> * Avviare il debug di una registrazione cronologicamente

## <a name="prerequisites"></a>Prerequisiti

* Debug di viaggio Time per le macchine virtuali (VM) di Azure è disponibile solo per Visual Studio 2019 Enterprise o superiore con il **carico di lavoro sviluppo di Azure**. (Nella scheda **Singoli componenti** in **Debug e test** > **Snapshot Debugger**.)

    Se non è già installato, installarlo [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Debug in fase di trasferimento è disponibile per le app web di macchina virtuale di Azure seguenti:
  * Applicazioni ASP.NET (AMD64) in esecuzione in .NET Framework 4.8 o versione successiva.

## <a name="open-your-project-and-start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Aprire il progetto e avviare il Debugger di Snapshot con il tempo Travel debug abilitato

1. Aprire il progetto che si vuole raccogliere una registrazione cronologicamente.

    > [!IMPORTANT]
    > Per avviare TTD, è necessario aprire la *stessa versione del codice sorgente* che viene pubblicato nel servizio macchine Virtuali di Azure.

1. Scegliere **Debug > Collega Snapshot Debugger**. Selezionare macchina virtuale di Azure viene distribuito l'app web e un account di archiviazione di Azure. Selezionare il **abilitare il debug in fase di viaggio** opzione di anteprima e quindi fare clic su **Attach**.

      ![Selezionare la risorsa di Azure](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > La prima volta che si seleziona **Collega Snapshot Debugger** per la macchina virtuale, viene automaticamente riavviato IIS.

    I metadati per i **moduli** non verranno inizialmente attivati. Passare all'app Web e il pulsante **Avvia raccolta** diventerà attivo. Visual Studio è ora in modalità debug di snapshot.

   ![Modalità debug di snapshot](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > L'estensione del sito Application Insights supporta anche il debug di snapshot. Se viene visualizzato un messaggio di errore "estensione del sito non aggiornata", vedere i [suggerimenti per la risoluzione dei problemi e i problemi noti per il debug di snapshot](../debugger/debug-live-azure-apps-troubleshooting.md) per informazioni dettagliate sull'aggiornamento.

   Il **moduli** finestra viene visualizzato quando tutti i moduli sono caricati per la macchina virtuale di Azure (sceglie **Debug > Windows > moduli** per aprire questa finestra).

   ![Controllare la finestra Moduli](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Impostare un punto di ancoraggio e raccogliere una registrazione cronologicamente

1. Nell'editor del codice, fare clic sulla barra di navigazione a sinistra in un metodo che si è interessati per impostare un punto di ancoraggio. Assicurarsi che si tratti di codice che si è certi verrà eseguito.

   ![Impostare un punto di acquisizione snapshot](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Fare doppio clic sull'icona di punto di ancoraggio (la palla vuota) e scegliere **azioni**. Nella finestra Snapshot impostazioni scegliere la **azione** casella di controllo. Scegliere il **raccogliere una traccia di viaggio tempo alla fine di questo metodo** casella di controllo.

   ![Raccogliere una traccia di viaggio tempo alla fine del metodo](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Fare clic su **Avvia raccolta** per attivare il punto di acquisizione snapshot.

   ![Attivare il punto di acquisizione snapshot](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Acquisire uno snapshot

Quando viene attivato un punto di acquisizione snapshot, verrà acquisito uno snapshot ogni volta che viene eseguita la riga di codice in cui si trova il punto di acquisizione snapshot. L'esecuzione può essere causata da una richiesta reale nel server. Per forzare il raggiungimento del punto di acquisizione snapshot, passare alla visualizzazione del browser del sito Web ed eseguire le eventuali azioni necessarie per raggiungere il punto di acquisizione snapshot.

## <a name="start-debugging-a-time-travel-recording"></a>Avviare il debug di una registrazione cronologicamente

1. Quando viene raggiunto il punto di acquisizione snapshot, nella finestra Strumenti di diagnostica viene visualizzato uno snapshot. Per aprire questa finestra, scegliere **Debug > Finestre > Mostra strumenti di diagnostica**.

   ![Aprire un punto di acquisizione snapshot](../debugger/media/snapshot-diagsession-window.png)

1. Fare clic sul collegamento Visualizza lo Snapshot per aprire il viaggio di tempo nell'editor del codice di registrazione.
  
   È possibile eseguire tutte le righe di codice registrato per il TTD usando il **continuazione** e **invertire continuare** pulsanti. Inoltre la barra degli strumenti Debug può essere usato per **Mostra istruzione successiva**, **Esegui istruzione**, **Esegui istruzione/routine**, **Esci**,  **Eseguire nuovamente**, **passa Indietro**, **un passo indietro**.

   ![Avvia debug](../debugger/media/time-travel-debugging-step-commands.png)

   È anche possibile usare la **variabili locali**, **controlla**, e **Stack di chiamate** windows e anche valutare le espressioni.

   ![Esaminare i dati dello snapshot](../debugger/media/time-travel-debugging-start-debugging.png)

    Il sito Web stesso è ancora in tempo reale e gli utenti finali non sono interessati da tutte le attività successive TTD. Viene acquisito un solo snapshot per ogni punto di acquisizione snapshot per impostazione predefinita. Dopo l'acquisizione, il punto di acquisizione snapshot viene disattivato. Se si vuole acquisire un altro snapshot in corrispondenza del punto di acquisizione snapshot, è possibile riattivare il punto di acquisizione snapshot facendo clic su **Aggiorna raccolta**.

**Serve aiuto?** Vedere le pagine [Risoluzione dei problemi e problemi noti](../debugger/debug-live-azure-apps-troubleshooting.md) e [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Impostare un punto di acquisizione snapshot condizionale

Se è difficile ricreare uno stato specifico nell'app, valutare se l'uso di un punto di acquisizione snapshot condizionale può essere d'aiuto. Punti di ancoraggio condizionale consentono di che evitare la raccolta di un viaggio ora la registrazione fino a quando l'app passa allo stato desiderato, ad esempio quando una variabile ha un valore specifico che si desidera esaminare. [È possibile impostare le condizioni di utilizzo delle espressioni, filtri, o conteggio](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come raccogliere una registrazione cronologicamente per le macchine virtuali di Azure. È possibile leggere altre informazioni sul Debugger di Snapshot.

> [!div class="nextstepaction"]
> [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.md)