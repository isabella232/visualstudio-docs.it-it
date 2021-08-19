---
title: Suggerimenti e consigli nel debugger
description: Informazioni su alcune delle funzionalità meno note supportate dal debugger Visual Studio
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 55beb1375dd4f1befa8a18ee404dbc2b0e10d0f8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081018"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Informazioni su Suggerimenti e consigli per il debugger in Visual Studio

Leggere questo argomento per ottenere alcuni suggerimenti e consigli per la produttività per il debugger Visual Studio. Per informazioni sulle funzionalità di base del debugger, vedere [Prima di tutto il debugger.](../debugger/debugger-feature-tour.md) In questo argomento vengono trattate alcune aree non incluse nella presentazione delle funzionalità.

## <a name="pin-data-tips"></a>Aggiungere suggerimenti dati

Se si passa spesso il puntatore del mouse sui suggerimenti dati durante il debug, è possibile aggiungere il suggerimento dati per la variabile per ottenere un accesso rapido. La variabile rimane bloccata anche dopo il riavvio. Per aggiungere il suggerimento dati, fare clic sull'icona a forma di puntina mentre si passa il puntatore del mouse su di esso. È possibile aggiungere più variabili.

![Aggiunta di un suggerimento dati](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Modificare il codice e continuare il debug (C#, VB, C++)

Nella maggior parte dei linguaggi supportati Visual Studio, è possibile modificare il codice nel corso di una sessione di debug e continuare il debug. Per usare questa funzionalità, fare clic nel codice con il cursore mentre è in pausa nel debugger, apportare modifiche e premere **F5**, **F10** o **F11** per continuare il debug.

![Debug di Modifica e continuazione](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Per altre informazioni sull'uso della funzionalità e sulle limitazioni delle funzionalità, vedere [Modifica e continuazione.](../debugger/edit-and-continue.md)

## <a name="edit-xaml-code-and-continue-debugging"></a>Modificare il codice XAML e continuare il debug

Per modificare il codice XAML durante una sessione di debug, vedere Scrivere ed eseguire [il debug di codice XAML](../xaml-tools/xaml-hot-reload.md)in esecuzione con Ricaricamento rapido XAML .

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Problemi di debug difficili da riprodurre

Se è difficile o dispendioso in termini di tempo ricreare un determinato stato nell'app, valutare se l'uso di un punto di interruzione condizionale può essere utile. È possibile [](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) usare punti di interruzione condizionali e filtrare i punti di interruzione per evitare di interrompere il codice dell'app fino a quando l'app non entra in uno stato desiderato, ad esempio uno stato in cui una variabile archivia dati non validi. È possibile impostare le condizioni usando espressioni, filtri, hit count e così via.

#### <a name="to-create-a-conditional-breakpoint"></a>Per creare un punto di interruzione condizionale

1. Fare clic con il pulsante destro del mouse sull'icona di un punto di interruzione (la palla rossa) e **scegliere Condizioni**.

2. Nella finestra **Impostazioni** punto di interruzione digitare un'espressione.

    ![Punto di interruzione condizionale](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "Punto di interruzione condizionale")

3. Se si è interessati a un  altro  tipo di condizione, selezionare Filtro **anziché** Espressione condizionale nella finestra di dialogo Impostazioni punto di interruzione e quindi seguire i suggerimenti per il filtro.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Configurare i dati da visualizzare nel debugger

Per C#, Visual Basic e C++ (solo codice C++/CLI), è possibile indicare al debugger quali informazioni visualizzare usando [l'attributo DebuggerDisplay.](../debugger/using-the-debuggerdisplay-attribute.md) Per il codice C++, è possibile eseguire la stessa operazione usando [le visualizzazioni Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

Con il debugger sospeso su una riga di codice, usare il mouse per afferrare il puntatore della freccia gialla a sinistra. Spostare il puntatore della freccia gialla in un punto diverso nel percorso di esecuzione del codice. Si usa quindi F5 o un comando di passaggio per continuare a eseguire l'app.

![Spostare il puntatore di esecuzione](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Spostare il puntatore di esecuzione")

Modificando il flusso di esecuzione è possibile eseguire operazioni come testare percorsi di esecuzione del codice diversi o rieseguire il codice senza riavviare il debugger.

> [!WARNING]
> Spesso questa funzionalità deve essere usata con attenzione. Nella descrizione comando viene visualizzato un avviso. È anche possibile che vengano visualizzati altri avvisi. Lo spostamento del puntatore non può ripristinare lo stato precedente dell'app.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Tenere traccia di un oggetto esterno all'ambito (C#, Visual Basic)

È facile visualizzare le variabili usando finestre del debugger come la **finestra Espressioni di** controllo. Tuttavia, quando una variabile esce dall'ambito nella finestra **Espressioni** di controllo, è possibile notare che è disattivata. In alcuni scenari di app, il valore di una variabile può cambiare anche quando la variabile non è in ambito ed è consigliabile osservarla attentamente (ad esempio, una variabile può essere garbage collection). È possibile tenere traccia della variabile creando un ID oggetto per la variabile nella **finestra Espressioni di** controllo.

#### <a name="to-create-an-object-id"></a>Per creare un ID oggetto

1. Impostare un punto di interruzione vicino a una variabile di cui si vuole tenere traccia.

2. Avviare il debugger (**F5**) e arrestarsi in corrispondenza del punto di interruzione.

3. Trovare la variabile nella finestra **Variabili locali** ( Debug **> Windows > Variabili** locali ), fare clic con il pulsante destro del mouse sulla variabile e scegliere Crea **ID oggetto**.

    ![Creare un ID oggetto](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. Nella finestra Variabili locali **$** verrà visualizzato un segno più **un** numero. Questa variabile è l'ID oggetto.

5. Fare clic con il pulsante destro del mouse sulla variabile ID oggetto e **scegliere Aggiungi espressioni di controllo.**

Per altre informazioni, vedere [Creare un ID oggetto.](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)

## <a name="view-return-values-for-functions"></a>Visualizzare i valori restituiti per le funzioni

Per visualizzare i valori restituiti per le funzioni, esaminare le funzioni visualizzate nella finestra Auto durante l'esecuzione del codice.  Per visualizzare il valore restituito per una funzione, assicurarsi che la funzione a cui si è interessati sia già stata eseguita (premere **F10** una volta se si è attualmente arrestati nella chiamata di funzione). Se la finestra è chiusa, usare **Debug > Windows > Auto per** aprire la finestra **Auto.**

![Finestra Auto](../debugger/media/dbg-tips-autos-window.png "Finestra Autos")

È anche possibile immettere funzioni nella **finestra** Controllo immediato per visualizzare i valori restituiti. Aprirlo usando debug **> Windows > immediato.**

![Finestra di controllo immediato](../debugger/media/dbg-tips-immediate-window.png "Finestra di controllo immediato")

È anche possibile usare [pseudovariabili nella](../debugger/pseudovariables.md) finestra **Espressioni di** controllo **e controllo** immediato, ad esempio `$ReturnValue` .

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Esaminare le stringhe in un visualizzatore

Quando si lavora con le stringhe, può essere utile visualizzare l'intera stringa formattata. Per visualizzare una stringa di testo normale, XML, HTML o JSON, fare clic sull'icona della lente di ingrandimento ![VisualizzatoreIcona](../debugger/media/dbg-tips-visualizer-icon.png "Icona visualizzatore") mentre si passa il mouse su una variabile contenente un valore stringa.

![Aprire un visualizzatore di stringhe](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualizzatore di stringhe può essere utile per determinare se il formato di una stringa non è corretto, a seconda del tipo di stringa. Ad esempio, un campo **Valore** vuoto indica che la stringa non è riconosciuta dal tipo di visualizzatore. Per altre informazioni, vedere [Finestra di dialogo Visualizzatore stringhe](../debugger/string-visualizer-dialog-box.md).

![Visualizzatore di stringhe JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Per alcuni altri tipi, ad esempio oggetti DataSet e DataTable visualizzati nelle finestre del debugger, è anche possibile aprire un visualizzatore predefinito.

## <a name="break-into-code-on-handled-exceptions"></a>Interrompi nel codice per le eccezioni gestite

Il debugger si interrompe nel codice in seguito ad eccezioni non gestite. Tuttavia, anche le eccezioni gestite(ad esempio le eccezioni che si verificano all'interno di un blocco) possono essere un'origine di bug ed è possibile esaminare quando `try/catch` si verificano. È possibile configurare il debugger in modo che interrompa il codice per le eccezioni gestite, nonché configurando le opzioni nella finestra di **dialogo Impostazioni** eccezione . Aprire questa finestra di dialogo scegliendo **Debug > Windows > eccezione Impostazioni**.

La **finestra Impostazioni** eccezioni consente di indicare al debugger di interrompere il codice in caso di eccezioni specifiche. Nella figura seguente il debugger si interrompe nel codice ogni volta che si verifica `System.NullReferenceException` un. Per altre informazioni, vedere [Gestione delle eccezioni.](../debugger/managing-exceptions-with-the-debugger.md)

![Finestra di Impostazioni eccezioni](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Eseguire il debug di deadlock e race conditions

Se è necessario eseguire il debug dei tipi di problemi comuni alle app multithreading, spesso è utile visualizzare la posizione dei thread durante il debug. È possibile eseguire facilmente questa operazione usando **il pulsante Mostra thread nell'origine.**

#### <a name="to-show-threads-in-your-source-code"></a>Per visualizzare i thread nel codice sorgente

1. Durante il debug, fare clic **sul pulsante Mostra thread nell'origine** Mostra thread ![nell'origine nella](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") barra degli strumenti **Debug.**

2. All'estrema sinistra della finestra, In questa riga viene visualizzata l'icona del *marcatore*  ![thread Marcatore](../debugger/media/dbg-thread-marker.png "ThreadMarker") thread simile a due thread in forma di thread. Il marcatore del thread indica l'interruzione di un thread in questa posizione.

    Si noti che un marcatore di thread può essere parzialmente nascosto da un punto di interruzione.

3. Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati. in cui è indicato il nome e il numero ID di ciascun thread interrotto.

    È anche possibile visualizzare la posizione dei thread nella [finestra Stack in parallelo](../debugger/get-started-debugging-multithreaded-apps.md).

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Esaminare i payload per i servizi Web e le risorse di rete (UWP)

Nelle app UWP è possibile analizzare le operazioni di rete eseguite usando `Windows.Web.Http` l'API. È possibile usare questo strumento per eseguire il debug di servizi Web e risorse di rete. Per usare lo strumento, selezionare **Debug > Profiler prestazioni**. Selezionare **Rete** e quindi scegliere **Avvia.** Nell'applicazione seguire lo scenario che usa `Windows.Web.Http` e quindi scegliere **Arresta raccolta** per generare il report.

![Strumento di profilatura Utilizzo rete](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Selezionare un'operazione nella visualizzazione di riepilogo per visualizzare altri dettagli.

![Informazioni dettagliate nello strumento Utilizzo rete](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Per altre informazioni, vedere [Utilizzo della rete](../profiling/network-usage.md).
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>Acquisire familiarità con il modo in cui il debugger si collega all'app (C#, C++, Visual Basic, F#)

Per connettersi all'app in esecuzione, il debugger carica i file di simboli (con estensione pdb) generati per la stessa compilazione dell'app di cui si sta tentando di eseguire il debug. In alcuni scenari può essere utile avere una conoscenza approfondita dei file di simboli. È possibile esaminare come Visual Studio i file di simboli usando la **finestra** Moduli.

Aprire la **finestra Moduli** durante il debug selezionando Debug **> Windows > Moduli**. La **finestra** Moduli può indicare i moduli che il debugger sta trattando come codice utente, o [*My Code,*](../debugger/just-my-code.md)e lo stato di caricamento dei simboli per il modulo. Nella maggior parte degli scenari, il debugger trova automaticamente i file di simboli per il codice utente, ma se si vuole eseguire un'istruzione o eseguire il debug di codice .NET, codice di sistema o codice di libreria di terze parti, sono necessari passaggi aggiuntivi per ottenere i file di simboli corretti.

![Visualizzare le informazioni sui simboli nella finestra Moduli](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

È possibile caricare le informazioni sui simboli direttamente dalla **finestra Moduli** facendo clic con il pulsante destro del mouse e scegliendo **Carica simboli**.

In alcuni casi, gli sviluppatori di app spediranno le app senza i file di simboli corrispondenti (per ridurre il footprint), ma conservano una copia dei file di simboli corrispondenti per la compilazione in modo che possano eseguire il debug di una versione rilasciata in un secondo momento.

Per scoprire in che modo il debugger classifica il codice come codice utente, [vedere Just My Code](../debugger/just-my-code.md). Per altre informazioni sui file di simboli, vedere Specificare i file di simboli (con estensione [pdb)](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)e di origine nel debugger Visual Studio .

## <a name="learn-more"></a>Altre informazioni

Per altri suggerimenti e consigli e informazioni più dettagliate, vedere questi post di blog:

- [7 hack meno noti per il debug in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 gemme nascoste in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Vedi anche

[Tasti di scelta rapida](../ide/productivity-shortcuts.md)
