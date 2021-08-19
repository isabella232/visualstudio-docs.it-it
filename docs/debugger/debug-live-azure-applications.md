---
title: Eseguire il debug di app di Azure ASP.NET attive
titleSuffix: Visual Studio Enterprise
description: Informazioni su come usare il Snapshot Debugger in Visual Studio per impostare punti di agganciamenti ed eseguire snapshot durante il debug in tempo ASP.NET applicazioni Azure.
ms.custom: ''
ms.date: 03/16/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 288c13dbf249bfe953f46886cc55dee6e1408515
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090953"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Eseguire il debug di app di Azure ASP.NET attive con Snapshot Debugger

Snapshot Debugger crea uno snapshot delle app in produzione quando viene eseguito il codice a cui si è interessati. Per indicare al debugger di creare uno snapshot, impostare punti di ancoraggio e punti di registrazione nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

I punti di acquisizione snapshot e i punti di inserimento istruzione di registrazione sono simili ai punti di interruzione, ma a differenza dei punti di interruzione, l'applicazione non viene interrotta al raggiungimento dei punti di acquisizione snapshot. L'acquisizione di uno snapshot in un punto di acquisizione snapshot richiede in genere 10-20 millisecondi.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Avviare Snapshot Debugger
> * Impostare un punto di acquisizione snapshot e visualizzare uno snapshot
> * Impostare un punto di inserimento istruzione di registrazione

## <a name="prerequisites"></a>Prerequisiti

* Snapshot Debugger è disponibile solo a partire da Visual Studio 2017 Enterprise versione 15.5 o successiva con il carico di lavoro Sviluppo **di Azure.** (Nella scheda **Singoli componenti** in **Debug e test** > **Snapshot Debugger**.)

   ::: moniker range=">=vs-2019"
   Se non è già installato, installare Visual Studio [2019.](https://visualstudio.microsoft.com/downloads) Se si esegue l'aggiornamento da un'installazione Visual Studio precedente, eseguire il Programma di installazione di Visual Studio e controllare il componente Snapshot Debugger nel carico di lavoro sviluppo ASP.NET **web.**
   ::: moniker-end
   ::: moniker range="<=vs-2017"
   Se non è già installato, installare [Visual Studio 2017 Enterprise versione 15.5](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) o versione successiva. Se si esegue l'aggiornamento da un'installazione di Visual Studio 2017 precedente, eseguire il Programma di installazione di Visual Studio e controllare il componente Snapshot Debugger nel carico di lavoro ASP.NET e **sviluppo** Web .
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

2. Scegliere **Debug > Collega Snapshot Debugger...**. Selezionare il Servizio app di Azure in cui viene distribuito il progetto e un account di archiviazione di Azure e quindi fare clic su **Collega.** Snapshot Debugger supporta anche i set [servizio Azure Kubernetes](debug-live-azure-kubernetes.md) macchine virtuali [di Azure e & di scalabilità di macchine virtuali.](debug-live-azure-virtual-machines.md)

   ![Avviare Snapshot Debugger dal menu Debug](../debugger/media/snapshot-debug-menu-attach.png)

   ![Selezionare la risorsa di Azure](../debugger/media/snapshot-select-azure-resource-appservices.png)

::: moniker-end

   > [!IMPORTANT]
   > La prima volta che si seleziona **Collega Snapshot Debugger**, viene richiesto di installare l'estensione del sito Snapshot Debugger nel servizio app di Azure. Questa installazione richiede un riavvio del servizio app di Azure.

   ::: moniker range="<=vs-2017"
   > [!NOTE]
   > L'estensione del sito Application Insights supporta anche il debug di snapshot. Se viene visualizzato un messaggio di errore "Estensione del sito non aggiornata", vedere i suggerimenti per la risoluzione dei problemi e i problemi noti per il [debug degli snapshot](../debugger/debug-live-azure-apps-troubleshooting.md) per informazioni dettagliate sull'aggiornamento.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   > [!NOTE]
   > (Visual Studio 2019 versione 16.2 e successive) Snapshot Debugger ha abilitato il supporto cloud di Azure. Assicurarsi che sia la risorsa di Azure che Archiviazione di Azure'account selezionato siano nello stesso cloud. Per domande sulle configurazioni di conformità di Azure dell'organizzazione, contattare [l'amministratore di Azure.](https://azure.microsoft.com/overview/trusted-cloud/)
   ::: moniker-end

   Visual Studio è ora in modalità debug di snapshot.
   ![Modalità di debug degli snapshot](../debugger/media/snapshot-message.png)

   Nella finestra **Moduli** viene indicato quando tutti i moduli sono caricati per il servizio app di Azure (scegliere **Debug > Finestre > Moduli** per aprire questa finestra).

   ![Controllare la finestra Moduli](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Impostare un punto di acquisizione snapshot

1. Nell'editor di codice fare clic sulla barra di spostamento sinistra accanto a una riga di codice a cui si è interessati per impostare un punto di allineamento. Assicurarsi che sia il codice che verrà eseguito.

   ![Impostare un punto di acquisizione snapshot](../debugger/media/snapshot-set-snappoint.png)

2. Fare clic su **Avvia raccolta** per attivare il punto di acquisizione snapshot.

   ![Attivare il punto di acquisizione snapshot](../debugger/media/snapshot-start-collection.png)

   > [!TIP]
   > Non è possibile eseguire il codice passaggio per passaggio quando si visualizza uno snapshot, ma è possibile inserire più punti di acquisizione snapshot nel codice per seguire l'esecuzione in corrispondenza di righe diverse del codice. Se il codice include più punti di acquisizione snapshot, Snapshot Debugger si assicura che gli snapshot corrispondenti provengano dalla stessa sessione dell'utente finale. Snapshot Debugger esegue questa verifica anche se l'app è usata da molti utenti.

## <a name="take-a-snapshot"></a>Creare uno snapshot

Dopo aver impostato un punto di agganciato, è possibile generare manualmente uno snapshot dalla visualizzazione del browser del sito Web ed eseguendo la riga di codice contrassegnata o attendere che gli utenti ne generino uno dall'utilizzo del sito.

## <a name="inspect-snapshot-data"></a>Esaminare i dati dello snapshot

1. Quando viene raggiunto il punto di acquisizione snapshot, nella finestra Strumenti di diagnostica viene visualizzato uno snapshot. Per aprire questa finestra, scegliere **Debug > Finestre > Mostra strumenti di diagnostica**.

   ![Aprire un punto di acquisizione snapshot](../debugger/media/snapshot-diagsession-window.png)

1. Fare doppio clic sul punto di acquisizione snapshot per aprire lo snapshot nell'editor del codice.

   ![Esaminare i dati dello snapshot](../debugger/media/snapshot-inspect-data.png)

   Da questa visualizzazione, è possibile passare il mouse sulle variabili per visualizzare i suggerimenti dati, usare le finestre **Variabili locali**, **Espressioni di controllo** e **Stack di chiamate** e anche valutare le espressioni.

   Il sito Web è ancora live e gli utenti finali non sono interessati. Viene acquisito un solo snapshot per ogni punto di acquisizione snapshot per impostazione predefinita. Dopo l'acquisizione, il punto di acquisizione snapshot viene disattivato. Se si vuole acquisire un altro snapshot in corrispondenza del punto di acquisizione snapshot, è possibile riattivare il punto di acquisizione snapshot facendo clic su **Aggiorna raccolta**.

È anche possibile aggiungere ulteriori punti di acquisizione snapshot all'app e attivarli con il pulsante **Aggiorna raccolta**.

**Richiesta di assistenza** Vedere le pagine [Risoluzione dei problemi e problemi noti](../debugger/debug-live-azure-apps-troubleshooting.md) e [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.yml).

## <a name="set-a-conditional-snappoint"></a>Impostare un punto di acquisizione snapshot condizionale

Se è difficile ricreare uno stato specifico nell'app, è consigliabile usare un punto di agganciato condizionale. Gli snappoint condizionali consentono di controllare quando creare uno snapshot, ad esempio quando una variabile contiene un determinato valore che si vuole controllare. È possibile impostare le condizioni usando espressioni, filtri o numeri di passaggi.

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
> [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.yml)