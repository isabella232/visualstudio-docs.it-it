---
title: Suggerimenti e consigli nel debugger
description: Informazioni su alcune delle funzionalità meno conosciute supportata dal debugger di Visual Studio
ms.custom: seodec18
ms.date: 06/15/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 238236df48adab491cd8a1f9282a8f6a440c5321
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055225"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Informazioni su consigli e suggerimenti relativi alla produttività per il Debugger di Visual Studio

Leggere questo argomento per informazioni su alcuni suggerimenti per la produttività e consigli per il debugger di Visual Studio. Per esaminare le funzionalità di base del debugger, vedere [Debugger Feature Tour](../debugger/debugger-feature-tour.md). In questo argomento illustra alcune aree che non sono inclusi nella presentazione funzionalità.

## <a name="pin-data-tips"></a>Suggerimenti dati pin

Se si passa spesso sui suggerimenti per i dati durante il debug, è possibile aggiungere il suggerimento dati per la variabile aumentare l'accesso rapido. La variabile rimane bloccata anche dopo il riavvio. Per bloccare il suggerimento dati, fare clic sull'icona della puntina al passaggio del mouse su di esso. È possibile aggiungere più variabili.

![L'aggiunta di un suggerimento dati](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Modificare il codice e continuare il debug (C#, VB, C++)

Nella maggior parte dei linguaggi supportati da Visual Studio, è possibile modificare il codice all'interno di una sessione di debug e continuare il debug. Per usare questa funzionalità, fare clic nel codice con il cursore durante la pausa del debugger, apportare modifiche e premere **F5**, **F10**, o **F11** per continuare il debug.

![Modificare e continuare il debug](../debugger/media/dbg-tips-edit-and-continue.gif "/EDITANDCONTINUE")

Per altre informazioni sull'uso della funzionalità e sulle limitazioni di funzionalità, vedere [modifica e continuazione](../debugger/edit-and-continue.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Il debug dei problemi che sono difficili da riprodurre

Se è difficile o che richiedono molto tempo ricreare uno stato specifico nell'app, prendere in considerazione se consentono l'uso di un punto di interruzione condizionale. È possibile usare [punti di interruzione condizionali](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) e filtrare i punti di interruzione per evitare l'interruzione nel codice dell'app fino a quando l'app passa allo stato desiderato (ad esempio uno stato in cui una variabile è l'archiviazione dei dati non validi). È possibile impostare le condizioni tramite espressioni, filtri, conteggio e così via.

#### <a name="to-create-a-conditional-breakpoint"></a>Per creare un punto di interruzione condizionale

1. Fare doppio clic su un'icona di punto di interruzione (la palla di colore rosso) e scegliere **condizioni**.

2. Nel **impostazioni punto di interruzione** finestra, digitare un'espressione.

    ![Punto di interruzione condizionale](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Se è interessati a un altro tipo di condizione, selezionare **filtro** invece di **espressione condizionale** nel **impostazioni punto di interruzione** nella finestra di dialogo e quindi seguire le suggerimenti di filtro.

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

Con il debugger sospeso su una riga di codice, utilizzare il mouse per trascinare il puntatore sulla freccia gialla a sinistra. Spostare il puntatore sulla freccia gialla in un altro punto nel percorso di esecuzione del codice. Per continuare a eseguire l'app è usare F5 o un comando di esecuzione.

![Spostare il puntatore di esecuzione](../debugger/media/dbg-tour-move-the-execution-pointer.gif "spostare il puntatore di esecuzione")

Modificando il flusso di esecuzione è possibile eseguire operazioni come testare percorsi di esecuzione del codice diversi o rieseguire il codice senza riavviare il debugger.

> [!WARNING]
> Spesso questa funzionalità deve essere usata con attenzione. Nella descrizione comando viene visualizzato un avviso. È anche possibile che vengano visualizzati altri avvisi. Spostare il puntatore del mouse non è possibile ripristinare l'app a uno stato precedente dell'applicazione.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Tenere traccia di un oggetto out-of-scope (C#, Visual Basic)

È facile visualizzare le variabili usando finestre del debugger, ad esempio la **Watch** finestra. Tuttavia, quando una variabile esce dall'ambito nel **Watch** finestra, è possibile notare che è disattivato. In alcuni scenari di app, il valore di una variabile può cambiare anche quando la variabile esula dall'ambito, e si potrebbe voler guardala strettamente (ad esempio, una variabile venga sottoposto a garbage collection). È possibile monitorare la variabile tramite la creazione di un ID oggetto corrispondente nei **Watch** finestra.

#### <a name="to-create-an-object-id"></a>Per creare un ID di oggetto

1.  Impostare un punto di interruzione in prossimità di una variabile che si vuole tenere traccia.

2.  Avviare il debugger (**F5**) e interrompere nel punto di interruzione.

3. Trovare la variabile nel **variabili locali** finestra (**Debug > Windows > variabili locali**), la variabile e scegliere **Crea ID oggetto**.

    ![Creare un ID di oggetto](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  Nella finestra **$** verrà visualizzato il simbolo **Variabili locali** . Questa variabile è l'ID oggetto.
  
5.  Fare doppio clic la variabile dell'ID oggetto e scegli **Aggiungi espressione di controllo**.

Per altre informazioni, vedere [creare un ID di oggetto](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Visualizzare i valori restituiti per le funzioni

Per visualizzare i valori restituiti per le funzioni, esaminare le funzioni che vengono visualizzati nei **Auto** finestra mentre eseguono le istruzioni del codice. Per visualizzare il valore restituito per una funzione, assicurarsi che la funzione si è interessati è già stata eseguita (premere **F10** once se è attualmente interrotto alla chiamata di funzione). Se la finestra viene chiusa, usare **Debug > Windows > Auto** per aprire il **Auto** finestra.

![Finestra Auto](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Inoltre, è possibile immettere le funzioni nel **Immediate** finestra per visualizzare i valori restituiti. (Aprirlo utilizzando **Debug > Windows > controllo immediato**.)

![Finestra di controllo immediato](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

È anche possibile usare [pseudo variabili](../debugger/pseudovariables.md) nel **Watch** e **controllo immediato** finestra, ad esempio `$ReturnValue`.

## <a name="string_visualizer"></a>Esaminare le stringhe in un visualizzatore

Quando si usano le stringhe, può essere utile visualizzare l'intera stringa formattata. Per visualizzare un testo normale, una stringa XML, HTML o JSON, fare clic sull'icona della lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icona Visualizzatore") al passaggio del mouse su una variabile che contiene un valore stringa.

![Aprire un visualizzatore di stringhe](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualizzatore di stringhe può aiutare a determinare se una stringa è in formato non corretto, a seconda del tipo stringa. Ad esempio, uno spazio vuoto **valore** campo indica la stringa non è riconosciuta per il tipo del visualizzatore. Per altre informazioni, vedere [dialogo Visualizzatore stringhe](../debugger/string-visualizer-dialog-box.md).

![Visualizzatore di stringhe JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Per alcuni altri tipi, ad esempio gli oggetti WPF visualizzati nelle finestre del debugger, è anche possibile aprire i visualizzatori.

## <a name="break-into-code-on-handled-exceptions"></a>Inserire un'interruzione nel codice in corrispondenza di eccezioni gestite

Il debugger si interrompe nel codice su eccezioni non gestite. Tuttavia, gestite le eccezioni (ad esempio le eccezioni che si verificano all'interno di un `try/catch` blocco) può anche essere fonte di bug e si potrebbe voler conoscere quando si verificano. È possibile configurare il debugger per inserire un'interruzione nel codice per le eccezioni gestite tramite la configurazione di opzioni nel **impostazioni eccezioni** nella finestra di dialogo. Aprire la finestra di dialogo scegliendo **Debug > Windows > Impostazioni eccezioni**.

Il **impostazioni eccezioni** nella finestra di dialogo consente di indicare al debugger di inserire un'interruzione nel codice per eccezioni specifiche. Nell'illustrazione seguente, il debugger si interrompe nel codice ogni volta che un `System.NullReferenceException` si verifica. Per altre informazioni, vedere [la gestione delle eccezioni](../debugger/managing-exceptions-with-the-debugger.md).

![Finestra di dialogo Impostazioni eccezioni](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Eseguire il debug di deadlock e race condition

Se è necessario eseguire il debug di tipi di problemi comuni per le app a thread multipli, è spesso utile per visualizzare la posizione dei thread durante il debug. È possibile farlo facilmente usando le **Mostra thread nell'origine** pulsante.

#### <a name="to-show-threads-in-your-source-code"></a>Per visualizzare i thread nel codice sorgente

1.  Durante il debug, fare clic sui **Mostra thread nell'origine** pulsante ![Mostra thread nell'origine](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") nel **Debug** sulla barra degli strumenti.
  
2.  All'estrema sinistra della finestra, In questa riga, viene visualizzato un *marcatore del thread* icona ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") che due fili. Il marcatore del thread indica l'interruzione di un thread in questa posizione.

    Si noti che un marcatore del thread potrebbe essere parzialmente nascosta da un punto di interruzione.
  
3.  Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati. in cui è indicato il nome e il numero ID di ciascun thread interrotto.

    È anche possibile visualizzare il percorso del thread dei [finestra Stack in parallelo](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Esaminare i payload dei servizi web e le risorse di rete (UWP)

Nelle App UWP, è possibile analizzare le operazioni di rete eseguite con la `Windows.Web.Http` API. È possibile utilizzare questo strumento per facilitare il debug dei servizi web e le risorse di rete. Per usare lo strumento, selezionare **Debug > Profiler prestazioni**. Selezionare **Network**, quindi scegliere **avviare**. Nell'applicazione seguire lo scenario che usa `Windows.Web.Http` e quindi scegliere **Arresta raccolta** per generare il report.

![Utilizzo dello strumento di profilatura della rete](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Selezionare un'operazione nella visualizzazione di riepilogo per visualizzare altri dettagli.

![Informazioni dettagliate nello strumento utilizzo della rete](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Per altre informazioni, vedere [Utilizzo della rete](../profiling/network-usage.md).

## <a name="modules_window"></a> Acquisire familiarità con la modalità con cui il debugger si connette all'App (C#, C++, Visual Basic, F#)

Per collegare all'App in esecuzione, il debugger carica i file di simboli (PDB) generati per la stessa build dell'app che si sta tentando di eseguire il debug. In alcuni scenari, può essere utile conoscenza dei file di simboli. È possibile esaminare come Visual Studio carica il file di simboli tramite il **moduli** finestra.

Aprire il **moduli** finestra durante il debug, selezionando **Debug > Windows > moduli**. Il **moduli** finestra può indicare quali moduli il debugger è trattare come codice utente, o [ *My Code*](../debugger/just-my-code.md)e il simbolo di caricamento dello stato per il modulo. Nella maggior parte degli scenari, il debugger individua automaticamente i file di simboli per il codice utente, ma se si desidera eseguire l'istruzione (o eseguire il debug) codice .NET framework, codice di sistema o il codice della libreria di terze parti, sono necessari passaggi aggiuntivi per ottenere i file di simboli corretto.

![Visualizzare le informazioni sui simboli nella finestra di moduli](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

È possibile caricare le informazioni sui simboli direttamente dai **moduli** finestra facendo clic e scegliendo **Carica simboli**.

In alcuni casi, gli sviluppatori di app invia l'App senza i corrispondente file di simboli (per ridurre il footprint), ma tenere una copia del simbolo corrisponda file per la compilazione in modo che possono eseguire il debug una versione rilasciata in un secondo momento.

Per scoprire come il debugger consente di classificare il codice come codice utente, vedere [Just My Code](../debugger/just-my-code.md). Per altre informazioni sui file di simboli, vedere [specifica simboli (PDB) e i file di origine nel debugger di Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Altre informazioni

Per altri suggerimenti e consigli e informazioni più dettagliate, vedere questi post di blog:

- [7 HACK noti minori per il debug in Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 strumenti utili nascosti in Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Vedere anche
[Tasti di scelta rapida](../ide/tips-and-tricks-for-visual-studio.md)
