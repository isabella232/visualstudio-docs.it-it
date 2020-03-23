---
title: Suggerimenti e trucchi nel debugger
description: Informazioni su alcune delle funzionalità meno note supportate dal debugger di Visual Studio
ms.custom: seodec18
ms.date: 06/15/2018
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf8d6df020694bb10fe4f3f051551056549d5673
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302217"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Scopri suggerimenti e trucchi per la produttività per il debugger in Visual StudioLearn Productivity Tips and Tricks for the Debugger in Visual Studio

Leggere questo argomento per informazioni su alcuni suggerimenti e suggerimenti sulla produttività per il debugger di Visual Studio.Read this topic to learn a learn a few productivity tips and tricks for the Visual Studio debugger. Per informazioni sulle funzionalità di base del debugger, vedere [First look at the debugger](../debugger/debugger-feature-tour.md). In questo argomento vengono illustrate alcune aree non incluse nel tour delle funzionalità.

## <a name="pin-data-tips"></a>Suggerimenti per i dati dei pin

Se si passa spesso il mouse sui suggerimenti dati durante il debug, è possibile aggiungere il suggerimento dati per la variabile per accedere rapidamente. La variabile rimane bloccata anche dopo il riavvio. Per bloccare il suggerimento dati, fare clic sull'icona a forma di puntina mentre si passa il mouse su di esso. È possibile bloccare più variabili.

![Aggiunta di un suggerimento dati](../debugger/media/dbg-tips-data-tips-pinned.png "Suggerimento Dati pinning")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Modificare il codice e continuare il debug (C

Nella maggior parte dei linguaggi supportati da Visual Studio, è possibile modificare il codice durante una sessione di debug e continuare il debug. Per utilizzare questa funzionalità, fare clic nel codice con il cursore durante la pausa nel debugger, apportare modifiche e premere **F5**, **F10**o **F11** per continuare il debug.

![Modificare e continuare il debug](../debugger/media/dbg-tips-edit-and-continue.gif "ModificaAndContinua")

Per ulteriori informazioni sull'utilizzo della funzionalità e sulle limitazioni delle funzionalità, vedere [Modifica e continuazione](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Modificare il codice XAML e continuare il debug

Per modificare il codice XAML durante una sessione di debug, vedere [Scrivere ed eseguire il debug di codice XAML in esecuzione con XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Problemi di debug difficili da riprodurre

Se è difficile o dispendioso in termini di tempo ricreare un determinato stato nell'app, valuta se l'uso di un punto di interruzione condizionale può essere utile. Puoi usare [punti di interruzione condizionali](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) e filtrare i punti di interruzione per evitare di entrare nel codice dell'app finché l'app non raggiunge lo stato desiderato, ad esempio uno stato in cui una variabile archivia dati non valida. È possibile impostare le condizioni utilizzando espressioni, filtri, conteggi dei riscontri e così via.

#### <a name="to-create-a-conditional-breakpoint"></a>Per creare un punto di interruzione condizionaleTo create a conditional breakpoint

1. Fate clic con il pulsante destro del mouse sull'icona di un punto di interruzione (la sfera rossa) e scegliete **Condizioni**.

2. Nella finestra **Impostazioni punto di interruzione** digitare un'espressione.

    ![Punto di interruzione condizionaleConditional Breakpoint](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Se si è interessati a un altro tipo di condizione, selezionare **Filtro** anziché **Espressione condizionale** nella finestra di dialogo Impostazioni punto di **interruzione** e quindi seguire i suggerimenti per il filtro.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Configurare i dati da visualizzare nel debugger

Per c'è, Visual Basic e C , (solo per il codice C/CLI), è possibile indicare al debugger le informazioni da visualizzare utilizzando l'attributo [DebuggerDisplay.](../debugger/using-the-debuggerdisplay-attribute.md) Per il codice di C, è possibile eseguire la stessa operazione utilizzando [le visualizzazioni Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

Con il debugger in pausa su una riga di codice, utilizzare il mouse per afferrare il puntatore a freccia gialla a sinistra. Spostare il puntatore a freccia gialla in un punto diverso nel percorso di esecuzione del codice. Quindi si usa F5 o un comando di passaggio per continuare l'esecuzione dell'app.

![Spostare il puntatore di esecuzione](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Spostare il puntatore di esecuzione")

Modificando il flusso di esecuzione è possibile eseguire operazioni come testare percorsi di esecuzione del codice diversi o rieseguire il codice senza riavviare il debugger.

> [!WARNING]
> Spesso questa funzionalità deve essere usata con attenzione. Nella descrizione comando viene visualizzato un avviso. È anche possibile che vengano visualizzati altri avvisi. Lo spostamento del puntatore non può ripristinare l'app a uno stato dell'applicazione precedente.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Tenere traccia di un oggetto esterno all'ambito (C, Visual Basic)

È facile visualizzare le variabili utilizzando le finestre del debugger come la finestra **Espressioni di controllo.** Tuttavia, quando una variabile esce dall'ambito nella finestra **Espressioni** di controllo, è possibile notare che è disattivata. In alcuni scenari di app, il valore di una variabile può cambiare anche quando la variabile non rientra nell'ambito e potrebbe essere necessario guardarla attentamente (ad esempio, una variabile potrebbe ottenere la procedura di Garbage Collection). È possibile tenere traccia della variabile creando un ID oggetto per essa nella finestra **Espressioni di controllo.**

#### <a name="to-create-an-object-id"></a>Per creare un ID oggetto

1. Impostare un punto di interruzione accanto a una variabile di cui si desidera tenere traccia.

2. Avviare il debugger (**F5**) e arrestarsi in corrispondenza del punto di interruzione.

3. Individuare la variabile nella finestra **Variabili locali** **(Debug > Windows > Variabili locali**), fare clic con il pulsante destro del mouse sulla variabile e scegliere Crea ID **oggetto**.

    ![Creare un ID oggetto](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. Dovresti vedere **$** un più un numero nella finestra **Variabili locali.** Questa variabile è l'ID oggetto.

5. Fare clic con il pulsante destro del mouse sulla variabile ID oggetto e scegliere **Aggiungi controllo**.

Per ulteriori informazioni, consultate [Creare un ID oggetto.](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)

## <a name="view-return-values-for-functions"></a>Visualizzare i valori restituiti per le funzioniView return values for functions

Per visualizzare i valori **restituiti** per le funzioni, esaminare le funzioni visualizzate nella finestra Auto durante l'esecuzione del codice. Per visualizzare il valore restituito per una funzione, assicurarsi che la funzione desiderata sia già stata eseguita (premere **F10** una volta se si è attualmente arrestati nella chiamata di funzione). Se la finestra è chiusa, utilizzare **Debug > Windows > Auto** per aprire la finestra **Auto.**

![Finestra Auto](../debugger/media/dbg-tips-autos-window.png "Finestra di comando AutosWindow")

Inoltre, è possibile immettere funzioni nella finestra **Immediata** per visualizzare i valori restituiti. (Aprirlo utilizzando **Debug > Windows > Controllo immediato**.)

![Finestra di controllo immediato](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow (Finestra Immediata)")

È inoltre possibile utilizzare [pseudovariabili](../debugger/pseudovariables.md) nella finestra `$ReturnValue`Espressioni **di** controllo e Controllo **immediato,** ad esempio .

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Esaminare le stringhe in un visualizzatoreInspect strings in a visualizer

Quando si lavora con le stringhe, può essere utile visualizzare l'intera stringa formattata. Per visualizzare una stringa di testo normale, XML, HTML o JSON, fare clic sull'icona della lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icona del visualizzatore") passando il mouse su una variabile contenente un valore stringa.

![Aprire un visualizzatore di stringheOpen a String Visualizer](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualizzatore di stringhe può aiutare a scoprire se una stringa è in formato non corretto, a seconda del tipo di stringa. Ad esempio, un campo **Valore** vuoto indica che la stringa non è riconosciuta dal tipo di visualizzatore. Per ulteriori informazioni, vedere Finestra di [dialogo Visualizzatore di stringhe](../debugger/string-visualizer-dialog-box.md).

![Visualizzatore di stringhe JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Per alcuni altri tipi, ad esempio DataSet e DataTable oggetti visualizzati nelle finestre del debugger, è anche possibile aprire un visualizzatore incorporato.

## <a name="break-into-code-on-handled-exceptions"></a>Suddividere il codice nelle eccezioni gestite

Il debugger interrompe il codice per le eccezioni non gestite. Tuttavia, le eccezioni gestite (ad `try/catch` esempio le eccezioni che si verificano all'interno di un blocco) possono anche essere un'origine di bug e si consiglia di analizzare quando si verificano. È possibile configurare il debugger in modo che interrompa il codice anche per le eccezioni gestite configurando le opzioni nella finestra di dialogo **Impostazioni eccezione.** Aprire questa finestra di dialogo scegliendo **Debug > Impostazioni eccezioni di Windows >**.

La finestra di dialogo **Impostazioni eccezione** consente di indicare al debugger di interrompere il codice in base a eccezioni specifiche. Nell'illustrazione seguente, il debugger interrompe `System.NullReferenceException` il codice ogni volta che si verifica un errore. Per ulteriori informazioni, vedere [Gestione delle eccezioni](../debugger/managing-exceptions-with-the-debugger.md).

![Finestra di dialogo Impostazioni eccezione](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox (Finestra di dialogo su ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Debug di deadlock e race condition

Se è necessario eseguire il debug dei tipi di problemi comuni alle app multithreading, spesso è utile visualizzare la posizione dei thread durante il debug. È possibile farlo facilmente utilizzando il **pulsante Mostra thread nell'origine.**

#### <a name="to-show-threads-in-your-source-code"></a>Per visualizzare i thread nel codice sorgenteTo show threads in your source code

1. Durante il debug, fare clic sul pulsante **Mostra thread nell'origine** nella barra degli strumenti Debug.While debugging, click the Show Threads in Source button ![Show Threads in Source](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") in the **Debug** toolbar.

2. All'estrema sinistra della finestra, In questa riga, viene visualizzata un'icona *del marcatore del thread* Marker di ![filettatura](../debugger/media/dbg-thread-marker.png "ThreadMarker") simile a due thread di tessuto. Il marcatore del thread indica l'interruzione di un thread in questa posizione.

    Si noti che un marcatore di thread può essere parzialmente nascosto da un punto di interruzione.

3. Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati. in cui è indicato il nome e il numero ID di ciascun thread interrotto.

    È inoltre possibile visualizzare la posizione dei thread nella [finestra Stack in parallelo](../debugger/get-started-debugging-multithreaded-apps.md).

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Esaminare i payload per i servizi Web e le risorse di rete (UWP)Examine payloads for web services and network resources (UWP)

Nelle app UWP è possibile analizzare `Windows.Web.Http` le operazioni di rete eseguite tramite l'API. È possibile utilizzare questo strumento per facilitare il debug dei servizi Web e delle risorse di rete. Per utilizzare lo strumento, selezionare **Debug > Performance Profiler**. Selezionare **Rete**, quindi scegliere **Avvia**. Nell'applicazione seguire lo scenario che usa `Windows.Web.Http` e quindi scegliere **Arresta raccolta** per generare il report.

![Strumento di profilatura dell'utilizzo della rete](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool (strumento Di rete)")

Selezionare un'operazione nella visualizzazione di riepilogo per visualizzare altri dettagli.

![Informazioni dettagliate nello strumento Utilizzo rete](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Per altre informazioni, vedere [Utilizzo della rete](../profiling/network-usage.md).
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>Acquisire maggiore familiarità con la modalità di connessione del debugger all'app in C, in C, in Visual Basic, in Questo modo

Per connettersi all'app in esecuzione, il debugger carica i file di simboli (con estensione pdb) generati per la stessa build dell'app di cui si sta tentando di eseguire il debug. In alcuni scenari, può essere utile una piccola conoscenza dei file di simboli. È possibile esaminare il modo in cui Visual Studio carica i file di simboli utilizzando la finestra **Moduli.You** can examine how Visual Studio loads symbol files using the Modules window.

Aprire la finestra **Moduli** durante il debug selezionando **Debug > moduli > di Windows**. La finestra **Moduli** può indicare quali moduli il debugger considera come codice utente, o [*Codice Personale,*](../debugger/just-my-code.md)e lo stato di caricamento del simbolo per il modulo. Nella maggior parte degli scenari, il debugger trova automaticamente i file di simboli per il codice utente, ma se si desidera eseguire il codice .NET, il codice di sistema o il codice della libreria di terze parti, sono necessari passaggi aggiuntivi per ottenere i file di simboli corretti.

![Visualizzare le informazioni sui simboli nella finestra Moduli](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

È possibile caricare le informazioni sui simboli direttamente dalla finestra **Moduli** facendo clic con il pulsante destro del mouse e scegliendo **Carica simboli**.

A volte, gli sviluppatori di app forniscono app senza i file di simboli corrispondenti (per ridurre l'impronta), ma conservano una copia dei file di simboli corrispondenti per la compilazione in modo che possano eseguire il debug di una versione rilasciata in un secondo momento.

Per scoprire in che modo il debugger classifica il codice come codice utente, vedere [Just My Code](../debugger/just-my-code.md). Per ulteriori informazioni sui file di simboli, vedere Specificare i [file di simboli (con estensione pdb) e](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)i file di origine nel debugger di Visual Studio .

## <a name="learn-more"></a>Altre informazioni

Per ulteriori suggerimenti e suggerimenti e informazioni più dettagliate, vedere questi post di blog:

- [7 hack meno noti per il debug in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 gemme nascoste in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Vedere anche

[Tasti di scelta rapida](../ide/productivity-shortcuts.md)
