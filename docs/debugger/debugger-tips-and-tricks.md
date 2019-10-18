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
ms.openlocfilehash: 92d1c327c168bfd2881ad014b7f9ab87f771b95d
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72536070"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Informazioni sui suggerimenti per la produttività per il debugger in Visual Studio

Leggere questo argomento per apprendere alcuni suggerimenti e trucchi per la produttività per il debugger di Visual Studio. Per informazioni sulle funzionalità di base del debugger, vedere [la prima occhiata al debugger](../debugger/debugger-feature-tour.md). In questo argomento vengono illustrate alcune aree che non sono incluse nella presentazione delle funzionalità.

## <a name="pin-data-tips"></a>Aggiungere suggerimenti sui dati

Se si passa spesso il mouse sui suggerimenti dati durante il debug, potrebbe essere necessario aggiungere il suggerimento dati per la variabile per consentire l'accesso rapido. La variabile rimane bloccata anche dopo il riavvio. Per aggiungere il suggerimento dati, fare clic sull'icona Aggiungi mentre si posiziona il puntatore del mouse su di essa. È possibile aggiungere più variabili.

![Aggiunta di un suggerimento dati](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Modificare il codice e continuare il debugC#(, VB C++,)

Nella maggior parte dei linguaggi supportati da Visual Studio, è possibile modificare il codice nel corso di una sessione di debug e continuare il debug. Per usare questa funzionalità, fare clic sul codice con il cursore mentre è in pausa nel debugger, apportare modifiche e premere **F5**, **F10**o **F11** per continuare il debug.

![Debug di modifica e continuazione](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Per ulteriori informazioni sull'utilizzo della funzionalità e sulle limitazioni delle funzionalità, vedere [modifica e continuazione](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Modificare il codice XAML e continuare il debug

Per modificare il codice XAML durante una sessione di debug, vedere [scrivere ed eseguire il debug di codice XAML in esecuzione con il ricaricamento a caldo di XAML](xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Problemi di debug difficili da riprodurre

Se è difficile o dispendioso in termini di tempo per ricreare un determinato stato nell'app, valutare se l'uso di un punto di interruzione condizionale può essere utile. È possibile usare punti di interruzione [condizionali](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) e filtrare i punti di interruzione per evitare di suddividere il codice dell'app fino a quando l'app non entra in uno stato desiderato, ad esempio uno stato in cui una variabile archivia dati non validi. È possibile impostare le condizioni usando espressioni, filtri, conteggi dei passaggi e così via.

#### <a name="to-create-a-conditional-breakpoint"></a>Per creare un punto di interruzione condizionale

1. Fare clic con il pulsante destro del mouse sull'icona di un punto di interruzione (palla rossa) e scegliere **condizioni**.

2. Nella finestra **Impostazioni** del punto di interruzione digitare un'espressione.

    ![Punto di interruzione condizionale](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Se si è interessati a un altro tipo di condizione, selezionare **filtro** anziché **espressione condizionale** nella finestra di dialogo impostazioni punto di **interruzione** e quindi seguire i suggerimenti per il filtro.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Configurare i dati da visualizzare nel debugger

Per C#, Visual Basic e C++ (C++solo codice/CLI), è possibile indicare al debugger quali informazioni visualizzare utilizzando l'attributo [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) . Per C++ il codice, è possibile eseguire la stessa operazione usando le [visualizzazioni Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

Con il debugger sospeso in una riga di codice, usare il mouse per estrarre il puntatore a freccia gialla a sinistra. Spostare il puntatore della freccia gialla in un punto diverso nel percorso di esecuzione del codice. Si usa quindi F5 o un comando Step per continuare a eseguire l'app.

![Spostare il puntatore di esecuzione](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Spostare il puntatore di esecuzione")

Modificando il flusso di esecuzione è possibile eseguire operazioni come testare percorsi di esecuzione del codice diversi o rieseguire il codice senza riavviare il debugger.

> [!WARNING]
> Spesso questa funzionalità deve essere usata con attenzione. Nella descrizione comando viene visualizzato un avviso. È anche possibile che vengano visualizzati altri avvisi. Lo stato di un puntatore non può ripristinare lo stato precedente dell'applicazione.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Rilevare un oggetto esterno all'ambito (C#, Visual Basic)

È facile visualizzare le variabili usando le finestre del debugger come la finestra **espressioni di controllo** . Tuttavia, quando una variabile esce dall'ambito nella finestra **espressioni di controllo** , è possibile notare che è disabilitata. In alcuni scenari di app, il valore di una variabile può variare anche quando la variabile è fuori dall'ambito e può essere utile osservarla attentamente (ad esempio, una variabile può essere sottoposta a Garbage Collection). È possibile tenere traccia della variabile creando un ID oggetto nella finestra espressioni di **controllo** .

#### <a name="to-create-an-object-id"></a>Per creare un ID oggetto

1. Impostare un punto di interruzione accanto a una variabile che si desidera rilevare.

2. Avviare il debugger (**F5**) e arrestarsi in corrispondenza del punto di interruzione.

3. Trovare la variabile nella finestra variabili **locali** (**debug > impostazioni locali di Windows >** ), fare clic con il pulsante destro del mouse sulla variabile e scegliere **Crea ID oggetto**.

    ![Creare un ID oggetto](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. Nella finestra **$** verrà visualizzato il simbolo **Variabili locali** . Questa variabile è l'ID oggetto.

5. Fare clic con il pulsante destro del mouse sulla variabile ID oggetto e scegliere Aggiungi espressione di **controllo**.

Per ulteriori informazioni, vedere la pagina relativa alla [creazione di un ID oggetto](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Visualizzare i valori restituiti per le funzioni

Per visualizzare i valori restituiti per le funzioni, esaminare le funzioni visualizzate nella finestra **auto** durante l'esecuzione del codice. Per visualizzare il valore restituito per una funzione, assicurarsi che la funzione a cui si è interessati sia già stata eseguita (premere **F10** una volta se la chiamata di funzione è stata arrestata). Se la finestra è chiusa, utilizzare **Debug > Windows > auto** per aprire la finestra **auto** .

![Finestra auto](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Inoltre, è possibile immettere le funzioni nella finestra di **controllo immediato** per visualizzare i valori restituiti. Aprirlo utilizzando **Debug > Windows > immediato**.

![Finestra di controllo immediato](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

È anche possibile usare [pseudo variabili riportate](../debugger/pseudovariables.md) nella finestra **espressioni** di controllo e **controllo immediato** , ad esempio `$ReturnValue`.

## <a name="string_visualizer"></a>Controllare le stringhe in un visualizzatore

Quando si utilizzano le stringhe, può essere utile visualizzare l'intera stringa formattata. Per visualizzare una stringa di testo normale, XML, HTML o JSON, fare clic sull'icona della lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icona del Visualizzatore") mentre si posiziona il puntatore del mouse su una variabile contenente un valore stringa.

![Apre un visualizzatore di stringhe](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualizzatore di stringhe può essere utile per determinare se una stringa non è in formato corretto, a seconda del tipo di stringa. Ad esempio, un campo **valore** vuoto indica che la stringa non è riconosciuta dal tipo del visualizzatore. Per altre informazioni, vedere [finestra di dialogo Visualizzatore stringhe](../debugger/string-visualizer-dialog-box.md).

![Visualizzatore stringhe JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Per altri tipi, ad esempio oggetti DataSet e DataTable, che vengono visualizzati nelle finestre del debugger, è anche possibile aprire un visualizzatore incorporato.

## <a name="break-into-code-on-handled-exceptions"></a>Interrompi nel codice per le eccezioni gestite

Il debugger interrompe il codice in corrispondenza di eccezioni non gestite. Tuttavia, le eccezioni gestite, ad esempio le eccezioni che si verificano all'interno di un blocco di `try/catch`, possono anche essere un'origine di bug e potrebbe essere necessario analizzare quando si verificano. È possibile configurare il debugger per l'interruzione nel codice anche per le eccezioni gestite configurando le opzioni nella finestra di dialogo **Impostazioni eccezioni** . Aprire questa finestra di dialogo scegliendo **Debug > Windows > impostazioni eccezioni**.

La finestra di dialogo **Impostazioni eccezioni** consente di indicare al debugger di suddividere il codice in base a eccezioni specifiche. Nell'illustrazione seguente il debugger interrompe il codice ogni volta che si verifica un `System.NullReferenceException`. Per ulteriori informazioni, vedere [gestione delle eccezioni](../debugger/managing-exceptions-with-the-debugger.md).

![Finestra di dialogo Impostazioni eccezioni](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Eseguire il debug di deadlock e race condition

Se è necessario eseguire il debug dei tipi di problemi comuni alle app multithreading, spesso consente di visualizzare il percorso dei thread durante il debug. Questa operazione può essere eseguita facilmente usando il pulsante **Mostra thread nel codice sorgente** .

#### <a name="to-show-threads-in-your-source-code"></a>Per visualizzare i thread nel codice sorgente

1. Durante il debug, fare clic sul pulsante **Mostra thread nel codice sorgente** ![Mostra thread nell'origine](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") nella barra degli strumenti **debug** .

2. All'estrema sinistra della finestra, In questa riga viene visualizzato un ![marcatore di thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") icona *indicatore di thread* simile a due thread di tela. Il marcatore del thread indica l'interruzione di un thread in questa posizione.

    Si noti che un marcatore di thread può essere parzialmente nascosto da un punto di interruzione.

3. Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati. in cui è indicato il nome e il numero ID di ciascun thread interrotto.

    È anche possibile visualizzare il percorso dei thread nella [finestra stack in parallelo](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Esaminare i payload per i servizi Web e le risorse di rete (UWP)

Nelle app UWP è possibile analizzare le operazioni di rete eseguite con l'API `Windows.Web.Http`. È possibile utilizzare questo strumento per facilitare il debug di servizi Web e risorse di rete. Per usare lo strumento, selezionare **Debug > Profiler prestazioni**. Selezionare **rete**, quindi fare clic su **Avvia**. Nell'applicazione seguire lo scenario che usa `Windows.Web.Http` e quindi scegliere **Arresta raccolta** per generare il report.

![Strumento di profilatura utilizzo rete](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Selezionare un'operazione nella visualizzazione di riepilogo per visualizzare altri dettagli.

![Informazioni dettagliate nello strumento utilizzo rete](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Per altre informazioni, vedere [Utilizzo della rete](../profiling/network-usage.md).

## <a name="modules_window"></a>Acquisire familiarità con le modalità di connessione del debugger all'app (C#, C++, Visual Basic, F#)

Per connettersi all'app in esecuzione, il debugger carica i file di simboli (con estensione pdb) generati per la stessa build dell'app di cui si sta provando a eseguire il debug. In alcuni scenari, può essere utile una conoscenza minima dei file di simboli. È possibile esaminare il modo in cui Visual Studio carica i file di simboli usando la finestra **moduli** .

Aprire la finestra **moduli** durante il debug selezionando **debug > moduli > di Windows**. La finestra **moduli** consente di indicare quali moduli il debugger sta trattando come codice utente, [*codice personale*](../debugger/just-my-code.md)e lo stato di caricamento dei simboli per il modulo. Nella maggior parte degli scenari, il debugger trova automaticamente i file di simboli per il codice utente, ma se si desidera eseguire un'istruzione (o eseguire il debug) del codice .NET, del codice di sistema o del codice della libreria di terze parti, è necessario eseguire passaggi aggiuntivi per ottenere i file di simboli corretti.

![Visualizzare le informazioni sui simboli nella finestra moduli](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

È possibile caricare le informazioni sui simboli direttamente dalla finestra **moduli** facendo clic con il pulsante destro del mouse e scegliendo **Carica simboli**.

A volte, gli sviluppatori di app spedito app senza i file di simboli corrispondenti (per ridurre il footprint), conservando però una copia dei file di simboli corrispondenti per la compilazione in modo che possano eseguire il debug di una versione rilasciata in un secondo momento.

Per informazioni sul modo in cui il debugger classifica il codice come codice utente, vedere [Just My Code](../debugger/just-my-code.md). Per altre informazioni sui file di simboli, vedere [specificare i file di simboli (con estensione pdb) e di origine nel debugger di Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Altre informazioni

Per ulteriori suggerimenti e consigli e informazioni più dettagliate, vedere i post di Blog seguenti:

- [7 hacker meno noti per il debug in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 gemme nascoste in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Vedere anche

[Tasti di scelta rapida](../ide/productivity-shortcuts.md)
