---
title: Introduzione con il debug in Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca3f3806f9097082d71dd80e74ccf48cd78c951b
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386888"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Introduzione al debug in Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015 fornisce un potente set integrato di strumenti per il debug e la compilazione di un progetto. Questo argomento spiega come iniziare a usare il set di base delle funzionalità dell'interfaccia utente di debug.

 Nota: i collegamenti a funzionalità più avanzate e ad argomenti per specifiche piattaforme o funzionalità sono disponibili nella parte inferiore della pagina.

## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Il codice non funziona. Come si risolve il problema?
 Ora che si è acquisita familiarità con l'editor ed è stato creato il codice, è possibile iniziare il debug del codice. In Visual Studio 2015, come per la maggior parte degli IDE, il debug viene eseguito in due fasi: la compilazione del codice per rilevare e risolvere gli errori relativi al progetto e al compilatore e l'esecuzione del codice nell'ambiente per rilevare e risolvere gli errori dinamici e di runtime.

### <a name="configuring-a-build"></a>Configurazione di una compilazione
 Sono disponibili due tipi di base per la configurazione della build: **Debug** e **Release**. La prima configurazione produce un file eseguibile più lento e di dimensioni maggiori che offre un'esperienza di debug del runtime interattiva più completa, ma che non deve essere mai distribuito. La seconda configurazione compila un file eseguibile più veloce e ottimizzato, adatto alla distribuzione (almeno dal punto di vista del compilatore).

 La configurazione predefinita della build è **Debug**.

 ![Pulsante Debug per la build di Visual Studio](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")

 È anche possibile specificare una determinata piattaforma della build di destinazione, ad esempio **x86** (CPU Intel a 32 bit), **x64** (CPU Intel a 64 bit) e **ARM** (CPU ARM, supportate solo per alcuni tipi di applicazione). L'impostazione predefinita è **x86** per i progetti gestiti e nativi. Per modificarlo, fare clic sull'elenco a discesa piattaforma di compilazione e selezionare una piattaforma diversa o **Configuration Manager...**

 ![Finestra di gestione del file di configurazione di Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")

 Per specificare una configurazione della build di destinazione, usare **Gestione configurazione**. Avviare il programma, fare clic sull'elenco a discesa della **Configurazione** o della **CPU**, quindi selezionare **Nuovo** per creare una nuova build o una nuova piattaforma.

 ![Finestra Gestione configurazione di Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")

 Per iniziare, usare semplicemente **Debug** e **x86** rispettivamente come configurazione e piattaforma della build. Al termine della codifica e del debug, modificare la configurazione in **Release** e fare riferimento a una piattaforma specifica. Le versioni precedenti di Visual Studio specificavano una piattaforma predefinita **AnyCPU** per i progetti di codice .NET.

 Nota: quando si compila il progetto, i valori di configurazione e piattaforma vengono usati anche per determinare il percorso della directory del progetto da creare per archiviare il file eseguibile, In genere, si tratta ** \<path-to-project> \\<nome di progetto \> \\<\> \\ \> piattaforma di configurazione<**. Ad esempio, un progetto con una configurazione di `Debug` e una piattaforma `x86` si troverebbe in `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86`. Questa funzionalità è utile se si usano strumenti o script personalizzati per gestire questi file eseguibili compilati.

### <a name="building-your-code"></a>Compilazione del codice
 Dopo aver configurato la compilazione, è possibile passare alla compilazione effettiva del progetto. Il modo più semplice è premere F7, ma è anche possibile avviare la compilazione selezionando **Compila->Compila soluzione** dal menu principale.

 ![Selezione del menu del progetto di compilazione di Visual Studio](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")

 È possibile osservare il processo di compilazione nella finestra di stato **Output** nella parte inferiore dell'interfaccia utente di Visual Studio, dove vengono visualizzati gli eventuali errori, avvisi e operazioni di compilazione. In caso di errori (o se vengono rilevati avvisi di livello superiore a quello configurato), la compilazione non riuscirà. È possibile fare clic su errori e avvisi per passare alla riga in cui si sono verificati. Ricompilare il progetto premendo di nuovo **F7**, per ricompilare solo i file con errori, o **CTRL+ALT+F7**, per una ricompilazione pulita e completa.

 Nella finestra dei risultati sotto l'editor vengono visualizzate due finestre a schede della compilazione: la finestra **Output** che contiene l'output del compilatore non elaborato (compresi i messaggi di errore) e la finestra **Elenco errori** che visualizza un elenco ordinabile e filtrabile di tutti gli errori e gli avvisi.

 Se l'operazione viene completata correttamente, nella finestra **Output** vengono visualizzati risultati simili ai seguenti.

 ![Output di una compilazione riuscita di Visual Studio](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")

### <a name="reviewing-the-error-list"></a>Revisione dell'elenco errori
 A meno che non siano state apportate modifiche al codice compilato correttamente in precedenza, è probabile venga rilevato un errore. Se non si ha familiarità con la codifica, è probabile che ne vengano rilevati molti. Gli errori possono essere elementari, ad esempio un errore di sintassi semplice o un nome di variabile non corretto, oppure difficili da comprendere, in cui l'unico aiuto è un codice non facile da decifrare. Per una visualizzazione più chiara dei problemi, passare alla parte inferiore della finestra di **output** di compilazione, quindi fare clic sulla scheda **Elenco errori** . In questo modo si ottiene una visualizzazione più organizzata degli errori e degli avvisi per il progetto e vengono fornite anche alcune opzioni aggiuntive.

 ![Output ed Elenco errori di Visual Studio 2015](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")

 Fare clic sulla riga di errore nella finestra **Elenco errori** per passare alla riga in cui si è verificato l'errore. In alternativa, attivare i numeri di riga facendo clic sulla barra **avvio veloce** in alto a destra, digitando "numeri di riga" al suo interno e premendo INVIO. Questo è il modo più rapido per passare alla voce della finestra **Opzioni** in cui è possibile attivare i numeri di riga. Per risparmiare tempo, è consigliabile imparare a usare la barra **Avvio veloce**.

 ![Editor di Visual Studio con numeri di riga](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")

 ![Opzione dei numeri di riga di Visual Studio](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")

 Per passare rapidamente al numero di riga in cui si è verificato l'errore, premere CTRL+G.

 L'errore viene identificato mediante una sottolineatura rossa "a zigzag". Per altri dettagli, passare il mouse sull'errore. Correggere il problema per farlo scomparire. La correzione, però, potrebbe causare un nuovo errore. Questo fenomeno viene chiamato "regressione".

 ![Errore di Visual Studio al passaggio del mouse](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")

 Scorrere l'elenco degli errori e risolvere tutti gli errori nel codice.

 ![Finestra degli errori di debug di Visual Studio](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")

### <a name="reviewing-errors-in-detail"></a>Revisione degli errori in dettaglio
 Molti errori possono essere poco comprensibili per l'utente poiché sono stati espressi con un linguaggio da compilatori. In questi casi sono necessarie informazioni aggiuntive. Dalla finestra **Elenco errori** è possibile eseguire una ricerca automatica in Bing per ottenere altre informazioni sull'errore, o sull'avviso, facendo clic con il pulsante destro del mouse sulla riga corrispondente e scegliendo **Mostra guida errore** dal menu di scelta rapida.

 ![Ricerca Bing dell'elenco di errori di Visual Studio](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")

 Viene avviata una scheda all'interno di Visual Studio 2015 che ospita i risultati di una ricerca in Bing relativa al codice e al testo dell'errore. I risultati provengono da diverse origini in Internet, quindi è probabile che non tutti siano utili.

 In alternativa, è possibile fare clic sul valore del codice di errore con collegamento ipertestuale nella colonna **Codice** dell'**Elenco errori**. Viene avviata una ricerca in Bing solo per lo specifico codice di errore.

### <a name="performing-static-code-analysis"></a>Esecuzione dell'analisi statica del codice
 L'"analisi statica del codice" consente di controllare automaticamente il codice alla ricerca di problemi frequenti che potrebbero causare errori di runtime o problemi nella gestione del codice. Si consiglia di eseguire questa analisi dopo aver rimosso gli errori più semplici che impediscono la compilazione e di dedicare del tempo alla risoluzione degli eventuali avvisi restituiti. In questo modo si prevengono ulteriori problemi in futuro e si apprendono alcune tecniche relative allo stile del codice.

 Premere ALT + F11 (oppure selezionare **analizza->Esegui analisi del codice su soluzione** dal menu superiore) per avviare l'analisi statica del codice. Se la quantità di codice è elevata, l'operazione potrebbe richiedere del tempo.

 ![Voce del menu Analisi codice di Visual Studio 2015](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")

 Eventuali avvisi nuovi o aggiornati verranno visualizzati nella scheda **Elenco errori** nella parte inferiore dell'IDE. Fare clic sugli avvisi per aprirli.

 ![Elenco errori con avvisi di Visual Studio 2015](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")

 Gli avvisi verranno identificati con una sottolineatura giallo-verde brillante a zigzag, anziché rossa. Passare il mouse su di essi per ulteriori dettagli e fare clic con il pulsante destro del mouse per visualizzare un menu di scelta rapida in cui vengono fornite funzionalità di supporto per le correzioni o opzioni di refactoring.

 ![Avviso di analisi del codice di Visual Studio al passaggio del mouse](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Uso delle lampadine per correggere o effettuare il refactoring del codice
 Le lampadine sono una nuova funzionalità di Visual Studio 2015 che consente di effettuare il refactoring del codice inline. Consentono di risolvere con la massima semplicità gli avvisi più comuni in modo rapido ed efficace. Per accedere a questa nuova funzionalità, fare clic con il pulsante destro del mouse sulla sottolineatura a zigzag di un avviso o premere CTRL+. mentre si passa il mouse sulla sottolineatura, e selezionare **Azioni rapide**.

 ![Opzioni rapide del menu Lampadina di Visual Studio 2015](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")

 Verrà visualizzato un elenco di possibili correzioni o refactoring che è possibile applicare alla riga di codice.

 ![Anteprima del menu Lampadina di Visual Studio 2015](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")

 Le lampadine possono essere usate in tutti i casi in cui gli analizzatori di codice individuano la possibilità di correggere, eseguire il refactoring o migliorare il codice. Fare clic su una qualsiasi riga di codice, fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida e scegliere **Azioni rapide** oppure, per aumentare l'efficienza, premere CTRL+. Se sono disponibili opzioni di refactoring dell'area o di miglioramento, verranno visualizzate. In caso contrario, verrà visualizzato il messaggio `No quick options available here` nel riquadro nell'angolo inferiore sinistro dell'IDE.

 ![Testo 'Nessuna opzione' del menu Lampadina di Visual Studio 2015](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")

 Con l'esperienza si apprenderà a usare rapidamente i tasti di direzione e CTRL+. per controllare se sia possibile eseguire il refactoring con Azioni rapide e per pulire il codice.

 Per altre informazioni sulle lampadine, vedere [eseguire azioni rapide con le lampadine](../ide/perform-quick-actions-with-light-bulbs.md).

### <a name="debugging-your-running-code"></a>Debug del codice in esecuzione
 Ora che il codice è stato compilato correttamente ed è stato eseguito un po' di pulizia, eseguirlo premendo F5 o selezionando **debug->avviare il debug**. L'applicazione verrà avviata in un ambiente di debug in modo che sia possibile osservarne il comportamento in modo dettagliato. L'IDE di Visual Studio 2015 viene modificato mentre l'applicazione è in esecuzione: la finestra **Output** viene sostituita da due nuove finestre a schede (nella configurazione predefinita della finestra): **Auto/Variabili locali/Moduli/Espressione di controllo** e **Stack di chiamate/Punti di interruzione/Impostazioni eccezione/Output**. In queste finestre sono presenti più schede che consentono di esaminare e valutare le variabili, i thread, gli stack di chiamate e vari altri comportamenti dell'applicazione durante l'esecuzione.

 ![Finestre Auto e Stack di chiamate di VS2015](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")

 Provare a eseguire delle azioni con l'applicazione e osservare le modifiche. In caso di anomalie sospendere l'applicazione premendo CTRL + ALT + INTERR, oppure fare clic sul pulsante **Sospendi**.

 ![Pulsante Interrompi tutto di Visual Studio](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")

 Per continuare l'esecuzione dell'applicazione, premere F5 oppure fare clic sul pulsante **Continua**.

 ![Pulsante di continuazione del debug di Visual Studio](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")

 È possibile arrestare l'applicazione premendo MAIUSC+F5 o facendo clic sul pulsante **Arresta**. In alternativa, è possibile chiudere semplicemente la finestra principale dell'applicazione (o la finestra di dialogo della riga di comando).

 Se il codice è stato eseguito senza errori ed esattamente come previsto, complimenti! Modificare la configurazione della build in **Release** e ricompilarla per la distribuzione. Tuttavia, i professionisti potrebbero voler passare al bit sul testing unità alla fine. Tuttavia, se smette di rispondere o si arresta in modo anomalo o si sono verificati risultati anomali, è necessario individuare l'origine dei problemi e correggere i bug.

### <a name="setting-simple-breakpoints"></a>Impostazione di punti di interruzione semplici
 I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice. NON è necessario ricompilare un progetto dopo l'impostazione e la rimozione dei punti di interruzione.

 Impostare un punto di interruzione facendo clic sul margine più esterno della riga in cui si vuole inserire l'interruzione oppure selezionare la riga di codice e premere F9. Quando si esegue il codice, questo verrà interrotto prima dell'esecuzione delle istruzioni per la riga di codice specificata.

 ![Punto di interruzione di Visual Studio](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")

 Quando il codice viene interrotto, la riga di codice contrassegnata non è stata ancora eseguita. A questo punto è possibile eseguire le istruzioni per la riga di codice contrassegnata dal punto di interruzione ed esaminare i valori modificati. Questa operazione viene denominata "esecuzione di istruzioni" nel codice. Se il codice contrassegnato è una chiamata a un metodo, è possibile eseguire le istruzioni premendo F11. È anche possibile usare Esegui istruzione/routine per la riga di codice premendo F10. Per altre informazioni sulle azioni dei punti di interruzione, vedere [Navigating through Code with the Debugger](../debugger/navigating-through-code-with-the-debugger.md) (Esplorare il codice con il debugger).

 Di seguito sono riportati alcuni usi comuni dei punti di interruzione:

1. Per limitare l'origine di un arresto anomalo o di un programma che non risponde, disperderli in tutto il codice della chiamata al metodo che si ritiene causi l'errore. Durante l'esecuzione del codice, rimuovere e riunire i punti di interruzione fino a individuare la riga di codice interessata.

2. Quando si introduce un nuovo codice, impostare un punto di interruzione all'inizio del codice e eseguire un'istruzione alla volta per assicurarsi che il codice funzioni come previsto.

3. Se è stato implementato un comportamento complesso, impostare punti di interruzione per il codice algoritmico affinché sia possibile esaminare i valori delle variabili e i dati quando il programma si interrompe.

4. Se si scrive codice C o C++, usare i punti di interruzione per arrestare il codice affinché sia possibile esaminare i valori di indirizzo (cercare NULL) e conteggi riferimenti durante il debug degli errori correlati alla memoria.

   Per ulteriori informazioni sull'utilizzo dei punti di interruzione, vedere Utilizzo di punti di [interruzione](../debugger/using-breakpoints.md)

### <a name="setting-conditional-breakpoints"></a>Impostazione di punti di interruzione condizionali
 Se si ha un punto di interruzione in un ciclo o in una ricorsione oppure si hanno molti punti di interruzione di cui si esegue spesso un'istruzione alla volta, usare un punto di interruzione condizionale per assicurare che il codice venga sospeso SOLO quando vengono soddisfatte specifiche condizioni. In caso contrario, sarà necessario premere F11 un numero molto elevato di volte.

 Per impostare un punto di interruzione condizionale e sospendere il codice quando una variabile è impostata su un determinato valore o supera una determinata soglia, fare clic sul margine per impostare un punto di interruzione, quindi scegliere la rotellina dal menu visualizzato al passaggio del mouse.

 ![Impostazioni dei punti di interruzione di Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")

 Verrà visualizzata una finestra di dialogo simile alla seguente in cui è possibile impostare le condizioni per l'interruzione.

 ![Punto di interruzione condizionale di Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")

 Per altre informazioni su come dichiarare le espressioni usate per valutare i punti di interruzione condizionali, guardare il video di Channel9 [Breakpoint Configuration Experience in Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711) (Esperienza di configurazione dei punti di interruzione in Visual Studio 2015).

### <a name="inspecting-your-code-at-run-time"></a>Esame del codice in fase di esecuzione
 Quando il codice in esecuzione raggiunge un punto di interruzione e si arresta, è possibile esaminare le variabili e gli stack di chiamate per individuare il problema. I valori sono compresi negli intervalli previsti? L'ordine con cui si stanno eseguendo le chiamate è corretto?

 ![Ispezione del valore di&#45;tempo di esecuzione di Visual Studio 2015](../ide/media/vs-ide-gs-debug-inspect-value.PNG "vs_ide_gs_debug_inspect_value")

 Passare il mouse su una variabile per visualizzare i valori e i riferimenti attualmente contenuti. Se viene visualizzato un valore non previsto, è probabile che ci sia un bug nelle righe di codice precedenti o chiamate. Spostare i punti di interruzione verso l'alto o aggiungere condizioni ai punti di interruzione esistenti per restringere ulteriormente la ricerca.

 Inoltre, Visual Studio 2015 visualizza la finestra Strumenti di diagnostica, in cui è possibile osservare l'utilizzo della memoria e della CPU dell'applicazione nel corso del tempo. Usare questi strumenti per cercare un utilizzo della CPU o un'allocazione della memoria particolarmente elevati e non previsti. Usarlo insieme alla finestra **espressioni di controllo** e ai punti di interruzione per determinare la causa di un utilizzo intensivo imprevisto o di risorse non rilasciate.

 ![Finestra Strumenti di diagnostica di Visual Studio 2015](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")

### <a name="running-unit-tests"></a>Esecuzione di unit test
 Gli unit test sono programmi che verificano i percorsi di codice nell'applicazione o nel servizio. Visual Studio 2015 installa i framework di testing unità di Microsoft sia per il codice gestito e che per quello nativo. Usare un framework di testing unità per creare unit test, eseguirli e riportare i risultati dei test. Eseguire nuovamente gli unit test quando si apportano modifiche per verificare che il codice funzioni ancora correttamente. Quando si usa Visual Studio 2015 Enterprise è possibile eseguire automaticamente i test dopo ogni compilazione.

 Per iniziare, vedere [Generate unit tests for your code with IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) (Generare unit test per il codice con IntelliTest).

 Per altre informazioni sugli unit test in Visual Studio 2015 e su come usarli per creare codice di qualità migliore, leggere [Nozioni di base sugli unit test](../test/unit-test-basics.md).

## <a name="see-also"></a>Vedere anche
 [Debug nelle impostazioni del debugger di Visual Studio](../debugger/debugging-in-visual-studio.md) [e preparazione debug delle](../debugger/debugger-settings-and-preparation.md) [applicazioni a 64 bit](../debugger/debug-64-bit-applications.md) [nozioni di base sul debugger](../debugger/debugger-basics.md)
