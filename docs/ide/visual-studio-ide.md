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
ms.openlocfilehash: 5647bbc6aa520fdf5427b61f53a54c28b9a0a48d
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381172"
---
# <a name="visual-studio-overview"></a>Panoramica di Visual Studio

L'*ambiente di sviluppo integrato (IDE)* di Visual Studio è un'area di avvio creativa che consente di modificare, eseguire il debug, compilare il codice e quindi pubblicare un'app. Un ambiente di sviluppo integrato (IDE) è un programma con numerose funzionalità che può essere usato per molti aspetti dello sviluppo software. A differenza dell'editor e del debugger standard disponibili nella maggior parte degli ambienti IDE, Visual Studio include compilatori, strumenti di completamento codice, finestre di progettazione con interfaccia grafica e altre funzionalità che semplificano il processo di sviluppo del software.

Visual Studio è disponibile per Windows e Mac. [Visual Studio per Mac](/visualstudio/mac/) include numerose funzionalità di Visual Studio 2017 ed è ottimizzato per lo sviluppo di app multipiattaforma e per dispositivi mobili.

Questo articolo descrive Visual Studio 2017 per Windows. Vengono illustrate le funzionalità di base dell'IDE. Verranno esaminate alcune operazioni che è possibile eseguire con Visual Studio che comprendono la creazione di un progetto semplice, l'utilizzo di [IntelliSense](using-intellisense.md) come supporto per la creazione del codice e il debug di un'app per visualizzare il valore di una variabile durante l'esecuzione del programma. Vengono anche descritte le diverse finestre dello strumento.

## <a name="install-the-visual-studio-ide"></a>Installare l'IDE di Visual Studio

Per iniziare, [scaricare Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) e installarlo nel sistema.

Il programma di installazione modulare consente di scegliere e installare specifici *carichi di lavoro*, ovvero gruppi di funzionalità necessarie per il linguaggio di programmazione o la piattaforma preferiti. Per seguire la procedura per la [creazione di un programma](#create-a-program) assicurarsi di selezionare il carico di lavoro **Sviluppo multipiattaforma .NET Core** durante l'installazione.

![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../ide/media/dotnet-core-cross-platform-workload.png)

Al primo avvio di Visual Studio, è possibile scegliere facoltativamente di [accedere](signing-in-to-visual-studio.md) con l'account Microsoft o con l'account aziendale o dell'istituto di istruzione.

## <a name="tour-of-the-ide"></a>Presentazione dell'IDE

Per offrire una panoramica visiva di Visual Studio ad alto livello, l'immagine seguente mostra Visual Studio con un progetto aperto e diverse finestre dei principali strumenti di uso comune:

![IDE di Visual Studio](../ide/media/visualstudioide.png)

- [**Esplora soluzioni**](../ide/solutions-and-projects-in-visual-studio.md) (in alto a destra) consente di visualizzare, esplorare e gestire i file del codice. **Esplora soluzioni** consente di organizzare il codice raggruppando i file in [soluzioni e progetti](quickstart-projects-solutions.md).

- La [finestra dell'editor](../ide/writing-code-in-the-code-and-text-editor.md) (al centro), uno degli strumenti più utilizzati, visualizza il contenuto dei file. Nella finestra è possibile modificare il codice o progettare un'interfaccia utente, ad esempio una finestra con pulsanti e caselle di testo.

- La finestra [Output](../ide/reference/output-window.md) (in basso al centro) è la finestra in cui Visual Studio invia le notifiche, ad esempio messaggi di errore e di debug, avvisi del compilatore, messaggi di stato di pubblicazione e altro. Ogni messaggio viene visualizzato in una scheda separata.

- [Team Explorer](/vsts/user-guide/work-team-explorer) (in basso a destra) consente di tenere traccia degli elementi di lavoro e di condividere il codice con altri utenti usando tecnologie di controllo della versione come [Git](https://git-scm.com/) e [Team Foundation Version Control (TFVC)](/vsts/tfvc/overview).

### <a name="popular-productivity-features"></a>Funzionalità di produttività più note

Le funzionalità più note di Visual Studio che offrono una maggiore produttività nello sviluppo del software includono:

- [Refactoring](../ide/refactoring-in-visual-studio.md)

   Il refactoring prevede operazioni come la ridenominazione intelligente delle variabili, l'estrazione di una o più righe di codice in un nuovo metodo, la modifica dell'ordine dei parametri dei metodi e altro ancora.

   ![Effettuare il refactoring in Visual Studio](../ide/media/refactoring-menu.png)

- [IntelliSense](../ide/using-intellisense.md)

   IntelliSense è un termine che indica diverse funzionalità che visualizzano le informazioni sul codice direttamente nell'editor e, in alcuni casi, scrivono automaticamente piccole parti di codice. È come se si avesse a disposizione la documentazione di base all'interno dell'editor senza dover cercare le informazioni sul tipo altrove. Le funzionalità di IntelliSense variano a seconda del linguaggio. Per altre informazioni, vedere [IntelliSense per C#](../ide/visual-csharp-intellisense.md), [IntelliSense per Visual C++](../ide/visual-cpp-intellisense.md), [IntelliSense per JavaScript](../ide/javascript-intellisense.md) e [IntelliSense per Visual Basic](../ide/visual-basic-specific-intellisense.md). La figura seguente mostra come IntelliSense visualizza un elenco di membri per un tipo:

   ![Elenco dei membri di Visual Studio](../ide/media/intellisense-list-members.png)

- [Avvio veloce](../ide/reference/quick-launch-environment-options-dialog-box.md)

   La quantità di menu, opzioni e proprietà disponibili in Visual Studio può sembrare a volte eccessiva. La casella di ricerca **Avvio veloce** è un ottimo modo per trovare rapidamente quello che serve in Visual Studio. Quando si inizia a digitare il nome di un elemento da cercare, Visual Studio visualizza risultati che consentono di passare esattamente all'elemento desiderato. Se si vuole aggiungere una funzionalità a Visual Studio, ad esempio il supporto di un altro linguaggio di programmazione, **Avvio veloce** fornisce risultati che aprono il programma di installazione di Visual Studio per installare un carico di lavoro o un singolo componente.

   ![Casella di ricerca di Avvio veloce in Visual Studio](../ide/media/quick-launch-nuget.png)

- Controllo ortografia durante la digitazione e [azioni rapide](../ide/quick-actions.md)

   Il controllo ortografia durante la digitazione visualizza sottolineature ondulate che segnalano errori o problemi potenziali nel codice in tempo reale. Questi indizi visivi consentono di risolvere i problemi immediatamente senza attendere che l'errore venga rilevato durante la compilazione o quando si esegue il programma. Se si passa il mouse su una linea ondulata, vengono visualizzate informazioni aggiuntive sull'errore. Sul margine sinistro può essere visualizzata anche una lampadina con le azioni, denominate azioni rapide, per risolvere l'errore.

   ![Controllo ortografia durante la digitazione in Visual Studio](../ide/media/squiggles-error.png)

- [Gerarchia di chiamata](../ide/reference/call-hierarchy.md)

   La finestra **Gerarchia di chiamata** mostra i metodi che chiamano un metodo selezionato. Si tratta di informazioni che possono risultare utili quando si prevede di cambiare o rimuovere il metodo o quando si tenta di rilevare un bug.

   ![Finestra Gerarchia di chiamata](../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens consente di trovare i riferimenti e le modifiche al codice, i bug collegati, gli elementi di lavoro, le revisioni del codice e gli unit test senza uscire dall'editor.

   ![CodeLens](../ide/media/codelensoverview.png)

- [Vai a definizione](../ide/go-to-and-peek-definition.md)

  La funzionalità Vai a definizione consente di passare direttamente alla posizione in cui viene definita una funzione o un tipo.

   ![Vai a definizione](../ide/media/go-to-definition-menu.png)

- [Visualizza definizione](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   La finestra **Visualizza definizione** mostra la definizione di un metodo o un tipo senza aprire un file separato.

   ![Visualizza definizione](../ide/media/peek-definition.png)

## <a name="create-a-program"></a>Creare un programma

In questa sezione viene descritta in dettaglio la procedura per creare un nuovo semplice programma.

1. Aprire Visual Studio. Scegliere **File** > **Nuovo** > **Progetto** dal menu.

   ![File > Nuovo progetto sulla barra dei menu](../ide/media/file-new-project-menu.png)

1. Viene visualizzata la finestra di dialogo **Nuovo progetto** con vari *modelli* di progetto. Un modello contiene i file di base e le impostazioni necessarie per un determinato tipo di progetto. Scegliere la categoria **.NET Core** in **Visual C#** e quindi scegliere il modello **App console (.NET Core)**. Nella casella di testo **Nome** digitare **HelloWorld** e quindi selezionare il pulsante **OK**.

   ![Modello di app .NET Core](../ide/media/overview-new-project-dialog.png)

   Visual Studio crea il progetto. È una semplice applicazione "Hello World" che chiama il metodo <xref:System.Console.WriteLine?displayProperty=nameWithType> per visualizzare il valore letterale stringa "Hello World!" nella finestra della console (output del programma).

  > [!NOTE]
  > Se non viene visualizzata la categoria **.NET Core** è necessario installare il carico di lavoro **Sviluppo multipiattaforma .NET Core**. A tale scopo, scegliere il collegamento **Apri il programma di installazione di Visual Studio** in basso a sinistra nella finestra di dialogo **Nuovo progetto**. Dopo l'apertura del programma di installazione di Visual Studio, scorrere e selezionare il carico di lavoro **Sviluppo multipiattaforma .NET Core** e quindi scegliere **Modifica**.

   Il risultato visualizzato a breve dovrebbe essere simile al seguente:

   ![IDE di Visual Studio](../ide/media/overview-ide-console-app.png)

   Il codice C# per l'applicazione viene visualizzato nella finestra dell'editor che occupa la maggior parte dello spazio. Si noti che il testo viene colorato automaticamente per indicare le diverse parti del codice, ad esempio parole chiave e tipi. Le piccole linee tratteggiate verticali nel codice indicano inoltre le parentesi graffe corrispondenti e i numeri di riga facilitano l'individuazione del codice in un secondo momento. È possibile scegliere i piccoli segni meno racchiusi in un riquadro per comprimere o espandere blocchi di codice. Questa funzionalità per la strutturazione del codice consente di nascondere il codice non necessario, migliorando la leggibilità del contenuto visualizzato sullo schermo. I file del progetto sono elencati sul lato destro in una finestra denominata **Esplora soluzioni**.

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

1. Digitare il nuovo nome per la variabile, **username**.

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

Durante la scrittura del codice è necessario eseguirlo e testarlo per individuare eventuali bug. Il sistema di debug di Visual Studio consente di esaminare il codice un'istruzione alla volta e controllare le variabili man mano. È possibile impostare *punti di interruzione* che arrestano l'esecuzione del codice in una determinata riga. È possibile osservare come viene modificato il valore di una variabile durante l'esecuzione del codice e altro ancora.

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

È possibile personalizzare l'interfaccia utente di Visual Studio, ad esempio modificare il tema colori predefinito. Per modificare il tema **Scuro**:

1. Dalla barra dei menu scegliere **Strumenti** > **Opzioni** per aprire la finestra di dialogo **Opzioni**.

1. Nella pagina delle opzioni **Ambiente** > **Generale** modificare la selezione del **Tema colori** in **Scuro** e quindi scegliere **OK**.

   Viene applicato il tema colori **Scuro** all'intero ambiente IDE.

   ![Visual Studio con tema Scuro](media/quickstart-personalize-dark-theme.png)

Per informazioni su altri modi per personalizzare l'IDE, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="learn-more"></a>Altre informazioni

È possibile creare un'app per un telefono Android o iOS o creare un gioco 3D o un'app cloud. Per informazioni su queste e altre funzionalità di Visual Studio, vedere [Funzionalità di Visual Studio 2017](../ide/advanced-feature-overview.md).

Per iniziare a scrivere codice, scegliere uno degli argomenti della Guida introduttiva dal sommario, ad esempio [Usare Visual Studio per creare la prima app Web ASP.NET Core](quickstart-aspnet-core.md).

Guardare anche i corsi gratuiti su Visual Studio disponibili in [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033).

## <a name="see-also"></a>Vedere anche

* [Altre funzionalità di Visual Studio](../ide/advanced-feature-overview.md)
* [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
* [Blog di Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
* [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
