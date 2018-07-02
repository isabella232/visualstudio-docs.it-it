---
title: Panoramica di Visual Studio 2017
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- MSDNSTART
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a7667cac2a26a3e98d2e92dfeb13cee36d870e9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691160"
---
# <a name="visual-studio-ide-overview"></a>Panoramica dell'ambiente IDE di Visual Studio

L'ambiente IDE (Interactive Development Environment) di Visual Studio è un ambiente di sviluppo integrato, ovvero una superficie creativa utilizzabile per visualizzare e modificare il codice e quindi eseguire il debug, la compilazione e la pubblicazione di un'app.

Visual Studio è disponibile per Windows e Mac. [Visual Studio per Mac](/visualstudio/mac/) include numerose funzionalità di Visual Studio 2017 ed è ottimizzato per lo sviluppo di app multipiattaforma e per dispositivi mobili.

Questo articolo descrive Visual Studio 2017 per Windows. Vengono illustrate le funzionalità di base dell'IDE. Verranno esaminate alcune operazioni che è possibile eseguire con Visual Studio che comprendono la creazione di un progetto semplice usando IntelliSense come supporto per la codifica e il debug di un'app per visualizzare il valore di una variabile durante l'esecuzione del programma. Vengono anche descritte le diverse finestre dello strumento.

## <a name="install-the-visual-studio-ide"></a>Installare l'IDE di Visual Studio

Per iniziare, [scaricare Visual Studio 2017](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) e installarlo nel sistema.

Il programma di installazione modulare consente di scegliere e installare specifici *carichi di lavoro*, ovvero gruppi di funzionalità necessarie per il linguaggio di programmazione o la piattaforma preferiti. Per seguire la procedura per la [creazione di un programma](#create-a-program) assicurarsi di selezionare il carico di lavoro **Sviluppo multipiattaforma .NET Core** durante l'installazione. Gli argomenti introduttivi, ad esempio [Introduzione a C++ in Visual Studio](getting-started-with-cpp-in-visual-studio.md), contengono le istruzioni per l'installazione di altri carichi di lavoro.

![Programma di installazione di Visual Studio](../ide/media/overview-net-core-workload.png)

Al primo avvio di Visual Studio, è possibile scegliere facoltativamente di accedere con l'account Microsoft o con l'account aziendale o dell'istituto di istruzione.

## <a name="tour-of-the-ide"></a>Presentazione dell'IDE

Per offrire una panoramica visiva di Visual Studio ad alto livello, l'immagine seguente mostra Visual Studio con un progetto aperto e varie finestre di strumenti fondamentali di uso estremamente probabile:

![IDE di Visual Studio](../ide/media/visualstudioide.png)

- [Esplora soluzioni](../ide/solutions-and-projects-in-visual-studio.md) consente di visualizzare, esplorare e gestire i file del codice. Esplora soluzioni consente di organizzare il codice raggruppando i file in soluzioni e progetti.

- La finestra dell'[editor](../ide/writing-code-in-the-code-and-text-editor.md), in cui probabilmente si trascorre la maggior parte del tempo, visualizza il codice e consente di modificare il codice sorgente e di progettare l'interfaccia utente.

- La finestra [Output](../ide/reference/output-window.md) è la finestra in cui Visual Studio invia le notifiche, ad esempio messaggi di errore e di debug, avvisi del compilatore, messaggi di stato di pubblicazione e altro. Ogni messaggio viene visualizzato in una scheda separata.

- [Team Explorer (VSTS)](/vsts/user-guide/work-team-explorer) consente di tenere traccia degli elementi di lavoro e di condividere il codice con altri utenti usando tecnologie di controllo della versione come [Git](https://git-scm.com/) e [Team Foundation Version Control (TFVC)](/vsts/tfvc/overview).

Di seguito sono illustrate alcune altre funzionalità di produttività comuni in Visual Studio:

- [Refactoring](../ide/refactoring-in-visual-studio.md) include operazioni come la ridenominazione intelligente delle variabili, lo spostamento delle righe di codice selezionate in funzioni separate, lo spostamento di codice in altre posizioni, il riordinamento dei parametri di funzione e altro ancora.

   ![Refactoring](../ide/media/VSIDE_refactor.png)

- [IntelliSense](../ide/using-intellisense.md) è un termine generico che comprende diverse funzionalità comuni che visualizzano le informazioni sul tipo di codice direttamente nell'editor e, in alcuni casi, scrivono automaticamente piccole parti di codice. È come se si avesse a disposizione la documentazione di base all'interno dell'editor, senza dover cercare le informazioni sul tipo in una finestra della Guida separata. Le funzionalità di IntelliSense variano a seconda del linguaggio. Per altre informazioni, vedere [IntelliSense per C#](../ide/visual-csharp-intellisense.md), [IntelliSense per Visual C++](../ide/visual-cpp-intellisense.md), [IntelliSense per JavaScript](../ide/javascript-intellisense.md) e [IntelliSense per Visual Basic](../ide/visual-basic-specific-intellisense.md). La figura seguente illustra alcune funzionalità di IntelliSense:

   ![Elenco dei membri di Visual Studio](../ide/media/vs2017_Intellisense.png)

- La casella di ricerca [Avvio veloce](../ide/reference/quick-launch-environment-options-dialog-box.md) è un ottimo modo per trovare rapidamente quello che serve in Visual Studio. È sufficiente digitare il nome dell'elemento che si sta cercando per visualizzare risultati da cui è possibile passare direttamente all'elemento desiderato. In **Avvio veloce** sono visualizzati anche collegamenti per avviare il **Programma di installazione di Visual Studio** per qualsiasi carico di lavoro o singolo componente.

   ![Casella di ricerca di Avvio veloce](../ide/media/VSIDE_Tour_QuickLaunch.png)

- Le **linee a zigzag** sono sottolineature ondulate che segnalano errori o problemi potenziali nel codice in tempo reale durante la digitazione e consentono di risolverli immediatamente senza attendere che vengano rilevati durante la fase di compilazione o di esecuzione. Se si passa il mouse su una linea a zigzag, vengono visualizzate informazioni aggiuntive sull'errore. Sul margine sinistro può essere visualizzata anche una lampadina con le azioni per risolvere l'errore. Per altre informazioni, vedere [Azioni rapide](../ide/quick-actions.md).

   ![Linee a zigzag](../ide/media/vs2017_squiggle.png)

- Nel menu di scelta rapida dell'editor di testo è possibile aprire la finestra [Gerarchia di chiamata](../ide/reference/call-hierarchy.md) per visualizzare i metodi che chiamano e vengono chiamati dal metodo sotto il cursore (punto di inserimento).

   ![Finestra Gerarchia di chiamata](../ide/media/VSIDE_call_hierarchy.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) consente di trovare i riferimenti e le modifiche al codice, i bug collegati, gli elementi di lavoro, le revisioni del codice e gli unit test senza uscire dall'editor.

   ![CodeLens](../ide/media/codelensoverview.png)

- La finestra [Visualizza definizione](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) mostra un metodo o una definizione di tipo inline senza uscire dal contesto corrente.

   ![Visualizza definizione](../ide/media/VSIDE_peek_definition.png)

- L'opzione del menu di scelta rapida [Vai a definizione](../ide/go-to-and-peek-definition.md) visualizza direttamente la posizione in cui è definita la funzione o l'oggetto. Facendo clic con il pulsante destro del mouse nell'editor sono disponibili anche altri comandi di spostamento.

   ![Vai a definizione](../ide/media/VSIDE_go_to_definition.png)

## <a name="create-a-program"></a>Creare un programma

In questa sezione viene descritta in dettaglio la procedura per creare un nuovo semplice programma.

1. Aprire Visual Studio. Scegliere **File** > **Nuovo** > **Progetto** dal menu.

  ![File > Nuovo progetto sulla barra dei menu](../ide/media/VSIDE_Tour_NewProject1.png)

1. Viene visualizzata la finestra di dialogo **Nuovo progetto** con vari *modelli* di progetto. Un modello contiene i file di base e le impostazioni necessarie per un determinato tipo di progetto. Scegliere la categoria **.NET Core** in **Visual C#** e quindi scegliere il modello **App console (.NET Core)**. Nella casella di testo **Nome** digitare **HelloWorld** e quindi selezionare il pulsante **OK**.

  ![Modello di app .NET Core](../ide/media/overview-new-project-dialog.png)

   Visual Studio crea il progetto. È una semplice applicazione "Hello World" che chiama il metodo <xref:System.Console.WriteLine?displayProperty=nameWithType> per visualizzare il valore letterale stringa "Hello World!" nella finestra della console.

  > [!NOTE]
  > Se non viene visualizzata la categoria **.NET Core** è necessario installare il carico di lavoro **Sviluppo multipiattaforma .NET Core**. A tale scopo, scegliere il collegamento **Apri il programma di installazione di Visual Studio** in basso a sinistra nella finestra di dialogo **Nuovo progetto**. Dopo l'apertura del **Programma di installazione di Visual Studio** selezionare il carico di lavoro **Sviluppo multipiattaforma .NET Core** e quindi scegliere **Modifica**.

   Il risultato visualizzato a breve dovrebbe essere simile al seguente:

   ![IDE di Visual Studio](../ide/media/overview-ide-console-app.png)

   Il codice C# per l'applicazione viene visualizzato nella finestra dell'editor, che occupa la maggior parte dello spazio. Si noti che il testo viene colorato automaticamente per indicare i diversi aspetti del codice, ad esempio parole chiave e tipi. Le piccole linee tratteggiate verticali nel codice indicano inoltre le parentesi graffe corrispondenti e i numeri di riga facilitano l'individuazione del codice in un secondo momento. È possibile scegliere i piccoli segni meno racchiusi in un riquadro per comprimere o espandere il codice. Questa funzionalità per la strutturazione del codice consente di nascondere il codice non necessario, migliorando la leggibilità del contenuto visualizzato sullo schermo.

   I file del progetto sono elencati sul lato destro in una finestra denominata **Esplora soluzioni**.

  ![IDE di Visual Studio con caselle rosse](../ide/media/overview-ide-console-app-red-boxes.png)

  Sono disponibili altri menu e finestre degli strumenti, ma per il momento si procederà con la creazione del programma.

1. Avviare l'app. È possibile farlo scegliendo **Avvia senza eseguire debug** dal menu **Debug** sulla barra dei menu. È anche possibile premere **CTRL**+**F5**.

  ![Menu Debug > Avvia senza eseguire debug](../ide/media/overview-start-without-debugging.png)

  Visual Studio compila l'app e apre una finestra della console con il messaggio **Hello World!**. Ed ecco un'app in esecuzione.

  ![Finestra della console](../ide/media/overview-console-window.png)

1. Per chiudere la finestra della console, premere un tasto qualsiasi.

1. A questo punto verrà aggiunto ulteriore codice per l'app. Aggiungere il codice C# seguente prima della riga `Console.WriteLine("Hello World!");`:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Il codice visualizza **What is your name?** nella finestra della console e attende che l'utente immetta testo seguito da **INVIO**.

1. Modificare la riga `Console.WriteLine("Hello World!");` con il codice seguente:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Eseguire nuovamente l'app selezionando **Debug** > **Avvia senza eseguire debug** o premendo **CTRL**+**F5**.

   Visual Studio ricompila l'app, viene aperta una finestra della console e viene richiesto il nome.

1. Immettere il nome nella finestra della console e premere **INVIO**.

   ![Input nella finestra della console](media/overview-console-input.png)

1. Premere un tasto qualsiasi per chiudere la finestra della console e arrestare l'esecuzione del programma.

## <a name="use-refactoring-and-intellisense"></a>Usare refactoring ed esplorazione

Di seguito sono descritti due modi in cui è possibile usare il [refactoring](refactoring-in-visual-studio.md) e [IntelliSense](using-intellisense.md) per creare codice in modo più efficace.

In primo luogo, rinominare la variabile `name`:

1. Fare doppio clic sulla variabile `name` per selezionarla.

1. Digitare il nuovo nome per la variabile, `username`.

   Si noti che viene visualizzata una casella grigia intorno a variabile e una lampadina viene visualizzata nel margine.

1. Selezionare l'icona lampadina per visualizzare le [azioni rapide](quick-actions.md) disponibili. Selezionare **Rinomina 'nome' in 'nomeutente'**.

   ![Rinominare l'azione in Visual Studio](media/rename-quick-action.png)

   La variabile viene rinominata all'interno del progetto, ovvero in questo caso in due posizioni.

   ![Gif animata che mostra il refactoring di ridenominazione in Visual Studio](media/rename-refactoring.gif)

1. Si esamini ora IntelliSense. Sotto la riga`Console.WriteLine($"\nHello {username}!");` digitare **DateTime now = DateTime.**.

   Una casella visualizza i membri della classe <xref:System.DateTime>. In una casella separata viene visualizzata anche la descrizione del membro correntemente selezionato.

   ![Membri dell'elenco di IntelliSense in Visual Studio](media/intellisense-list-members.png)

1. Selezionare il membro denominato **Now** che è una proprietà della classe facendo doppio clic su di esso oppure premendo **TAB**. Completare la riga di codice aggiungendo un punto e virgola **;**.

1. Nella parte sottostante digitare o copiare le righe di codice seguenti:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> è leggermente diverso da <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> in quanto non aggiunge un terminatore di riga dopo la stampa. Ciò significa che la parte successiva del testo che viene inviata all'output verrà stampata sulla stessa riga. È possibile passare il mouse su ognuno di questi metodi nel codice per visualizzarne la descrizione.

1. Successivamente, verrà nuovamente usato il refactoring per rendere più breve il codice. Fare clic sulla variabile `now` nella riga `DateTime now = DateTime.Now;`.

   Viene visualizzata una piccola icona cacciavite nel margine della riga.

1. Fare clic sull'icona cacciavite per visualizzare i suggerimenti disponibili in Visual Studio. In questo caso è visualizzato il refactoring [Variabile temporanea inline](reference/inline-temporary-variable.md) per rimuovere una riga di codice senza modificare il comportamento complessivo:

   ![Refactoring Variabile temporanea Inline in Visual Studio](media/inline-temporary-variable-refactoring.png)

1. Fare clic su **Variabile temporanea inline** per effettuare il refactoring del codice.

1. Eseguire nuovamente il programma premendo **CTRL**+**F5**. L'output è simile al seguente:

   ![Finestra della console con output del programma](../ide/media/overview-console-final.png)

## <a name="debug-code"></a>Debug del codice

Durante la scrittura del codice è necessario eseguirlo e testarlo per individuare eventuali bug. Il sistema di debug di Visual Studio consente di esaminare il codice un'istruzione alla volta e controllare le variabili man mano. È possibile impostare punti di interruzione che vengono raggiunti solo quando viene soddisfatta una condizione specificata. È possibile monitorare i valori delle variabili durante l'esecuzione del codice e altri aspetti.

Impostare un punto di interruzione per visualizzare il valore della variabile `username` mentre il programma è "in corso".

1. Individuare la riga di codice `Console.WriteLine($"\nHello {username}!");`. Per impostare un punto di interruzione nella riga di codice, ovvero per sospendere l'esecuzione del programma in corrispondenza della riga, fare clic sul margine di sinistra dell'editor. È anche possibile fare clic su un punto qualsiasi della riga di codice e quindi premere **F9**.

   Viene visualizzato un cerchio rosso nel margine di sinistra e il codice viene evidenziato in rosso.

   ![Punto di interruzione nella riga di codice in Visual Studio](media/breakpoint.png)

1. Avviare il debug selezionando **Debug** > **Avvia debug** o premendo **F5**.

1. Quando viene visualizzata la finestra della console e viene chiesto di immettere il nome, digitarlo e premere **INVIO**.

   Si noti che lo stato attivo torna all'editor di codice di Visual Studio e la riga di codice con il punto di interruzione viene evidenziata in giallo. Ciò significa che la riga è la successiva riga di codice eseguita dal programma.

1. Passare il mouse sulla variabile `username` per impostarne il valore. In alternativa, è possibile fare clic con il pulsante destro del mouse su `username` e selezionare **Aggiungi espressione di controllo** per aggiungere la variabile nella finestra **Espressione di controllo** in cui è possibile visualizzarne anche il valore.

   ![Valore della variabile durante il debug in Visual Studio](media/debugging-variable-value.png)

1. Per consentire il completamento dell'esecuzione del programma, premere di nuovo **F5**.

Per altri dettagli sul debug in Visual Studio, vedere [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Personalizzare Visual Studio

È possibile personalizzare l'IDE e modificare il tema colori predefinito. Per modificare il tema **Scuro**:

1. Dalla barra dei menu scegliere **Strumenti** > **Opzioni** per aprire la finestra di dialogo **Opzioni**.

1. Nella pagina delle opzioni **Ambiente** > **Generale** modificare la selezione del **Tema colori** in **Scuro** e quindi scegliere **OK**.

   Viene applicato il tema colori **Scuro** all'intero ambiente IDE.

   ![Visual Studio con tema Scuro](media/quickstart-personalize-dark-theme.png)

Per informazioni su altri modi per personalizzare l'IDE, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="learn-more"></a>Altre informazioni

È possibile creare un'app per un telefono Android o iOS o creare un gioco 3D o un'app cloud. Per informazioni su queste e altre funzionalità di Visual Studio, vedere [Funzionalità di Visual Studio 2017](../ide/advanced-feature-overview.md).

Se si è pronti per iniziare a scrivere codice, scegliere uno degli argomenti della Guida introduttiva dal sommario, ad esempio [Usare Visual Studio per creare la prima app Web ASP.NET Core](quickstart-aspnet-core.md).

Guardare anche i corsi gratuiti su Visual Studio disponibili in [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033).

## <a name="see-also"></a>Vedere anche

* [Altre funzionalità di Visual Studio](../ide/advanced-feature-overview.md)
* [www.visualstudio.com](https://www.visualstudio.com/vs/)
* [Blog di Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
* [Download di Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)