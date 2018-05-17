---
title: Correggere gli errori del programma e migliorare il codice
description: Questo articolo descrive alcune modalità di base in cui Visual Studio consente di individuare e correggere eventuali problemi nel codice, inclusi errori di compilazione, analisi del codice, strumenti per il debug e unit test.
ms.date: 05/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1aa3d2412bfeabcaa3a66be7470367fcaaf0bfbc
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="make-code-work-in-visual-studio"></a>Come far funzionare il codice in Visual Studio

Visual Studio offre un set integrato di strumenti efficaci per il debug e la compilazione dei progetti. Questo articolo spiega in che modo Visual Studio consente di individuare i problemi nel codice usando l'output di compilazione, l'analisi del codice, gli strumenti di debug e gli unit test.

Si è già acquisita una certa familiarità con l'editor ed è stato creato del codice. Ora si vuole avere la sicurezza che il codice funzioni correttamente. In Visual Studio, come nella maggior parte degli IDE, per garantire il funzionamento del codice sono necessari due passaggi: la compilazione del codice per rilevare e risolvere gli errori relativi al progetto e al compilatore e l'esecuzione del codice per individuare gli errori dinamici e di run-time.

## <a name="build-your-code"></a>Compilare il codice

Sono disponibili due tipi di base per la configurazione della build: **Debug** e **Release**. La configurazione di tipo **Debug** produce un file eseguibile più lento e di dimensioni maggiori che offre un'esperienza di debug del runtime interattiva più completa. Il file eseguibile di **Debug** non deve essere mai distribuito. La configurazione di tipo **Release** compila un file eseguibile più veloce e ottimizzato, adatto alla distribuzione (almeno dal punto di vista del compilatore). La configurazione predefinita della build è **Debug**.

Il modo più semplice per compilare il progetto è premere **F7**, ma è anche possibile avviare la compilazione selezionando **Compila** > **Compila soluzione** dal menu principale.

![Selezione del menu del progetto di compilazione di Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png)

È possibile osservare il processo di compilazione nella finestra **Output** nella parte inferiore dell'interfaccia utente di Visual Studio, dove vengono visualizzati gli eventuali errori, avvisi e operazioni di compilazione. In caso di errori, o se vengono rilevati avvisi di livello superiore a quello configurato, la compilazione ha esito negativo. È possibile fare clic su errori e avvisi per passare alla riga in cui si sono verificati. Ricompilare il progetto premendo di nuovo **F7**, per ricompilare solo i file con errori, o **CTRL**+**ALT**+**F7**, per una ricompilazione pulita e completa.

Nella finestra dei risultati sotto l'editor vengono visualizzate due finestre a schede: la finestra **Output** che contiene l'output del compilatore non elaborato (compresi i messaggi di errore) e la finestra **Elenco errori** che visualizza un elenco ordinabile e filtrabile di tutti gli errori e gli avvisi.

Se la compilazione viene completata correttamente, nella finestra **Output** vengono visualizzati risultati simili ai seguenti:

![Output di una compilazione riuscita di Visual Studio](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Rivedere l'elenco errori

A meno che non siano state apportate modifiche al codice compilato correttamente in precedenza, è probabile si verifichi un errore. Se non si ha familiarità con la codifica, gli errori potrebbero essere numerosi. Gli errori possono essere talvolta elementari, ad esempio un semplice errore di sintassi o un nome di variabile non corretto, oppure difficili da comprendere, in cui l'unico aiuto è un codice non facile da decifrare. Per una visualizzazione più chiara dei problemi, passare alla parte inferiore della finestra di compilazione **Output** e scegliere la scheda **Elenco errori**. Si apre una visualizzazione più organizzata degli errori e degli avvisi relativi al progetto in cui vengono fornite anche alcune opzioni aggiuntive.

![Output ed elenco di errori di Visual Studio](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Fare clic sulla riga di errore nella finestra **Elenco errori** per passare alla riga in cui si è verificato l'errore. In alternativa, attivare i numeri di riga facendo clic sulla barra **Avvio veloce** in alto a destra, digitando "numeri di riga" al suo interno e premendo **INVIO**. Questo è il modo più rapido per passare alla finestra di dialogo **Opzioni** in cui è possibile attivare i numeri di riga. Per risparmiare tempo, è consigliabile imparare a usare la barra **Avvio veloce**.

![Editor di Visual Studio con numeri di riga](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Opzione dei numeri di riga di Visual Studio](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Per passare rapidamente al numero di riga in cui si è verificato l'errore, premere **CTRL**+**G**.

L'errore viene segnalato da una sottolineatura rossa "a zigzag". Per altri dettagli, passare il mouse sull'errore. Correggere il problema per farlo scomparire. La correzione, però, potrebbe causare un nuovo errore. Questo fenomeno viene chiamato "regressione".

![Errore di Visual Studio al passaggio del mouse](../ide/media/vs_ide_gs_debug_error_hover1.png)

Scorrere l'elenco degli errori e risolvere tutti gli errori nel codice.

![Finestra degli errori di debug di Visual Studio](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Rivedere gli errori in dettaglio

Molti errori possono essere poco comprensibili per l'utente poiché sono stati espressi con un linguaggio da compilatori. In questi casi sono necessarie informazioni aggiuntive. Dalla finestra **Elenco errori** è possibile eseguire una ricerca automatica in Bing per visualizzare altre informazioni sull'errore o sull'avviso. Fare clic con il pulsante destro del mouse sulla riga corrispondente e selezionare **Mostra guida errore** dal menu di scelta rapida oppure fare clic sul valore del codice di errore con collegamento ipertestuale nella colonna **Codice** colonna dell'**Elenco errori**.

![Ricerca Bing dell'elenco di errori di Visual Studio](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

A seconda delle impostazioni, il Web browser visualizza i risultati della ricerca per il testo e il codice di errore o si apre una scheda in Visual Studio contenente i risultati della ricerca in Bing. I risultati provengono da diverse origini in Internet, quindi è probabile che non tutti siano utili.

## <a name="use-code-analysis"></a>Usare l'analisi codice

Gli analizzatori di codice cercano i problemi di codice comuni che possono causare errori di run-time o problemi nella gestione del codice.

### <a name="c-and-visual-basic-code-analysis"></a>Analisi del codice C# e Visual Basic

Visual Studio 2017 include un set predefinito di [analizzatori .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md) che esaminano il codice C# e Visual Basic durante la digitazione. È possibile installare analizzatori aggiuntivi come estensione di Visual Studio o pacchetto NuGet. Se rilevate, eventuali violazioni delle regole vengono segnalate sia nell'editor di codice con una linea ondulata sotto il codice che causa problemi, sia nell'**Elenco errori**.

### <a name="c-code-analysis"></a>Analisi del codice C++

Per analizzare il codice C++, eseguire l'[analisi del codice statico](../code-quality/quick-start-code-analysis-for-c-cpp.md). È consigliabile eseguire questa analisi dopo aver rimosso gli errori più semplici che impediscono una corretta compilazione e di dedicare del tempo alla risoluzione degli eventuali avvisi restituiti. In questo modo si prevengono altri problemi in futuro e si possono apprendere alcune tecniche relative allo stile del codice.

Per avviare l'analisi del codice statico, premere **ALT**+**F11** o selezionare **Analizza** > **Esegui analisi del codice sulla soluzione** dal menu principale.

![Voce del menu Analisi codice di Visual Studio](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Eventuali avvisi nuovi o aggiornati vengono visualizzati nella scheda **Elenco errori** nella parte inferiore dell'IDE. Fare clic sugli avvisi per aprirli nel codice.

![Elenco di errori con avvisi di Visual Studio](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-light-bulbs-to-fix-or-refactor-code"></a>Usare le lampadine per correggere o effettuare il refactoring del codice

Le [lampadine](../ide/quick-actions.md) sono una funzionalità relativamente nuova di Visual Studio che consente di effettuare il refactoring del codice inline. Consentono di risolvere con la massima semplicità gli avvisi più comuni in modo rapido ed efficace nel codice C#, C++ e Visual Basic. Per accedere a questa nuova funzionalità, fare clic con il pulsante destro del mouse sulla linea ondulata sotto un avviso e selezionare **Azioni rapide** o premere **CTRL**+**.** quando il cursore si trova sulla riga con la linea ondulata colorata. Verrà visualizzato un elenco di possibili correzioni o refactoring che è possibile applicare alla riga di codice.

![Anteprima di lampadina di Visual Studio](../ide/media/quick-actions-options.png)

Le lampadine possono essere usate in tutti i casi in cui gli analizzatori di codice individuano la possibilità di correggere, eseguire il refactoring o migliorare il codice. Fare clic su una qualsiasi riga di codice, fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida e selezionare **Azioni rapide** oppure, per aumentare l'efficienza, premere **CTRL**+**.** Se sono disponibili opzioni di refactoring o miglioramento, vengono visualizzate. In caso contrario, viene visualizzato il messaggio **Azioni rapide non disponibili in questo punto** nell'angolo inferiore sinistro dell'IDE.

![Testo 'Nessuna opzione' del menu Lampadina di Visual Studio](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Con l'esperienza si apprenderà a usare rapidamente i tasti di direzione e **CTRL**+**.** per controllare se sia possibile eseguire il refactoring con Azioni rapide e per pulire il codice.

Per altre informazioni sulle lampadine, vedere [Azioni rapide](../ide/quick-actions.md).

## <a name="debug-your-running-code"></a>Eseguire il debug del codice in esecuzione

Dopo aver compilato correttamente il codice e aver eseguito qualche attività di pulizia, eseguire il codice premendo **F5** o selezionando **Debug** > **Avvia debug**. L'applicazione viene avviata in un ambiente di debug in modo che sia possibile osservarne il comportamento in modo dettagliato. L'IDE di Visual Studio viene modificato mentre l'applicazione è in esecuzione. La finestra **Output** viene sostituita da due nuove finestre a schede (nella configurazione predefinita della finestra): **Auto/Variabili locali/Espressione di controllo** e **Stack di chiamate/Punti di interruzione/Impostazioni eccezione/Output**. In queste finestre sono presenti più schede che consentono di esaminare e valutare le variabili, i thread, gli stack di chiamate e vari altri comportamenti dell'app durante l'esecuzione.

![Finestre automatiche e di stack di chiamate di Visual Studio](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Per arrestare l'app, premere **MAIUSC**+**F5** o fare clic sul pulsante **Arresta**. In alternativa, è possibile chiudere semplicemente la finestra principale dell'app o la finestra di dialogo della riga di comando.

Se il codice è stato eseguito senza errori ed esattamente come previsto, complimenti! In caso di blocco, arresto anomalo o risultati imprevisti, è necessario individuare l'origine dei problemi e correggere i bug.

### <a name="set-simple-breakpoints"></a>Impostare punti di interruzione semplici

I [punti di interruzione](../debugger/using-breakpoints.md) rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice. Non è necessario ricompilare un progetto dopo l'impostazione e la rimozione dei punti di interruzione.

Impostare un punto di interruzione facendo clic sul margine più esterno della riga in cui si vuole inserire l'interruzione oppure premere **F9** per impostare un punto di interruzione nella riga di codice corrente. Quando si esegue il codice, questo verrà sospeso oppure *interrotto* prima dell'esecuzione delle istruzioni per la riga di codice specificata.

![Punto di interruzione di Visual Studio](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Di seguito sono riportati alcuni usi comuni dei punti di interruzione:

- Per limitare l'origine di un arresto anomalo o di blocco, inserire i punti di interruzione all'interno e intorno al codice della chiamata al metodo che si ritiene causi l'errore. Durante l'esecuzione del codice nel debugger, rimuovere e reimpostare i punti di interruzione fino a individuare la riga di codice interessata. Vedere la sezione successiva per informazioni su come eseguire il codice nel debugger.

- Quando si introduce un nuovo codice, impostare un punto di interruzione all'inizio del codice ed eseguire il codice per verificare che funzioni come previsto.

- Se è stato implementato un comportamento complesso, impostare punti di interruzione per il codice algoritmico affinché sia possibile esaminare i valori delle variabili e i dati quando il programma si interrompe.

- Se si scrive codice C o C++, usare i punti di interruzione per arrestare il codice affinché sia possibile esaminare i valori di indirizzo (cercare NULL) e conteggi riferimenti durante il debug degli errori correlati alla memoria.

Per altre informazioni sull'uso dei punti di interruzione, vedere [Uso di punti di interruzione](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Esaminare il codice in fase di esecuzione

Quando il codice in esecuzione incontra un punto di interruzione e viene sospeso, la riga di codice contrassegnata in giallo, ovvero l'istruzione corrente, non è ancora stata eseguita. A questo punto, è possibile eseguire l'istruzione corrente ed esaminare i valori modificati. È possibile usare diversi comandi di *esecuzione* per eseguire il codice nel debugger. Se il codice contrassegnato è una chiamata a un metodo, è possibile eseguire le istruzioni premendo **F11**. È anche possibile *eseguire l'istruzione/la routine* per la riga di codice premendo **F10**. Per informazioni su altri comandi e informazioni dettagliate su come esaminare il codice, leggere [Spostarsi nel codice con il debugger](../debugger/navigating-through-code-with-the-debugger.md).

![Verifica del valore di runtime di Visual Studio](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Nell'illustrazione precedente, è possibile spostarsi in un'istruzione con il debugger premendo **F10** o **F11**. In questo caso non si verifica una chiamata al metodo e pertanto il risultato dei due comandi è lo stesso.

Quando il debugger viene sospeso, è possibile esaminare le variabili e gli stack di chiamate per individuare il problema. I valori sono compresi negli intervalli previsti? L'ordine con cui si stanno eseguendo le chiamate è corretto?

![Verifica del valore di runtime di Visual Studio](../ide/media/vs_ide_gs_debug_inspect_value.png)

Passare il mouse su una variabile per visualizzarne il valore corrente e i riferimenti. Se viene visualizzato un valore non previsto, è probabile che ci sia un bug nel codice precedente o chiamante. Per i dettagli sul debug, [leggere altre informazioni ](../debugger/getting-started-with-the-debugger.md) sull'uso del debugger.

Visual Studio visualizza anche la finestra **Strumenti di diagnostica**, in cui è possibile osservare l'utilizzo della memoria e della CPU dell'app nel corso del tempo. Durante lo sviluppo dell'app, è possibile usare questi strumenti per individuare l'utilizzo intenso della CPU imprevisto o l'allocazione della memoria. Usare contemporaneamente anche la finestra **Espressione di controllo** e i punti di interruzione per determinare la causa di questo utilizzo intenso imprevisto o del mancato rilascio delle risorse. Per altre informazioni, vedere [Panoramica delle funzionalità di profilatura](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Eseguire unit test

Gli unit test sono il primo elemento di difesa contro i bug nel codice perché, se eseguiti correttamente, testano una singola "unità" di codice, in genere una singola funzione, ed è più semplice eseguirne il debug rispetto all'intero programma. Visual Studio installa i framework degli unit test di Microsoft sia per il codice gestito e che per quello nativo. Usare un framework di testing unità per creare unit test, eseguirli e riportare i risultati dei test. Eseguire nuovamente gli unit test quando si apportano modifiche per verificare che il codice funzioni ancora correttamente. Con Visual Studio Enterprise è possibile eseguire automaticamente i test dopo ogni compilazione.

Per iniziare, vedere [Generate unit tests for your code with IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) (Generare unit test per il codice con IntelliTest).

Per altre informazioni sugli unit test in Visual Studio e su come usarli per creare codice di qualità migliore, vedere [Unit Test Basics](../test/unit-test-basics.md) (Nozioni di base sugli unit test).

## <a name="see-also"></a>Vedere anche

- [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
- [Altre informazioni sull'uso del debugger](../debugger/getting-started-with-the-debugger.md)
- [Generare e correggere il codice](../ide/code-generation-in-visual-studio.md)