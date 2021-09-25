---
title: Panoramica per gli sviluppatori Visual Basic
description: Informazioni sull'uso Visual Studio per modificare, eseguire il debug e compilare il codice e quindi pubblicare un'app Visual Basic sviluppatore.
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
- get-started
- SEO-VS-2020
ms.topic: conceptual
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f2868a4a86f1ce70fbaf9f94bf1c5f3971b45c59
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429866"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Benvenuti all'IDE di Visual Studio | Visual Basic

Un *ambiente di sviluppo integrato* (IDE) è un programma ricco di funzionalità che supporta molti aspetti dello sviluppo software. L Visual Studio IDE è un'area di avvio creative che è possibile usare per modificare, eseguire il debug e compilare il codice e quindi pubblicare un'app. Oltre all'editor e al debugger standard forniti dalla maggior parte degli ID, Visual Studio include compilatori, strumenti di completamento del codice, finestre di progettazione grafiche e molte altre funzionalità per migliorare il processo di sviluppo software.

::: moniker range="vs-2017"

![Screenshot dell'IDE Visual Studio 2017 con Visual Basic codice.](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[![Screenshot dell'IDE Visual Studio 2019 con Visual Basic codice.](media/vs-2019/ide-overview.png)](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/ide-overview.png" alt-text="Screenshot dell'IDE Visual Studio con Visual Basic e funzionalità chiave." lightbox="media/vs-2022/ide-overview.png" border="false":::

::: moniker-end

L'immagine precedente mostra Visual Studio con un progetto Visual Basic aperto che mostra le finestre principali e le relative funzionalità:

- In [Esplora soluzioni](../../ide/solutions-and-projects-in-visual-studio.md), in alto a destra, è possibile visualizzare, esplorare e gestire i file di codice. **Esplora soluzioni** possibile organizzare il codice raggruppando i file in [soluzioni e progetti](tutorial-projects-solutions.md).

- La finestra [centrale dell'editor,](../../ide/writing-code-in-the-code-and-text-editor.md)in cui probabilmente si passerà la maggior parte del tempo, visualizza il contenuto del file. Nella finestra dell'editor è possibile modificare il codice o progettare un'interfaccia utente, ad esempio una finestra con pulsanti e caselle di testo.

::: moniker range="vs-2017"

- La finestra [Output](../../ide/reference/output-window.md) (in basso al centro) è la finestra in cui Visual Studio invia le notifiche, ad esempio messaggi di errore e di debug, avvisi del compilatore, messaggi di stato di pubblicazione e altro. Ogni origine dei messaggi ha una scheda separata.

::: moniker-end

::: moniker range="<=vs-2019"
- In [Team Explorer,](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true)in basso a destra, è possibile tenere traccia degli elementi di lavoro e condividere il codice usando tecnologie di controllo della versione come [Git](https://git-scm.com/) e [controllo della versione di Team Foundation (TFVC).](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true)
::: moniker-end

::: moniker range=">=vs-2022"
- In [Git Changes (Modifiche Git)](/visualstudio/version-control/) in basso a destra è possibile tenere traccia degli elementi di lavoro e condividere il codice con altri utenti usando tecnologie di controllo della versione come [Git](https://git-scm.com/) [e GitHub](https://docs.github.com/github).
::: moniker-end

## <a name="editions"></a>Edizioni

Visual Studio è disponibile per Windows e Mac. [Visual Studio per Mac](/visualstudio/mac/) offre molte delle stesse funzionalità di Visual Studio per Windows ed è ottimizzato per lo sviluppo di app multipiattaforma e per dispositivi mobili. Questo articolo è in particolare sulla Windows di Visual Studio.

Esistono tre edizioni di Visual Studio: Community, Professional e Enterprise. Vedere [Confrontare Visual Studio edizioni](https://visualstudio.microsoft.com/vs/compare/) per informazioni sulle funzionalità supportate da ogni edizione.

## <a name="popular-productivity-features"></a>Funzionalità di produttività più note

Alcune delle funzionalità più comuni di Visual Studio che migliorano la produttività durante lo sviluppo di software includono:

- Controllo ortografia durante la digitazione e [azioni rapide](../../ide/quick-actions.md)

  Il controllo ortografia durante la digitazione visualizza sottolineature ondulate che segnalano errori o problemi potenziali nel codice in tempo reale. Questi indizi visivi consentono di risolvere i problemi immediatamente, senza attendere di individuare gli errori durante la compilazione o il runtime. Se si passa il puntatore del mouse su una stringa onnipresente, vengono visualizzate altre informazioni sull'errore. Nel margine sinistro potrebbe essere visualizzata anche una lampadina con *azioni rapide* che è possibile eseguire per correggere l'errore.

   ::: moniker range="vs-2017"

   ![Screenshot di una sottolineatura ondulata in Visual Studio.](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Screenshot di una sottolineatura ondulata in Visual Studio.](media/vs-2019/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/squiggles-error.png" alt-text="Screenshot di una sottolineatura ondulata in Visual Studio." border="false":::

   ::: moniker-end

- [Refactoring](../../ide/refactoring-in-visual-studio.md)

   Il refactoring include operazioni quali la ridenominazione intelligente delle variabili, l'estrazione di una o più righe di codice in un nuovo metodo e la modifica dell'ordine dei parametri del metodo.

   ::: moniker range="vs-2017"

   ![Screenshot del menu Refactoring in Visual Studio.](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Screenshot del menu Refactoring in Visual Studio.](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/refactoring-menu.png" alt-text="Screenshot del menu Refactoring in Visual Studio." border="false":::

   ::: moniker-end

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense è un set di funzionalità che visualizzano informazioni sul codice direttamente nell'editor e, in alcuni casi, scrivono automaticamente piccole quantità di codice. È come avere la documentazione di base inline nell'editor, quindi non è necessario cercare informazioni sul tipo altrove.

   La figura seguente mostra come IntelliSense visualizza un elenco di membri per un tipo:

   ::: moniker range="vs-2017"

   ![Screenshot di un elenco di membri IntelliSense.](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Screenshot di un elenco di membri IntelliSense.](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/intellisense.png" alt-text="Screenshot di un elenco di membri IntelliSense." border="false":::

   ::: moniker-end

   Le funzionalità di IntelliSense variano a seconda del linguaggio. Per altre informazioni, vedere [IntelliSense per C#](../../ide/visual-csharp-intellisense.md), [IntelliSense per Visual C++](../../ide/visual-cpp-intellisense.md), [IntelliSense per JavaScript](../../ide/javascript-intellisense.md) e [IntelliSense per Visual Basic](../../ide/visual-basic-specific-intellisense.md).

- [Ricerca di Visual Studio](../../ide/visual-studio-search.md)

   Visual Studio, i menu, le opzioni e le proprietà possono sembrare a volte difficili da usare. Visual Studio, o **CTRL** Q, è un ottimo modo per trovare rapidamente le funzionalità IDE e + il codice in un'unica posizione.

   Quando si inizia a digitare il nome di un elemento che si sta cercando, Visual Studio i risultati che ti portano dove devi andare. Se è necessario aggiungere funzionalità, ad esempio un altro linguaggio di programmazione, è possibile aprire il Programma di installazione di Visual Studio dai risultati della casella di ricerca per installare il carico di lavoro o il componente.

   ::: moniker range="vs-2017"

   ![Screenshot che mostra la Avvio veloce di ricerca in Visual Studio 2017.](../media/quick-launch-nuget.png)

   Per altre informazioni, vedere [Avvio veloce](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Screenshot che mostra la Avvio veloce di ricerca in Visual Studio 2019.](../media/vs-2019/quick-launch-nuget.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/quick-launch-nuget.png" alt-text="Screenshot che mostra la Avvio veloce di ricerca nella Visual Studio." border="false":::

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Modifica e debug collaborativi con altri utenti in tempo reale, indipendentemente dal tipo di app o dal linguaggio di programmazione. È possibile condividere il progetto in modo immediato e sicuro. È anche possibile condividere sessioni di debug, istanze del terminale, app Web localhost, chiamate vocali e altro ancora.

- [Gerarchia delle chiamate](../../ide/reference/call-hierarchy.md)

   La finestra **Gerarchia di chiamata** mostra i metodi che chiamano un metodo selezionato. Queste informazioni possono essere utili quando si pensa di modificare o rimuovere il metodo o quando si tenta di rilevare un bug.

   ::: moniker range="vs-2017"

   ![Screenshot che mostra la finestra Gerarchia di chiamata in Visual Studio.](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Screenshot che mostra la finestra Gerarchia di chiamata in Visual Studio.](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/call-hierarchy.png" alt-text="Screenshot che mostra la finestra Gerarchia di chiamata in Visual Studio." border="false":::

   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens consente di trovare riferimenti al codice, modifiche al codice, bug collegati, elementi di lavoro, revisioni del codice e unit test, senza uscire dall'editor.

   ::: moniker range="vs-2017"

   ![Screenshot che mostra CodeLens in Visual Studio.](media/codelens.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Screenshot che mostra CodeLens in Visual Studio.](media/vs-2019/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/codelens.png" alt-text="Screenshot che mostra CodeLens in Visual Studio." border="false":::

   ::: moniker-end

- [Vai a definizione](../../ide/go-to-and-peek-definition.md)

   La **funzionalità Vai a definizione** consente di passare direttamente alla posizione di una definizione di funzione o di tipo.

   ::: moniker range="vs-2017"

   ![Screenshot che mostra Vai a definizione in Visual Studio 2017.](media/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Screenshot che mostra Vai a definizione in Visual Studio 2019.](media/vs-2019/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/go-to-definition-menu.png" alt-text="Screenshot che mostra Vai a definizione in Visual Studio." border="false":::

   ::: moniker-end

- [Visualizza definizione](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   La **finestra Visualizza** definizione mostra una definizione di metodo o tipo senza aprire un file separato.

   ::: moniker range="vs-2017"

   ![Screenshot che mostra Visualizza definizione in Visual Studio.](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Screenshot che mostra Visualizza definizione in Visual Studio.](media/vs-2019/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/peek-definition.png" alt-text="Screenshot che mostra Visualizza definizione in Visual Studio." border="false":::

   ::: moniker-end

## <a name="install-visual-studio"></a>Installare Visual Studio

In questa sezione viene creato un progetto semplice per provare alcune delle operazioni che è possibile eseguire con Visual Studio. Si apprenderà come modificare il tema colori, usare [IntelliSense](../../ide/using-intellisense.md) come supporto per la scrittura del codice ed eseguire il debug di un'app per visualizzare un valore variabile durante l'esecuzione dell'app.

::: moniker range="vs-2017"

Per iniziare, [scaricare Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) e installarlo nel sistema. Il programma di installazione modulare consente di scegliere e installare specifici *carichi di lavoro*, ovvero gruppi di funzionalità necessarie per il linguaggio di programmazione o la piattaforma preferiti. Per seguire la procedura per la [creazione di un programma](#create-a-program) assicurarsi di selezionare il carico di lavoro **Sviluppo multipiattaforma .NET Core** durante l'installazione.

![Screenshot del carico di lavoro sviluppo multipiattaforma dot NET Core nella Programma di installazione di Visual Studio.](../media/dotnet-core-cross-platform-workload.png)

::: moniker-end

::: moniker range="vs-2019"

Per iniziare, [scaricare Visual Studio](https://visualstudio.microsoft.com/downloads) e installarlo nel sistema. Il programma di installazione modulare consente di selezionare e installare carichi di *lavoro,* ovvero gruppi di funzionalità necessarie per il linguaggio di programmazione o la piattaforma preferita. Per seguire la procedura per la [creazione di un programma](#create-a-program) assicurarsi di selezionare il carico di lavoro **Sviluppo multipiattaforma .NET Core** durante l'installazione.

![Screenshot del carico di lavoro sviluppo multipiattaforma dot NET Core nella Programma di installazione di Visual Studio.](../media/dotnet-core-cross-platform-workload.png)

::: moniker-end

::: moniker range=">=vs-2022"

Per iniziare, [scaricare Visual Studio](https://visualstudio.microsoft.com/downloads) e installarlo nel sistema. Nel programma di installazione modulare è possibile scegliere e installare carichi di *lavoro,* ovvero gruppi di funzionalità necessari per i linguaggi di programmazione o le piattaforme desiderate. Per usare la procedura seguente per creare [un programma](#create-a-program), assicurarsi di selezionare il carico di lavoro Sviluppo per **desktop .NET** durante l'installazione.

:::image type="content" source="media/vs-2022/dot-net-development-workload.png" alt-text="Screenshot del carico di lavoro Dot NET Desktop Development selezionato nel Programma di installazione di Visual Studio." border="false":::

::: moniker-end

Quando si apre Visual Studio per la prima [](../../ide/signing-in-to-visual-studio.md) volta, è possibile accedere usando il proprio account Microsoft o l'account aziendale o dell'istituto di istruzione.

## <a name="customize-visual-studio"></a>Personalizzare Visual Studio

È possibile personalizzare l'Visual Studio utente, inclusa la modifica del tema colori predefinito.

### <a name="change-the-color-theme"></a>Modificare il tema colori

Per modificare il tema dei colori:

::: moniker range="vs-2017"

1. Aprire Visual Studio.

1. Nella barra dei menu scegliere **Opzioni** strumenti > **per** aprire la finestra **di dialogo** Opzioni.

1. Nella pagina **delle** > **opzioni Generale** ambiente modificare la selezione **tema** colore in **Scuro** e quindi fare clic su **OK.**

   ![Screenshot che mostra la modifica del tema del colore al colore scuro Visual Studio.](media/change-color-theme.png)

   Viene applicato il tema colori **Scuro** all'intero ambiente IDE.

   ![Screenshot che mostra le Visual Studio nel tema Scuro.](../../ide/media/quickstart-personalize-dark-theme.png)

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio. Nella finestra iniziale selezionare **Continua senza codice.**

   :::image type="content" source="media/vs-2019/continue-without-code.png" alt-text="Screenshot della finestra Start in Visual Studio 2019, con il collegamento &quot;Continua senza codice&quot; evidenziato.":::

   Si aprirà l'IDE.

1. Nella barra Visual Studio menu strumenti **scegliere** Opzioni strumenti >  per aprire la finestra **di dialogo** Opzioni.

1. Nella pagina **delle** > **opzioni Generale** ambiente modificare la selezione **tema** colore in **Scuro** e quindi scegliere **OK.**

   ![Screenshot che mostra la modifica del tema del colore al colore scuro Visual Studio.](media/change-color-theme.png)

   Viene applicato il tema colori **Scuro** all'intero ambiente IDE.

   ![Screenshot che mostra le Visual Studio nel tema Scuro.](../media/vs-2019/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2022"
1. Aprire Visual Studio. Nella finestra iniziale selezionare **Continua senza codice.**

   :::image type="content" source="media/vs-2022/continue-without-code.png" alt-text="Screenshot del Visual Studio schermata Start, con il collegamento Continua senza codice evidenziato." border="false":::

1. Nella barra Visual Studio menu strumenti **scegliere** Opzioni strumenti >  per aprire la finestra **di dialogo** Opzioni.

1. Nella pagina **delle** > **opzioni Generale** ambiente modificare la selezione **tema** colore in **Blu** o **Chiaro** e quindi selezionare **OK.**

   :::image type="content" source="media/vs-2022//change-color-theme.png" alt-text="Screenshot che mostra la modifica del tema del colore in Blu in Visual Studio.":::

   Il tema dei colori per l'intero IDE cambia di conseguenza. Lo screenshot seguente mostra il tema Blu:

   :::image type="content" source="media/vs-2022/blue-theme.png" alt-text="Screenshot che mostra le Visual Studio nel tema Blu.":::
::: moniker-end

### <a name="select-environment-settings"></a>Selezionare le impostazioni dell'ambiente

È possibile configurare Visual Studio per l'uso di impostazioni di ambiente personalizzate per Visual Basic sviluppatori.

1. Sulla barra dei menu scegliere **Strumenti**  >  **Importa ed esporta** Impostazioni .

1. Nell'**Importazione/Esportazione guidata delle impostazioni** selezionare **Reimposta tutte le impostazioni** e quindi selezionare **Avanti**.

1. Nella pagina **Salva Impostazioni** selezionare se salvare le impostazioni correnti prima della reimpostazione. Se non sono state personalizzate impostazioni, selezionare No, è sufficiente **reimpostare le impostazioni, sovrascrivendo le impostazioni correnti.** Selezionare quindi **Avanti**.

1. Nella pagina **Scegliere una raccolta predefinita di** Impostazioni scegliere **Visual Basic** e quindi selezionare **Fine.**

1. Nella pagina **Reimpostazione completa** selezionare **Chiudi**.

Per informazioni su altri modi per personalizzare l'IDE, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Creare un programma

Approfondire e creare un programma semplice.

::: moniker range="vs-2017"

1. Nella barra Visual Studio menu scegliere **File** > **nuovo Project**.

   ![Screenshot che mostra file > nuovo Project sulla barra dei menu.](media/file-new-project-menu.png)

   La **finestra di dialogo Project** mostra diversi modelli di *progetto.* Un modello contiene i file di base e le impostazioni necessarie per un determinato tipo di progetto.

1. Scegliere la categoria **.NET Core** in **Visual Basic** e quindi scegliere il modello **App console (.NET Core)**. Nella casella di testo **Nome** digitare **HelloWorld** e quindi selezionare il pulsante **OK**.

   ![Screenshot che mostra il modello di app .NET Core.](media/overview-npd.png)

   > [!NOTE]
   > Se non viene visualizzata la categoria **.NET Core** è necessario installare il carico di lavoro **Sviluppo multipiattaforma .NET Core**. A tale scopo, scegliere il collegamento **Apri il programma di installazione di Visual Studio** in basso a sinistra nella finestra di dialogo **Nuovo progetto**. Dopo l'apertura del programma di installazione di Visual Studio, scorrere e selezionare il carico di lavoro **Sviluppo multipiattaforma .NET Core** e quindi scegliere **Modifica**.

   Visual Studio crea il progetto. È una semplice applicazione "Hello World" che chiama il metodo <xref:System.Console.WriteLine?displayProperty=nameWithType> per visualizzare il valore letterale stringa "Hello World!" nella finestra della console (output del programma).

   Il risultato visualizzato a breve dovrebbe essere simile al seguente:

   ![Screenshot che mostra l'VISUAL STUDIO IDE.](media/overview-ide-console-app.png)

   Il codice Visual Basic per l'app viene visualizzato nella finestra dell'editor che occupa la maggior parte dello spazio. Si noti che il testo viene colorato automaticamente per indicare le diverse parti del codice, ad esempio parole chiave e tipi. Le piccole linee tratteggiate verticali nel codice indicano inoltre le parentesi graffe corrispondenti e i numeri di riga facilitano l'individuazione del codice in un secondo momento. È possibile scegliere i piccoli segni meno racchiusi in un riquadro per comprimere o espandere blocchi di codice. Questa funzionalità per la strutturazione del codice consente di nascondere il codice non necessario, migliorando la leggibilità del contenuto visualizzato sullo schermo. I file del progetto sono elencati sul lato destro in una finestra denominata **Esplora soluzioni**.

   ![Screenshot che mostra l'IDE Visual Studio con caselle rosse.](media/overview-ide-console-app-red-boxes.png)

   Sono disponibili altri menu e finestre degli strumenti, ma per il momento si procederà con la creazione del programma.

1. Avviare l'app. È possibile farlo scegliendo **Avvia senza eseguire debug** dal menu **Debug** sulla barra dei menu. È anche possibile premere **CTRL** + **F5.**

   ![Screenshot che mostra l'avvio > debug senza debug.](../media/overview-start-without-debugging.png)

   Visual Studio compila l'app e apre una finestra della console con il messaggio **Hello World!**. Ed ecco un'app in esecuzione.

   ![Screenshot che mostra la finestra della console.](../media/overview-console-window.png)

1. Per chiudere la finestra della console, premere un tasto qualsiasi.

1. A questo punto verrà aggiunto ulteriore codice per l'app. Aggiungere il codice Visual Basic seguente prima della riga `Console.WriteLine("Hello World!")`:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Il codice visualizza **What is your name?** nella finestra della console e attende che l'utente immetta testo seguito da **INVIO**.

1. Modificare la riga `Console.WriteLine("Hello World!")` con il codice seguente:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Eseguire di nuovo l'app premendo **CTRL** + **F5.**

   Visual Studio ricompila l'app, viene aperta una finestra della console e viene richiesto il nome.

1. Immettere il nome nella finestra della console e premere **INVIO**.

   ![Screenshot che mostra l'input della finestra della console.](../media/overview-console-input.png)

1. Premere un tasto qualsiasi per chiudere la finestra della console e arrestare l'esecuzione del programma.

::: moniker-end

::: moniker range="vs-2019"

1. Nella barra Visual Studio menu scegliere **File**  >  **nuovo**  >  **Project**. In alternativa, premere **CTRL** + **MAIUSC** + **N**.)

    :::image type="content" source="media/vs-2019/file-new-project.png" alt-text="Screenshot della finestra di dialogo > nuovo > Project dalla barra dei menu Visual Studio 2019.":::

   Viene visualizzata la finestra **Crea un nuovo progetto**, che mostra diversi *modelli* di progetto. Un modello contiene i file e le impostazioni di base necessari per un determinato tipo di progetto.

1. Per trovare il modello da usare, digitare o immettere **console .net core** nella casella di ricerca. L'elenco dei modelli disponibili viene automaticamente filtrato in base alle parole chiave immesse. È possibile filtrare ulteriormente i risultati del  modello scegliendo Visual Basic dall'elenco a discesa  Tutti i linguaggi, **Windows** dall'elenco Tutte le piattaforme e **Console** dall'elenco Tutti i tipi **di** progetto. 

   Selezionare il **modello Applicazione** console e quindi fare clic su **Avanti.**

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Screenshot della finestra &quot;Crea un nuovo progetto&quot; in Visual Studio 2019, in cui si seleziona il modello desiderato.":::

1. Nella finestra **Configura** il nuovo progetto immettere **HelloWorld** nella casella **nome Project , modificare facoltativamente** il percorso della directory per i file di progetto (le impostazioni locali predefinite sono ), quindi fare clic `C:\Users\<name>\source\repos` su **Avanti**.

    :::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Screenshot della finestra &quot;Configura il nuovo progetto&quot; in Visual Studio 2019, in cui si immette il nome del progetto.":::

1. Nella finestra **Informazioni aggiuntive** verificare che **.NET Core 3.1** sia visualizzato nel menu a discesa **Framework** di destinazione e quindi fare clic su **Crea**.

    :::image type="content" source="media/vs-2019/create-project-additional-info.png" alt-text="Screenshot della finestra &quot;Informazioni aggiuntive&quot; in Visual Studio 2019, in cui si seleziona la versione di .NET Core Framework desiderata.":::

   Visual Studio crea il progetto. È una semplice applicazione "Hello World" che chiama il metodo <xref:System.Console.WriteLine?displayProperty=nameWithType> per visualizzare il valore letterale stringa "Hello World!" nella finestra della console (output del programma).

   Il risultato visualizzato a breve dovrebbe essere simile al seguente:

   ![Screenshot che mostra l'VISUAL STUDIO IDE.](media/overview-ide-console-app.png)

   Il codice Visual Basic per l'app viene visualizzato nella finestra dell'editor che occupa la maggior parte dello spazio. Si noti che il testo viene colorato automaticamente per indicare le diverse parti del codice, ad esempio parole chiave e tipi. Le piccole linee tratteggiate verticali nel codice indicano inoltre le parentesi graffe corrispondenti e i numeri di riga facilitano l'individuazione del codice in un secondo momento. È possibile scegliere i piccoli segni meno racchiusi in un riquadro per comprimere o espandere blocchi di codice. Questa funzionalità per la strutturazione del codice consente di nascondere il codice non necessario, migliorando la leggibilità del contenuto visualizzato sullo schermo. I file del progetto sono elencati sul lato destro in una finestra denominata **Esplora soluzioni**.

   ![Screenshot che mostra l'IDE Visual Studio con caselle rosse.](media/overview-ide-console-app-red-boxes.png)

   Sono disponibili altri menu e finestre degli strumenti, ma per il momento si procederà con la creazione del programma.

1. Avviare l'app. È possibile farlo scegliendo **Avvia senza eseguire debug** dal menu **Debug** sulla barra dei menu. È anche possibile premere **CTRL** + **F5.**

   ![Screenshot che mostra l'avvio > debug.](media/vs-2019/start-without-debugging.png)

   Visual Studio compila l'app e apre una finestra della console con il messaggio **Hello World!**. Ed ecco un'app in esecuzione.

   ![Screenshot della finestra della console che mostra il Hello World messaggio.](../media/vs-2019/overview-console-window.png)

1. Per chiudere la finestra della console, premere un tasto qualsiasi.

1. A questo punto verrà aggiunto ulteriore codice per l'app. Aggiungere il codice Visual Basic seguente prima della riga `Console.WriteLine("Hello World!")`:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Il codice visualizza **What is your name?** nella finestra della console e attende che l'utente immetta testo seguito da **INVIO**.

1. Modificare la riga `Console.WriteLine("Hello World!")` con il codice seguente:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Eseguire di nuovo l'app premendo **CTRL** + **F5.**

   Visual Studio ricompila l'app, viene aperta una finestra della console e viene richiesto il nome.

1. Immettere il nome nella finestra della console e premere **INVIO**.

   ![Screenshot della finestra della console che mostra la domanda What is your name (Qual è il tuo nome) e la risposta dell'app.](../media/vs-2019/overview-console-input.png)

1. Premere un tasto qualsiasi per chiudere la finestra della console e arrestare l'esecuzione del programma.

::: moniker-end

::: moniker range=">=vs-2022&quot;

1. Nella barra dei menu Visual Studio scegliere **File**  >    >  **nuovo Project**. È anche possibile premere **CTRL** + **MAIUSC** + **N**.

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/file-new-project.png&quot; alt-text=&quot;Screenshot della selezione della > File > Project dalla barra Visual Studio menu.&quot; border=&quot;false&quot;:::

   Viene visualizzata la finestra **Crea un nuovo progetto**, che mostra diversi *modelli* di progetto. Un modello contiene i file e le impostazioni di base necessari per un determinato tipo di progetto.

1. Per trovare un modello, è possibile digitare o immettere parole chiave nella casella di ricerca. L'elenco dei modelli disponibili filtra in base alle parole chiave immesse. È possibile filtrare ulteriormente i risultati del  modello scegliendo Visual Basic dall'elenco **a** discesa Tutti i linguaggi, **Windows** dall'elenco **Tutte** le piattaforme e **Console** dall'elenco Tutti i tipi **di** progetto.

   Selezionare il Visual Basic **Applicazione console** e quindi selezionare **Avanti.**

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/create-project.png&quot; alt-text=&quot;Screenshot della finestra Crea un nuovo progetto con l'Visual Basic applicazione console selezionata.&quot; border=&quot;false&quot;:::

1. Nella finestra **Configura il nuovo progetto** immettere **HelloWorld** nella casella **Project nome.** Facoltativamente, modificare il percorso della directory del progetto dal percorso predefinito C: Repository di *\\ origine \\ \<name> \\ \\ utenti* e quindi selezionare **Avanti.**

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/configure.png&quot; alt-text=&quot;Screenshot della finestra Configura il nuovo progetto con il nome del progetto HelloWorld immesso.&quot; border=&quot;false&quot;:::

1. Nella finestra **Informazioni aggiuntive** verificare che **.NET 6.0** sia visualizzato nel menu a discesa **Framework** di destinazione e quindi selezionare **Crea.**

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/additional-information.png&quot; alt-text=&quot;Screenshot della finestra Informazioni aggiuntive con il punto NET 6.0 selezionato.&quot; border=&quot;false&quot;:::

   Visual Studio crea il progetto. Il programma è una semplice applicazione &quot;Hello World&quot; che chiama il metodo <xref:System.Console.WriteLine?displayProperty=nameWithType> per visualizzare la stringa **Hello, World!** in una finestra della console.

   I file di progetto vengono visualizzati sul lato destro dell'IDE Visual Studio, in una finestra denominata Esplora soluzioni **.** Nella finestra **Esplora soluzioni** selezionare il file **Program.vb.** Il Visual Basic per l'app viene aperto nella finestra centrale dell'editor, che occupa la maggior parte dello spazio.

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/open-program.png&quot; alt-text=&quot;Screenshot che mostra il Visual Studio ID E con il codice Program dot V B nell'editor.&quot; border=&quot;false&quot;:::

   Il codice viene colorato automaticamente per indicare parti diverse, ad esempio parole chiave e tipi. I numeri di riga consentono di individuare il codice.

   Piccole linee tratteggiate verticali nel codice indicano la struttura del codice o i blocchi di codice che si uniscono tra loro. È anche possibile selezionare i piccoli segni meno o più boxed per comprimere o espandere blocchi di codice. Questa funzionalità di struttura del codice consente di nascondere il codice che non è necessario visualizzare, riducendo al minimo il disordine sullo schermo.

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/editor-features.png&quot; alt-text=&quot;Screenshot che mostra la Visual Studio ID E con caselle rosse.&quot; border=&quot;false&quot;:::

   Sono disponibili molti altri menu e finestre degli strumenti.

1. Avviare l'app scegliendo  >  **Debug Avvia senza eseguire** debug dal menu Visual Studio superiore. È anche possibile premere **CTRL** + **F5.**

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/start-without-debugging.png&quot; alt-text=&quot;Screenshot che mostra la voce di menu Debug > menu Avvia senza eseguire debug.&quot; border=&quot;false&quot;:::

   Visual Studio compila l'app e apre una finestra della console con il messaggio **Hello World!**. Ed ecco un'app in esecuzione.

   :::image type=&quot;content&quot; source=&quot;../media/vs-2019/overview-console-window.png&quot; alt-text=&quot;Screenshot della finestra di Console di debug che mostra l'output Hello World! e Premere un tasto qualsiasi per chiudere questa finestra.&quot; border=&quot;false&quot;:::

1. Per chiudere la finestra della console, premere un tasto qualsiasi.

1. Aggiungere altro codice all'app. Aggiungere il codice Visual Basic seguente prima della riga `Console.WriteLine(&quot;Hello World!")`:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Questo codice visualizza **Qual è il tuo nome?** nella finestra della console e quindi attende che l'utente immissione di testo.

1. Modificare la riga che `Console.WriteLine("Hello World!")` indica la riga seguente:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Eseguire di nuovo l'app selezionando **Debug** > **Avvia senza eseguire** debug o premendo **CTRL** + **F5.**

   Visual Studio ricompila l'app, viene aperta una finestra della console e viene richiesto il nome.

1. Digitare il nome nella finestra della console e premere **INVIO.**

   :::image type="content" source="../media/vs-2022/overview-console-input.png" alt-text="Screenshot della finestra Console di debug che mostra la richiesta di un nome, l'input e l'output Hello Hellotte!." border="false":::

1. Premere un tasto qualsiasi per chiudere la finestra della console e arrestare l'esecuzione del programma.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Usare refactoring ed esplorazione

Di seguito sono descritti due modi in cui è possibile usare il [refactoring](../../ide/refactoring-in-visual-studio.md) e [IntelliSense](../../ide/using-intellisense.md) per creare codice in modo più efficace.

Rinominare prima di tutto la `name` variabile:

1. Fare doppio clic sulla `name` variabile e digitare il nuovo nome per la variabile, *nomeutente*.

   Viene visualizzata una casella intorno alla variabile e sul margine viene visualizzata una lampadina.

1. Selezionare l'icona a forma di lampadina per visualizzare [le azioni rapide disponibili.](../../ide/quick-actions.md) Selezionare **Rinomina 'nome' in 'nomeutente'**.

   ::: moniker range="<=vs-2019"
   ![Screenshot che mostra l'azione Rinomina in Visual Studio.](media/rename-quick-action.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022&quot;
   :::image type=&quot;content&quot; source=&quot;media/vs-2022/rename.png&quot; alt-text=&quot;Screenshot che mostra l'azione Rinomina in Visual Studio.&quot; border=&quot;false&quot;:::
   ::: moniker-end

   La variabile viene rinominata nel progetto, che in questo caso è solo due posizioni.

A questo punto, esaminare IntelliSense.

1. Sotto la riga , `Console.WriteLine(&quot;Hello &quot; + username + &quot;!")` digitare il codice seguente:

   ```vb
   Dim now = Date.
   ```
   
   Una casella visualizza i membri della classe <xref:System.DateTime>. La descrizione del membro attualmente selezionato viene visualizzata anche in una casella separata.

   ::: moniker range="<=vs-2019"
   ![Screenshot che mostra i membri dell'elenco IntelliSense in Visual Studio.](media/intellisense-list-members.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   :::image type="content" source="media/vs-2022/intellisense-list-members.png" alt-text="Screenshot che mostra i membri dell'elenco IntelliSense in Visual Studio." border="false":::
   ::: moniker-end

1. Scegliere il membro **denominato Now**, che è una proprietà della classe . Fare doppio clic su **Now (Ora)** oppure selezionarlo e premere **TAB.**

1. Sotto tale riga immettere le righe di codice seguenti:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> è diverso <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> da in perché non aggiunge un terminatore di riga dopo la stampa. Ciò significa che la parte successiva del testo che viene inviata all'output verrà stampata sulla stessa riga. È possibile passare il mouse su ognuno di questi metodi nel codice per visualizzarne le descrizioni.

Usare quindi di nuovo il refactoring per rendere il codice un po' più conciso.

::: moniker range="<=vs-2019"
1. Selezionare la variabile `now` nella riga `Dim now = Date.Now` . Sul margine della riga viene visualizzata un'icona a forma di cacciavite.

1. Selezionare l'icona a forma di cacciavite per visualizzare i suggerimenti disponibili Visual Studio. In questo caso viene illustrato il refactoring delle variabili temporanee [inline](../../ide/reference/inline-temporary-variable.md) per rimuovere una riga di codice senza modificare il comportamento complessivo del codice.

   ![Screenshot che mostra il suggerimento di variabile temporanea inline in Visual Studio.](media/inline-temporary-variable-refactoring.png)

1. Selezionare **Variabile temporanea inline per** eseguire il refactoring del codice.

1. Eseguire di nuovo il programma premendo **CTRL** + **F5.** L'output è simile al seguente:

   ![Screenshot della finestra Console di debug che mostra la richiesta di un nome, l'input e l'output.](../media/vs-2019/overview-console-final.png)
   ::: moniker-end

::: moniker range=">=vs-2022"
1. Selezionare la variabile `now` nella riga `Dim now = Date.Now` . Sul margine della riga viene visualizzata un'icona a forma di lampadina.

1. Selezionare l'icona lampadina per visualizzare i suggerimenti disponibili Visual Studio. In questo caso viene illustrato il refactoring delle variabili temporanee [inline](../../ide/reference/inline-temporary-variable.md) per rimuovere una riga di codice senza modificare il comportamento complessivo del codice.

   :::image type="content" source="media/vs-2022/inline-temporary-variable.png" alt-text="Screenshot che mostra il suggerimento di variabile temporanea inline in Visual Studio." border="false":::

1. Selezionare **Variabile temporanea inline per** eseguire il refactoring del codice.

1. Eseguire di nuovo il programma premendo **CTRL** + **F5.** L'output è simile al seguente:

   :::image type="content" source="../media/vs-2022/overview-console-final.png" alt-text="Screenshot della finestra Console di debug che mostra la richiesta di un nome, l'input e l'output." border="false":::
::: moniker-end

## <a name="debug-code"></a>Debug del codice

Quando si scrive codice, è necessario eseguirlo e testarlo per verificare la ricerca di bug. Il sistema di debug di Visual Studio consente di esaminare il codice un'istruzione alla volta e controllare le variabili man mano. È possibile impostare punti *di interruzione* che arrestino l'esecuzione del codice in una determinata riga e osservare come cambia il valore della variabile durante l'esecuzione del codice.

Impostare un punto di interruzione per visualizzare il valore `username` della variabile durante l'esecuzione del programma.

1. Impostare un punto di interruzione sulla riga di codice facendo clic sul margine all'estrema sinistra, o barra `Console.WriteLine("Hello " + username + "!")` di margine, accanto alla riga. È anche possibile selezionare la riga di codice e quindi premere **F9.**

   Nella barra di margine viene visualizzato un cerchio rosso e la linea è evidenziata.

   ::: moniker range="<=vs-2019"
   ![Screenshot che mostra un punto di interruzione in una riga di codice in Visual Studio.](media/breakpoint.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   :::image type="content" source="media/vs-2022/breakpoint.png" alt-text="Screenshot che mostra un punto di interruzione in una riga di codice in Visual Studio." border="false":::
   ::: moniker-end

1. Avviare il debug selezionando **Debug**  >  **Avvia debug** o premendo **F5.**

1. Quando viene visualizzata la finestra della console e viene chiesto di specificare il proprio nome, immettere il proprio nome.

   Lo stato attivo torna all'editor Visual Studio codice e la riga di codice con il punto di interruzione è evidenziata in giallo. L'evidenziazione gialla indica che questa riga di codice verrà eseguita successivamente. Il punto di interruzione consente all'app di sospendere l'esecuzione in questa riga.

1. Passare il mouse sulla variabile `username` per impostarne il valore. È anche possibile fare clic con il pulsante destro del mouse su e scegliere Aggiungi espressioni di controllo per aggiungere la variabile alla finestra Espressioni di controllo, in cui è anche possibile `username` visualizzarne il  valore. 

   ::: moniker range="<=vs-2019"
   ![Screenshot che mostra un valore di variabile durante il debug in Visual Studio.](media/debugging-variable-value.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   :::image type="content" source="media/vs-2022/inspect-variable.png" alt-text="Screenshot che mostra un valore di variabile durante il debug in Visual Studio." border="false":::
   ::: moniker-end

1. Premere **di nuovo F5** per completare l'esecuzione dell'app.

Per altre informazioni sul debug in Visual Studio, vedere la presentazione [delle funzionalità del debugger.](../../debugger/debugger-feature-tour.md)

## <a name="next-steps"></a>Passaggi successivi

Esplorare più approfonditamente Visual Studio seguendo uno di questi articoli introduttivi:

> [!div class="nextstepaction"]
> [Informazioni su come usare l'editor del codice](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Informazioni su progetti e soluzioni](tutorial-projects-solutions.md)

## <a name="see-also"></a>Vedi anche

- Altre [informazioni Visual Studio funzionalità .](../../ide/advanced-feature-overview.md)
- Visitare [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/).
- Leggere il [blog Visual Studio .](https://devblogs.microsoft.com/visualstudio/)
