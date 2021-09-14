---
title: Guida per la produttività
description: Informazioni sui tasti di scelta rapida e sulle funzionalità di produttività in Visual Studio che consentono di scrivere codice in modo efficiente, eseguire il debug del codice e gestire gli errori.
ms.custom: SEO-VS-2020
ms.date: 4/29/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ab3f07f0b9ec86ad1ec854ba5960099a084fb234
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636012"
---
# <a name="productivity-guide-for-visual-studio"></a>Guida alla produttività per Visual Studio

Se si vuole risparmiare tempo durante la scrittura del codice, si è nella posizione giusta. Questa guida alla produttività include suggerimenti utili per iniziare a usare Visual Studio, scrivere codice, eseguire il debug del codice, gestire gli errori e usare i tasti di scelta rapida in &mdash; un'unica pagina.

Per informazioni sui tasti di scelta rapida più utili, vedere [Tasti di scelta rapida per la produttività](../ide/productivity-shortcuts.md). Per un elenco completo dei tasti di scelta rapida per i comandi, vedere [Tasti di scelta rapida predefiniti](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="get-started"></a>Introduzione

È possibile risparmiare tempo nei menu cercando rapidamente qualsiasi elemento necessario, inclusi comandi, impostazioni, documentazione e opzioni di installazione. Vedere i tasti di scelta rapida per i comandi all'interno dei risultati della ricerca Visual Studio in modo da memorizzarli più facilmente. 

- **Mock code using task list**. Se non si hanno requisiti sufficienti per completare una parte di codice, usare Elenco attività per tenere traccia dei commenti del codice che usano token come e o token personalizzati e per gestire i collegamenti che guidano direttamente a una posizione predefinita nel `TODO` `HACK` codice. Per altre informazioni, vedere [Usare il Elenco attività](../ide/using-the-task-list.md).

- **Usare i Esplora soluzioni seguenti.** Se non si ha di Visual Studio, questi tasti di scelta rapida saranno utili e permetteranno di risparmiare tempo mentre si è in grado di velocizzare una nuova codebase. Per l'elenco completo dei tasti di scelta rapida, vedere [Tasti di scelta rapida predefiniti in Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL).

- **[Identificare e personalizzare i tasti di scelta rapida in Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)**. È possibile identificare i tasti di scelta rapida per i comandi di Visual Studio, personalizzarli ed esportarli per consentirne l'utilizzo ad altri utenti. È sempre possibile trovare e modificare un tasto di scelta rapida nella finestra di dialogo Opzioni.

- **Rendere Visual Studio più accessibile.** Visual Studio dispone di funzionalità di accessibilità integrate compatibili con utilità per la lettura dello schermo e altri tipi di Assistive Technology Program. Per [l'elenco completo delle funzionalità disponibili, Visual Studio](../ide/reference/accessibility-tips-and-tricks.md) suggerimenti sull'accessibilità per altre informazioni. 

- **Vedere l'articolo Visual Studio ciclo di vita e manutenzione del prodotto.** Per informazioni su come ottenere gli aggiornamenti per Visual Studio, le opzioni di supporto per i clienti Enterprise e Professional, il supporto per le versioni precedenti di Visual Studio e i componenti non coperti dalla manutenzione di Visual Studio, vedere Ciclo di vita e manutenzione del prodotto [Visual Studio.](/visualstudio/releases/2019/servicing) 

- **Installare e gestire NuGet pacchetti in Visual Studio**. L'interfaccia utente di Gestione pacchetti NuGet in Visual Studio in Windows consente di installare, disinstallare e aggiornare facilmente i pacchetti NuGet in progetti e soluzioni. Per altre informazioni, vedere [Install and manage packages in Visual Studio using the NuGet Gestione pacchetti](/nuget/consume-packages/install-use-packages-visual-studio).

## <a name="write-code"></a>Scrittura di codice

È possibile scrivere il codice più rapidamente tramite le seguenti funzionalità.

- **Usare i comandi di comodità**. Visual Studio include vari comandi che consentono di eseguire attività di modifica comuni più velocemente. Ad esempio, è possibile scegliere un comando per duplicare facilmente una riga di codice senza doverla copiare, modificare la posizione del cursore e quindi incollarla. Scegliere **Modifica**  >  **duplicato** o **premere CTRL** + **E**,**V**. È anche possibile espandere o comprimere rapidamente una selezione di testo scegliendo Modifica selezione avanzata Espandi selezione o Modifica selezione contratto avanzata oppure premendo  >    >     >    >   **MAIUSC** + **ALT** + **=** o **MAIUSC** +  + **-** ALT.

- **Usare IntelliSense.** Quando si immette il codice nell'editor, vengono visualizzate alcune informazioni di IntelliSense, come Elenca membri, Informazioni sul parametro, Informazioni rapide, Supporto firma e Completa parola. Queste funzionalità supportano la corrispondenza fuzzy del testo. Ad esempio, gli elenchi di risultati per Elenca membri includono non solo le voci che iniziano con i caratteri immessi, ma anche le voci che contengono la combinazione di caratteri in un punto qualsiasi dei nomi. Per altre informazioni, vedere [Utilizzo di IntelliSense](../ide/using-intellisense.md).

- **Modifica dell'inserimento automatico delle opzioni IntelliSense durante l'immissione del codice**. Se si attiva la modalità di suggerimento di IntelliSense, è possibile specificare che le opzioni IntelliSense vengano inserite solo se si scelgono in modo esplicito.

     Per abilitare la modalità di suggerimento, premere **CTRL** ALT+BARRA SPAZIATRICE oppure, sulla barra dei menu, scegliere Modifica +  +    >  **IntelliSense**  >  **Attiva/Disattiva modalità di completamento** IntelliSense.

- **Usare frammenti di codice**. È possibile usare frammenti di codice predefiniti o creare frammenti di codice personalizzati.

     Per inserire un frammento di codice, sulla barra dei menu scegliere Modifica Frammento di codice  >  **IntelliSense** Inserisci frammento o Racchiude tra oppure aprire il menu di scelta rapida in un file e scegliere Inserisci frammento di codice o Racchiude  >      >   tra.  Per altre informazioni, vedere [Code Snippets](../ide/code-snippets.md) (Frammenti di codice).

- **Correzione di errori di codice inline**. Le azioni rapide consentono di generare codice, effettuarne il refactoring o modificarlo in altro modo con facilità tramite un'unica azione. Queste azioni possono essere applicate usando l'icona a forma di cacciavite o la lampadina Icone icona lampadina oppure premendo ![ ](media/screwdriver-icon.png) ALT ![ ](media/light-bulb-icon.png)  + **INVIO** o  + **CTRL.** quando il cursore si trova sulla riga di codice appropriata. Per altre informazioni, vedere [Azioni rapide](quick-actions.md).

- **Visualizzazione e modifica della definizione di un elemento di codice**. È possibile visualizzare e modificare rapidamente il modulo in cui viene definito un elemento di codice, ad esempio un membro, una variabile o un elemento locale.

    Per aprire una definizione in una finestra popup, evidenziare l'elemento e quindi premere + **ALT F12** oppure aprire il menu di scelta rapida per l'elemento e quindi scegliere **Visualizza definizione.** Per aprire una definizione in una finestra di codice separata, aprire il menu di scelta rapida per l'elemento e quindi scegliere **Vai a definizione**.

- **Uso di applicazioni di esempio**. È possibile velocizzare lo sviluppo di applicazioni scaricando e installando applicazioni di esempio da [Microsoft Developer Network](https://code.msdn.microsoft.com/). È inoltre possibile capire un particolare concetto di programmazione o tecnologico, scaricando e esplorando un Pacchetto di esempi di un'area.

- **Modificare la formattazione delle parentesi graffe con Formattazione/Nuove righe**. Usare la **pagina Opzioni**  di formattazione per impostare le opzioni per la formattazione del codice nell'editor del codice, incluse le nuove righe. Per altre informazioni su come usare questa impostazione in C#, vedere Finestra di dialogo Opzioni: Editor di testo > [C# > Stile](../ide/reference/options-text-editor-csharp-formatting.md)codice > formattazione . Per C++, vedere [Impostare le preferenze di scrittura del codice C++ in Visual Studio](/cpp/ide/how-to-set-preferences). Per Python, vedere [Formattare il codice Python.](../python/formatting-python-code.md)

- **Modificare il rientro con Tabulazioni.** Usare impostazioni dell'editor personalizzate, personalizzate per ogni codebase, per applicare stili di codifica coerenti per più sviluppatori che lavorano sullo stesso progetto in editor e ID diversi. Assicurarsi che l'intero team segua le stesse convenzioni del linguaggio, le stesse convenzioni di denominazione e le stesse regole di formattazione. Poiché queste impostazioni personalizzate sono portabili e si spostano con il codice, è possibile applicare stili di codifica anche all'esterno Visual Studio. Per altre informazioni, vedere [Opzioni, Editor di testo, Tutti i linguaggi, Schede.](../ide/reference/options-text-editor-all-languages-tabs.md#tabs)

## <a name="navigate-within-your-code-and-the-ide"></a>Spostarsi all'interno del codice e dell'IDE

È possibile utilizzare varie tecniche per trovare e spostarsi in punti specifici del codice più rapidamente. È anche possibile modificare il layout delle finestre Visual Studio in base alle preferenze. 

- **Inserimento di un segnalibro per le righe di codice**. È possibile utilizzare i segnalibri per passare rapidamente alle righe di codice specifiche in un file.

    Per impostare un segnalibro, sulla barra dei menu scegliere **Modifica**  >  **segnalibri**  >  **Attiva/Disattiva segnalibro.** È possibile visualizzare tutti i segnalibri per una soluzione nella finestra **Segnalibri**. Per altre informazioni, vedere [Impostazione di segnalibri nel codice](../ide/setting-bookmarks-in-code.md).

- **Ricerca delle definizioni dei simboli in un file**. Sebbene sia possibile cercare all'interno di una soluzione definizioni di simboli e nomi file, i risultati della ricerca non includono gli spazi dei nomi o le variabili locali.

   Per accedere a questa funzionalità, sulla barra dei menu scegliere **Modifica**  >  **Passa a.**

- **Esplorazione della struttura generale del codice**. In **Esplora soluzioni** è possibile cercare e visualizzare le classi e i relativi tipi e membri nei progetti. È anche possibile cercare simboli, visualizzare la gerarchia di chiamata di un metodo, trovare i riferimenti dei simboli ed eseguire altre attività. Se si sceglie un elemento di codice in **Esplora soluzioni**, il file associato viene visualizzato nella scheda **Anteprima** e il cursore si sposta sull'elemento nel file. Per altre informazioni, vedere [Visualizzazione della struttura del codice](../ide/viewing-the-structure-of-code.md).

- **Passare a una posizione in un file con la modalità mappa**. La modalità mappa visualizza le righe di codice, in miniatura, sulla barra di scorrimento. Per altre informazioni su questa modalità di visualizzazione, [vedere Procedura: Personalizzare la barra di scorrimento.](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md#map-mode)

- **Comprendere la struttura del codice con la mappa codice**. Le mappe codice consentono di visualizzare le dipendenze all'interno del codice e di vedere come si adattano senza leggere file e righe di codice. Per altre informazioni, vedere [Mappare le dipendenze con le mappe del codice](../modeling/map-dependencies-across-your-solutions.md).

- **Vedere i file usati di frequente con Modifica/Vai al file recente.** Usare i comandi Vai a in Visual Studio eseguire una ricerca mirata del codice per trovare rapidamente gli elementi specificati. Per istruzioni dettagliate, vedere [Trovare il codice usando i comandi Vai a](../ide/go-to.md).

- **Spostare il [Finestra Proprietà](../ide/reference/properties-window.md) sul lato destro.** Se si sta cercando un layout di finestra più familiare, è possibile spostare il Finestra Proprietà in Visual Studio **premendo F4.**

## <a name="find-items-faster"></a>Ricerca di elementi più veloce

È possibile cercare nell'IDE comandi, file e opzioni, oltre a filtrare il contenuto delle finestre degli strumenti per visualizzare solo informazioni rilevanti per l'attività corrente.

- **Applicazione di filtri al contenuto delle finestre degli strumenti**. È possibile eseguire ricerche nel contenuto di molte finestre degli strumenti, come **Casella degli strumenti**, finestra **Proprietà** ed **Esplora soluzioni**, ma visualizzare solo gli elementi i cui nomi contengono i caratteri specificati.

- **Visualizzazione dei soli errori da risolvere**. Se si sceglie il pulsante **Filtro** nella barra degli strumenti **Elenco errori**, è possibile ridurre il numero di errori visualizzati nella finestra **Elenco errori**. È possibile visualizzare solo gli errori nei file aperti nell'editor, solo gli errori nel file corrente o solo gli errori nel progetto corrente. È anche possibile eseguire ricerche all'interno **della finestra Elenco** errori per trovare errori specifici.

- **Ricerca di finestre di dialogo, comandi di menu, opzioni e altro**. Nella casella di ricerca immettere le frasi o le parole chiave per gli elementi da trovare. Se ad esempio si digita **nuovo progetto** vengono visualizzate le opzioni seguenti:

   ::: moniker range="vs-2017"

   ![Risultati di Avvio veloce per il nuovo progetto](../ide/media/productivity_quicklaunch.png)

   **Avvio veloce** visualizza, tra gli altri, collegamenti per creare un nuovo progetto, aggiungere un nuovo elemento a un progetto e per la pagina **Progetti e soluzioni** della finestra di dialogo **Opzioni**. I risultati della ricerca possono includere anche file di progetto e finestre degli strumenti.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Risultati di ricerca per 'nuovo progetto'](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Premere **CTRL** + **Q per** passare direttamente alla casella di ricerca.

## <a name="debug-code"></a>Debug del codice

Il debug può richiedere molto tempo, ma i suggerimenti seguenti consentono di velocizzare il processo.

- **Usare gli strumenti Visual Studio debugger .** Nel contesto Visual Studio, quando si esegue il *debug dell'app*, in genere significa che l'applicazione viene eseguita in modalità debugger. Il debugger offre molti modi per visualizzare le operazioni del codice durante l'esecuzione. Per [una guida introduttiva, vedere Visual Studio Debugger.](../debugger/debugger-feature-tour.md) 

- **Verifica della stessa pagina, applicazione o sito in diversi browser**. Quando si esegue il debug del codice, è possibile passare facilmente da un Web browser installato all'altro, compreso [Controllo pagina (Visual Studio)](/previous-versions/hh974728(v=vs.140)), senza dover aprire la finestra di dialogo **Esplora con**. È possibile usare l'elenco **Destinazione** di debug,  disponibile sulla barra degli strumenti **Standard** accanto al pulsante Avvia debug, per verificare rapidamente il browser in uso durante il debug o la visualizzazione delle pagine.

    ![Selezionare opzioni di debug del Web browser](../ide/media/webbrowserdropdowntoolbar.png)

- **Impostazione di punti di interruzione temporanei**. È possibile creare un punto di interruzione temporaneo nella riga di codice corrente e avviare contemporaneamente il debugger. Quando si raggiunge la riga di codice, viene attivata la modalità di interruzione del debugger. Per altre informazioni, vedere [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md).

    Per usare questa funzionalità, scegliere i tasti **CTRL** + **F10** oppure aprire il menu di scelta rapida per la riga di codice in cui si vuole interrompere l'esecuzione e quindi scegliere Esegui fino al **cursore**.

- **Spostamento del punto di esecuzione durante il debug**. È possibile spostare il punto di esecuzione corrente in un'altra sezione del codice e quindi riavviare il debug da tale punto. Questa tecnica è utile se si desidera eseguire il debug di una sezione di codice senza dover ricreare tutti i passaggi necessari per raggiungere la sezione. Per altre informazioni, vedere [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md).

     Per spostare il punto di esecuzione, trascinare la freccia gialla nella posizione in cui si desidera impostare l'istruzione successiva nello stesso file di origine e quindi premere **F5** per continuare il debug.

- **Acquisizione di informazioni sui valori per le variabili**. È possibile aggiungere un suggerimento dati a una variabile nel codice e bloccarlo in modo da poter accedere all'ultimo valore noto della variabile al termine del debug. Per altre informazioni, vedere [View data values in Data Tips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) (Visualizzare i valori di dati nei suggerimenti dati).

     Per aggiungere un suggerimento dati, il debugger deve essere in modalità di interruzione. Posizionare il cursore sulla variabile e quindi scegliere il pulsante del blocco sul suggerimento dati visualizzato. Quando il debug viene arrestato, viene visualizzata un'icona a forma di puntina da disegno blu nel file di origine accanto alla riga di codice che contiene la variabile. Se si posiziona il puntatore del mouse su tale icona, viene visualizzato il valore della variabile della sessione di debug più recente.

- **Cancellazione della finestra di controllo immediato**. È possibile cancellare il contenuto della finestra [Controllo immediato in](../ide/reference/immediate-window.md) fase di progettazione `>cls` immettendo o `>Edit.ClearAll`

     Per altre informazioni sui comandi aggiuntivi, vedere [Visual Studio alias dei comandi](../ide/reference/visual-studio-command-aliases.md).

- **[Trovare le modifiche al codice e altre cronologia con CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)**. CodeLens consente di rimanere concentrati sulle proprie attività mentre si cercano informazioni sul codice senza uscire dall'editor. È possibile trovare i riferimenti a un frammento di codice, le modifiche apportate al codice, i bug collegati, gli elementi di lavoro, le revisioni del codice e gli unit test.

- **Usare Live Share per eseguire il debug in tempo reale con altri .** Live Share consente di modificare ed eseguire il debug in collaborazione con altri utenti in tempo reale, indipendentemente dal linguaggio di programmazione usato o dai tipi di app da creare. Per altre informazioni, vedere [Informazioni Visual Studio Live Share?](/visualstudio/liveshare/)

- **Usare La finestra interattiva per scrivere e testare codice di piccole dimensioni.** Visual Studio una finestra interattiva read-evaluate-print-loop (REPL) che consente di immettere codice arbitrario e visualizzare risultati immediati. Questo modo di scrivere codice consente di apprendere e sperimentare le API e le librerie e di sviluppare in modo interattivo codice funzionante da includere nei progetti. Per Python, vedere [Usare python finestra interattiva](../python/python-interactive-repl-in-visual-studio.md). La funzionalità Finestra interattiva è disponibile anche per C#. 

## <a name="access-visual-studio-tools"></a>Accesso agli strumenti di Visual Studio

È possibile accedere rapidamente al prompt dei comandi per gli sviluppatori o a un altro strumento di Visual Studio se lo si aggiunge nel menu di avvio o nella barra delle applicazioni.

::: moniker range="vs-2017"

1. In Esplora risorse passare a *%ProgramData%\Microsoft\Windows\Menu Start\Programmi\Visual Studio 2017\Strumenti di Visual Studio*.

::: moniker-end

::: moniker range=">=vs-2019"

1. In Esplora risorse passare a *%ProgramData%\Microsoft\Windows\Menu Start\Programmi\Visual Studio 2019\Strumenti di Visual Studio*.

::: moniker-end

2. Fare clic con il pulsante destro del mouse o aprire il menu di scelta rapida per visualizzare il **prompt dei comandi per sviluppatori**, quindi scegliere **Aggiungi a Start** o **Aggiungi alla barra delle applicazioni**.

## <a name="manage-files-toolbars-and-windows"></a>Gestione di file, barre degli strumenti e finestre

In qualsiasi momento, durante lo sviluppo di un'applicazione è possibile che sia necessario lavorare in più file di codice e spostarsi tra diverse finestre degli strumenti. I suggerimenti riportati di seguito consentono di organizzare al meglio le attività da eseguire:

- **Blocco della visualizzazione dei file usati di frequente nell'editor**. È possibile aggiungere i file a sinistra della scheda in modo che rimangano visibili indipendentemente dal numero di file aperti nell'editor.

   Per aggiungere un file, scegliere la scheda del file e quindi scegliere il pulsante **Attiva/Disattiva stato** pin.

- **Spostamento di documenti e finestre in altri monitor**. Se si utilizza più di un monitor durante lo sviluppo delle applicazioni, è possibile gestire più facilmente le parti dell'applicazione spostando i file aperti nell'editor in un altro monitor. È anche possibile spostare le finestre degli strumenti, ad esempio le finestre del debugger, in un altro monitor e ancorare le finestre degli strumenti e dei documenti per creare raggruppamenti. Per altre informazioni, vedere [Personalizzazione del layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

   È anche possibile gestire i file più facilmente creando un'altra istanza di **Esplora soluzioni** e spostandola in un altro monitor. Per creare un'altra istanza di **Esplora soluzioni**, aprire un menu di scelta rapida in **Esplora soluzioni** e quindi scegliere **Nuova visualizzazione Esplora soluzioni**.

- **Personalizzazione di tipi di carattere in Visual Studio**. È possibile modificare il tipo di carattere, la dimensione e il colore usato per il testo nell'IDE. Ad esempio, è possibile personalizzare il colore degli elementi di codice specifici nell'editor e il tipo di carattere nelle finestre degli strumenti o nell'IDE. Per altre informazioni, vedere [Procedura: Modificare tipi](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) di carattere e colori e [Procedura: Modificare tipi di carattere e colori nell'editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Vedi anche

- [Post di blog di suggerimenti e consigli per Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Tasti di scelta rapida predefiniti per i comandi usati di frequente](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Procedura: Personalizzare menu e barre degli strumenti](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Procedura dettagliata: Creare un'applicazione semplice](../get-started/csharp/tutorial-wpf.md)
- [Suggerimenti sull'accessibilità](../ide/reference/accessibility-tips-and-tricks.md)