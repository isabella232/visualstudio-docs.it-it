---
title: Panoramica per gli sviluppatori Visual Basic
ms.date: 11/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 506581dc329249fc4043e01222163499f2de46d7
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2018
ms.locfileid: "54405321"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Benvenuti all'IDE di Visual Studio | Visual Basic

L'*ambiente di sviluppo integrato (IDE)* di Visual Studio è un'area di avvio creativa che consente di modificare, eseguire il debug, compilare il codice e quindi pubblicare un'app. Un ambiente di sviluppo integrato (IDE) è un programma con numerose funzionalità che può essere usato per molti aspetti dello sviluppo software. A differenza dell'editor e del debugger standard disponibili nella maggior parte degli ambienti IDE, Visual Studio include compilatori, strumenti di completamento codice, finestre di progettazione con interfaccia grafica e altre funzionalità che semplificano il processo di sviluppo del software.

![IDE di Visual Studio](../media/visual-studio-ide.png)

Questa immagine presenta Visual Studio con un progetto aperto e varie finestre degli strumenti di base che probabilmente verranno usate:

- [**Esplora soluzioni**](../../ide/solutions-and-projects-in-visual-studio.md) (in alto a destra) consente di visualizzare, esplorare e gestire i file del codice. **Esplora soluzioni** consente di organizzare il codice raggruppando i file in [soluzioni e progetti](tutorial-projects-solutions.md).

- La [finestra dell'editor](../../ide/writing-code-in-the-code-and-text-editor.md) (al centro), uno degli strumenti più utilizzati, visualizza il contenuto dei file. Nella finestra è possibile modificare il codice o progettare un'interfaccia utente, ad esempio una finestra con pulsanti e caselle di testo.

- La finestra [Output](../../ide/reference/output-window.md) (in basso al centro) è la finestra in cui Visual Studio invia le notifiche, ad esempio messaggi di errore e di debug, avvisi del compilatore, messaggi di stato di pubblicazione e altro. Ogni messaggio viene visualizzato in una scheda separata.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (in basso a destra) consente di tenere traccia degli elementi di lavoro e di condividere il codice con altri utenti usando tecnologie di controllo della versione come [Git](https://git-scm.com/) e [Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Edizioni

Visual Studio è disponibile per Windows e Mac. [Visual Studio per Mac](/visualstudio/mac/) include numerose funzionalità di Visual Studio 2017 ed è ottimizzato per lo sviluppo di app multipiattaforma e per dispositivi mobili. Questo articolo è incentrato sulla versione Windows di Visual Studio 2017.

Sono disponibili tre edizioni di Visual Studio 2017: Community, Professional ed Enterprise. Vedere [Confronta gli IDE di Visual Studio2017](https://visualstudio.microsoft.com/vs/compare/) per informazioni sulle funzionalità supportate in ogni edizione.

## <a name="popular-productivity-features"></a>Funzionalità di produttività più note

Le funzionalità più note di Visual Studio che offrono una maggiore produttività nello sviluppo del software includono:

- [Refactoring](../../ide/refactoring-in-visual-studio.md)

   Il refactoring prevede operazioni come la ridenominazione intelligente delle variabili, l'estrazione di una o più righe di codice in un nuovo metodo, la modifica dell'ordine dei parametri dei metodi e altro ancora.

   ![Effettuare il refactoring in Visual Studio](media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense è un termine che indica diverse funzionalità che visualizzano le informazioni sul codice direttamente nell'editor e, in alcuni casi, scrivono automaticamente piccole parti di codice. È come se si avesse a disposizione la documentazione di base all'interno dell'editor senza dover cercare le informazioni sul tipo altrove. Le funzionalità di IntelliSense variano a seconda del linguaggio. Per altre informazioni, vedere [IntelliSense per C#](../../ide/visual-csharp-intellisense.md), [IntelliSense per Visual C++](../../ide/visual-cpp-intellisense.md), [IntelliSense per JavaScript](../../ide/javascript-intellisense.md) e [IntelliSense per Visual Basic](../../ide/visual-basic-specific-intellisense.md). La figura seguente mostra come IntelliSense visualizza un elenco di membri per un tipo:

   ![Elenco dei membri di Visual Studio](media/intellisense-list-members.png)

- [Avvio veloce](../../ide/reference/quick-launch-environment-options-dialog-box.md)

   La quantità di menu, opzioni e proprietà disponibili in Visual Studio può sembrare a volte eccessiva. La casella di ricerca **Avvio veloce** è un ottimo modo per trovare rapidamente quello che serve in Visual Studio. Quando si inizia a digitare il nome di un elemento da cercare, Visual Studio visualizza risultati che consentono di passare esattamente all'elemento desiderato. Se si vuole aggiungere una funzionalità a Visual Studio, ad esempio il supporto di un altro linguaggio di programmazione, **Avvio veloce** fornisce risultati che aprono il programma di installazione di Visual Studio per installare un carico di lavoro o un singolo componente.

   ![Casella di ricerca di Avvio veloce in Visual Studio](../media/quick-launch-nuget.png)

- Controllo ortografia durante la digitazione e [azioni rapide](../../ide/quick-actions.md)

   Il controllo ortografia durante la digitazione visualizza sottolineature ondulate che segnalano errori o problemi potenziali nel codice in tempo reale. Questi indizi visivi consentono di risolvere i problemi immediatamente senza attendere che l'errore venga rilevato durante la compilazione o quando si esegue il programma. Se si passa il mouse su una linea ondulata, vengono visualizzate informazioni aggiuntive sull'errore. Sul margine sinistro può essere visualizzata anche una lampadina con le azioni, denominate azioni rapide, per risolvere l'errore.

   ![Controllo ortografia durante la digitazione in Visual Studio](media/squiggles-error.png)

- [Gerarchia di chiamata](../../ide/reference/call-hierarchy.md)

   La finestra **Gerarchia di chiamata** mostra i metodi che chiamano un metodo selezionato. Si tratta di informazioni che possono risultare utili quando si prevede di cambiare o rimuovere il metodo o quando si tenta di rilevare un bug.

   ![Finestra Gerarchia di chiamata in Visual Studio](media/call-hierarchy.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens consente di trovare i riferimenti e le modifiche al codice, i bug collegati, gli elementi di lavoro, le revisioni del codice e gli unit test senza uscire dall'editor.

   ![CodeLens in Visual Studio](media/codelens.png)

   > [!NOTE]
   > CodeLens non è disponibile nell'edizione Community di Visual Studio 2017.

- [Vai a definizione](../../ide/go-to-and-peek-definition.md)

   La funzionalità Vai a definizione consente di passare direttamente alla posizione in cui viene definita una funzione o un tipo.

   ![Vai a definizione in Visual Studio](media/go-to-definition-menu.png)

- [Visualizza definizione](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   La finestra **Visualizza definizione** mostra la definizione di un metodo o un tipo senza aprire un file separato.

   ![Visualizza definizione in Visual Studio](media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Installare l'IDE di Visual Studio

Questa panoramica illustra la creazione di un progetto semplice e alcune operazioni eseguibili con Visual Studio, ad esempio la modifica del tema colori, l'uso di [Intellisense](../../ide/using-intellisense.md) per il supporto della creazione del codice e infine il debug di un'app per visualizzare il valore di una variabile durante l'esecuzione del programma. Per iniziare, [scaricare Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) e installarlo nel sistema.

Il programma di installazione modulare consente di scegliere e installare specifici *carichi di lavoro*, ovvero gruppi di funzionalità necessarie per il linguaggio di programmazione o la piattaforma preferiti. Per seguire la procedura per la [creazione di un programma](#create-a-program) assicurarsi di selezionare il carico di lavoro **Sviluppo multipiattaforma .NET Core** durante l'installazione.

![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Al primo avvio di Visual Studio, è possibile scegliere facoltativamente di [accedere](../../ide/signing-in-to-visual-studio.md) con l'account Microsoft o con l'account aziendale o dell'istituto di istruzione.

## <a name="customize-visual-studio"></a>Personalizzare Visual Studio

È possibile personalizzare l'interfaccia utente di Visual Studio, ad esempio modificare il tema colori predefinito.

### <a name="change-the-color-theme"></a>Modificare il tema colori

Per modificare il tema **Scuro**:

1. Dalla barra dei menu scegliere **Strumenti** > **Opzioni** per aprire la finestra di dialogo **Opzioni**.

2. Nella pagina delle opzioni **Ambiente** > **Generale** modificare la selezione del **Tema colori** in **Scuro** e quindi scegliere **OK**.

   ![Impostare il tema colori scuro in Visual Studio](media/change-color-theme.png)

   Viene applicato il tema colori **Scuro** all'intero ambiente IDE.

   ![Visual Studio con tema scuro](../../ide/media/quickstart-personalize-dark-theme.png)

### <a name="select-environment-settings"></a>Selezionare le impostazioni dell'ambiente

Visual Studio verrà quindi configurato per usare impostazioni di ambiente su misura per gli sviluppatori Visual Basic.

1. Nella barra dei menu scegliere **Strumenti** > **Importa/Esporta impostazioni**.

2. Nell'**Importazione/Esportazione guidata delle impostazioni** selezionare **Reimposta tutte le impostazioni** nella prima pagina e quindi scegliere **Avanti**.

3. Nella pagina **Salvare le impostazioni correnti** selezionare un'opzione per salvare o meno le impostazioni correnti e quindi scegliere **Avanti**. (Se non è stata personalizzata alcuna impostazione, selezionare **No, ripristina solo le impostazioni sovrascrivendo le impostazioni correnti**.)

4. Nella pagina **Scegliere una raccolta di impostazioni predefinita** scegliere **Visual Basic** e quindi scegliere **Fine**.

5. Nella pagina **Reimpostazione completa** scegliere **Chiudi**.

Per informazioni su altri modi per personalizzare l'IDE, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Creare un programma

In questa sezione viene descritta in dettaglio la procedura per creare un programma semplice.

1. Aprire Visual Studio. Nella barra dei menu scegliere **File** > **Nuovo progetto**.

   ![File > Nuovo progetto sulla barra dei menu](media/file-new-project-menu.png)

2. Viene visualizzata la finestra di dialogo **Nuovo progetto** con vari *modelli* di progetto. Un modello contiene i file di base e le impostazioni necessarie per un determinato tipo di progetto. Scegliere la categoria **.NET Core** in **Visual Basic** e quindi scegliere il modello **App console (.NET Core)**. Nella casella di testo **Nome** digitare **HelloWorld** e quindi selezionare il pulsante **OK**.

   ![Modello di app .NET Core](media/overview-npd.png)

   > [!NOTE]
   > Se non viene visualizzata la categoria **.NET Core** è necessario installare il carico di lavoro **Sviluppo multipiattaforma .NET Core**. A tale scopo, scegliere il collegamento **Apri il programma di installazione di Visual Studio** in basso a sinistra nella finestra di dialogo **Nuovo progetto**. Dopo l'apertura del programma di installazione di Visual Studio, scorrere e selezionare il carico di lavoro **Sviluppo multipiattaforma .NET Core** e quindi scegliere **Modifica**.

   Visual Studio crea il progetto. È una semplice applicazione "Hello World" che chiama il metodo <xref:System.Console.WriteLine?displayProperty=nameWithType> per visualizzare il valore letterale stringa "Hello World!" nella finestra della console (output del programma).

   Il risultato visualizzato a breve dovrebbe essere simile al seguente:

   ![IDE di Visual Studio](media/overview-ide-console-app.png)

   Il codice Visual Basic per l'app viene visualizzato nella finestra dell'editor che occupa la maggior parte dello spazio. Si noti che il testo viene colorato automaticamente per indicare le diverse parti del codice, ad esempio parole chiave e tipi. Le piccole linee tratteggiate verticali nel codice indicano inoltre le parentesi graffe corrispondenti e i numeri di riga facilitano l'individuazione del codice in un secondo momento. È possibile scegliere i piccoli segni meno racchiusi in un riquadro per comprimere o espandere blocchi di codice. Questa funzionalità per la strutturazione del codice consente di nascondere il codice non necessario, migliorando la leggibilità del contenuto visualizzato sullo schermo. I file del progetto sono elencati sul lato destro in una finestra denominata **Esplora soluzioni**.

   ![IDE di Visual Studio con caselle rosse](media/overview-ide-console-app-red-boxes.png)

   Sono disponibili altri menu e finestre degli strumenti, ma per il momento si procederà con la creazione del programma.

3. Premere ora **CTRL**+**F5** per avviare l'app.

   Visual Studio compila l'app e apre una finestra della console con il messaggio **Hello World!**. Ed ecco un'app in esecuzione.

   ![Finestra della console](../media/overview-console-window.png)

4. Per chiudere la finestra della console, premere un tasto qualsiasi.

5. A questo punto verrà aggiunto ulteriore codice per l'app. Aggiungere il codice Visual Basic seguente prima della riga `Console.WriteLine("Hello World!")`:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Il codice visualizza **What is your name?** nella finestra della console e attende che l'utente immetta testo seguito da **INVIO**.

6. Modificare la riga `Console.WriteLine("Hello World!")` con il codice seguente:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

7. Eseguire nuovamente l'app premendo **CTRL**+**F5**.

   Visual Studio ricompila l'app, viene aperta una finestra della console e viene richiesto il nome.

8. Immettere il nome nella finestra della console e premere **INVIO**.

   Il programma visualizza un saluto con il nome specificato.

   ![Input nella finestra della console](media/overview-console-input.png)

9. Premere un tasto qualsiasi per chiudere la finestra della console e arrestare l'esecuzione del programma.

## <a name="use-refactoring-and-intellisense"></a>Usare refactoring ed esplorazione

Di seguito sono descritti due modi in cui è possibile usare il [refactoring](../../ide/refactoring-in-visual-studio.md) e [IntelliSense](../../ide/using-intellisense.md) per creare codice in modo più efficace.

In primo luogo, rinominare la variabile `name`:

1. Fare doppio clic sulla variabile `name` per selezionarla.

2. Digitare il nuovo nome per la variabile, **username**.

   Si noti che viene visualizzata una casella grigia intorno a variabile e una lampadina viene visualizzata nel margine.

3. Selezionare l'icona lampadina per visualizzare le [azioni rapide](../../ide/quick-actions.md) disponibili. Selezionare **Rinomina 'nome' in 'nomeutente'**.

   ![Rinominare l'azione in Visual Studio](media/rename-quick-action.png)

   La variabile viene rinominata all'interno del progetto, ovvero in questo caso in due posizioni.

4. Si esamini ora IntelliSense. Sotto la riga `Console.WriteLine("Hello " + username + "!")` digitare il frammento di codice seguente:

    ```vb
   Dim now = Date.
   ```

   Una casella visualizza i membri della classe <xref:System.DateTime>. In una casella separata viene visualizzata anche la descrizione del membro correntemente selezionato.

   ![Membri dell'elenco di IntelliSense in Visual Studio](media/intellisense-list-members.png)

5. Selezionare il membro denominato **Now** che è una proprietà della classe facendo doppio clic su di esso oppure usando i tasti di direzione freccia SU e GIÙ e premendo **TAB**.

6. Sotto questa riga digitare o incollare le righe di codice seguenti:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> è leggermente diverso da <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> in quanto non aggiunge un terminatore di riga dopo la stampa. Ciò significa che la parte successiva del testo che viene inviata all'output verrà stampata sulla stessa riga. È possibile passare il mouse su ognuno di questi metodi nel codice per visualizzarne la descrizione.

7. Successivamente, verrà nuovamente usato il refactoring per rendere più breve il codice. Fare clic sulla variabile `now` nella riga `Dim now = Date.Now`.

   Viene visualizzata una piccola icona cacciavite nel margine della riga.

8. Fare clic sull'icona cacciavite per visualizzare i suggerimenti disponibili in Visual Studio. In questo caso viene visualizzato il refactoring [Variabile temporanea inline](../../ide/reference/inline-temporary-variable.md) per rimuovere una riga di codice senza modificare il comportamento complessivo del codice:

   ![Refactoring Variabile temporanea Inline in Visual Studio](media/inline-temporary-variable-refactoring.png)

9. Fare clic su **Variabile temporanea inline** per effettuare il refactoring del codice.

10. Eseguire nuovamente il programma premendo **CTRL**+**F5**. L'output è simile al seguente:

    ![Finestra della console con output del programma](media/overview-console-final.png)

## <a name="debug-code"></a>Debug del codice

Durante la scrittura del codice è necessario eseguirlo e testarlo per individuare eventuali bug. Il sistema di debug di Visual Studio consente di esaminare il codice un'istruzione alla volta e controllare le variabili man mano. È possibile impostare *punti di interruzione* che arrestano l'esecuzione del codice in una determinata riga. È possibile osservare come viene modificato il valore di una variabile durante l'esecuzione del codice e altro ancora.

Impostare un punto di interruzione per visualizzare il valore della variabile `username` mentre il programma è "in corso".

1. Individuare la riga di codice `Console.WriteLine("Hello " + username + "!")`. Per impostare un punto di interruzione nella riga di codice, ovvero per sospendere l'esecuzione del programma in corrispondenza della riga, fare clic sul margine di sinistra dell'editor. È anche possibile fare clic su un punto qualsiasi della riga di codice e quindi premere **F9**.

   Viene visualizzato un cerchio rosso nel margine di sinistra e il codice viene evidenziato in rosso.

   ![Punto di interruzione nella riga di codice in Visual Studio](media/breakpoint.png)

1. Avviare il debug selezionando **Debug** > **Avvia debug** o premendo **F5**.

1. Quando viene visualizzata la finestra della console e viene chiesto di immettere il nome, digitarlo e premere **INVIO**.

   Lo stato attivo torna all'editor del codice di Visual Studio e la riga di codice con il punto di interruzione viene evidenziata in giallo. Ciò significa che la riga è la successiva riga di codice eseguita dal programma.

1. Passare il mouse sulla variabile `username` per impostarne il valore. In alternativa, è possibile fare clic con il pulsante destro del mouse su `username` e selezionare **Aggiungi espressione di controllo** per aggiungere la variabile nella finestra **Espressione di controllo** in cui è possibile visualizzarne anche il valore.

   ![Valore della variabile durante il debug in Visual Studio](media/debugging-variable-value.png)

1. Per consentire il completamento dell'esecuzione del programma, premere di nuovo **F5**.

Per altri dettagli sul debug in Visual Studio, vedere [Tour delle funzionalità del debugger](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Passaggi successivi

Esplorare più approfonditamente Visual Studio seguendo uno di questi articoli introduttivi:

> [!div class="nextstepaction"]
> [Informazioni su come usare l'editor del codice](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Guida introduttiva: progetti e soluzioni](tutorial-projects-solutions.md)

## <a name="see-also"></a>Vedere anche

- Scoprire [altre funzionalità di Visual Studio](../../ide/advanced-feature-overview.md)
- Visitare [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Leggere il [Blog di Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
- Guardare i corsi gratuiti su Visual Studio disponibili in [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033)