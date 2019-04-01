---
title: 'Esercitazione: Introduzione a C# e ad ASP.NET Core'
titleSuffix: ''
description: Informazioni dettagliate su come creare un'app web ASP.NET Core in Visual Studio con C#.
ms.custom: seodec18, get-started
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: cb45386795077289e14e19ec9ad7e0071521db22
ms.sourcegitcommit: 8d453b345c72339c37b489a140dad00b244e6ba4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/26/2019
ms.locfileid: "58475903"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Esercitazione: Introduzione a C# e ad ASP.NET Core in Visual Studio

In questa esercitazione per lo sviluppo in C# con ASP.NET Core tramite Visual Studio si creerà un'app Web ASP.NET Core in C#, si apporteranno modifiche, si esploreranno alcune funzionalità dell'ambiente IDE e quindi si eseguirà l'app.

## <a name="before-you-begin"></a>Prima di iniziare

### <a name="install-visual-studio"></a>Installare Visual Studio

::: moniker range="vs-2017"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+rc) per installarlo gratuitamente.

::: moniker-end

### <a name="update-visual-studio"></a>Aggiornare Visual Studio

Se Visual Studio è già installato, verificare che si stia usando la versione più recente. Per altre informazioni su come aggiornare l'installazione, vedere la pagina [Aggiornare Visual Studio alla versione più recente](../../install/update-visual-studio.md).

### <a name="choose-your-theme-optional"></a>Scegliere il tema (facoltativo)

Questa esercitazione include screenshot in cui viene usato il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](../../ide/quickstart-personalize-the-ide.md).

## <a name="create-a-project"></a>Creare un progetto

Prima di tutto è necessario creare un progetto ASP.NET Core. Il tipo di progetto include fin dall'inizio tutti i file modello necessari per un sito Web completo funzionante.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual C#**, espandere **Web** e quindi scegliere **.NET Core**. Nel riquadro centrale scegliere **Applicazione Web ASP.NET Core**. Quindi denominare il file *MyCoreApp* e scegliere **OK**.

   ![Modello di progetto di applicazione Web ASP .NET Core nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>Aggiungere un carico di lavoro (facoltativo)

Se il modello di progetto **Applicazione Web ASP.NET Core** non è visualizzato, è possibile ottenerlo aggiungendo il carico di lavoro **Sviluppo ASP.NET e Web**. È possibile aggiungere questo carico di lavoro in uno dei due modi seguenti, a seconda degli aggiornamenti di Visual Studio 2017 installati nel computer.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opzione 1: usare la finestra di dialogo Nuovo progetto

1. Selezionare il collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**. A seconda delle impostazioni di visualizzazione, potrebbe essere necessario scorrere la pagina per visualizzarla.

   ![Selezionare il collegamento Apri il programma di installazione di Visual Studio dalla finestra di dialogo Nuovo progetto](../media/open-visual-studio-installer-mycoreapp.png)

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web** e quindi scegliere **Modifica**.

   ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../media/tutorial-aspnet-workload.png)

   (Potrebbe essere necessario chiudere Visual Studio prima di continuare l'installazione del nuovo carico di lavoro.)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opzione 2: usare la barra del menu Strumenti

1. Uscire dalla finestra di dialogo **Nuovo progetto**. Quindi, nella barra dei menu superiore scegliere **Strumenti** > **Get Tools and Features** (Ottieni strumenti e funzionalità).

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web** e quindi scegliere **Modifica**.

   (Potrebbe essere necessario chiudere Visual Studio prima di continuare l'installazione del nuovo carico di lavoro.)

### <a name="add-a-project-template"></a>Aggiungere un modello di progetto

1. Nella finestra di dialogo **Nuova applicazione Web ASP.NET Core** scegliere il modello di progetto **Applicazione Web**.

1. Verificare che **ASP.NET Core 2.1** venga visualizzato nel menu a discesa in alto. Scegliere quindi **OK**.

   ![Finestra di dialogo Nuova applicazione Web ASP.NET Core](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Se **ASP.NET Core 2.1** o versione successiva non è presente nel menu a discesa in alto, verificare se si sta eseguendo la versione più recente di Visual Studio. Per altre informazioni su come aggiornare l'installazione, vedere la pagina [Aggiornare Visual Studio alla versione più recente](../../install/update-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Visualizzare la finestra "Crea un nuovo progetto"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *ASP.NET* nella casella di ricerca. Scegliere quindi **C#**  dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato i filtri di linguaggio e piattaforma, scegliere il modello **Applicazione Web ASP.NET Core**, quindi scegliere **Avanti**.

   ![Selezionare il modello C# per l'applicazione Web ASP.NET Core](./media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Se il modello **Applicazione Web ASP.NET Core** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Scegliere quindi il carico di lavoro **Sviluppo ASP.NET e Web** nel programma di installazione di Visual Studio.
   >
   > ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Scegliere quindi il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *MyCoreApp* nella casella **Nome del progetto**. Scegliere **Crea**.

   ![nella finestra "Configura il nuovo progetto", denominare il progetto "MyCoreApp"](./media/vs-2019/csharp-name-your-aspnet-mycoreapp-project.png)

1. Nella finestra **Crea una nuova applicazione Web ASP.NET Core** verificare che **ASP.NET Core 2.1** o versione successiva venga visualizzato nel menu a discesa in alto. Scegliere quindi **Applicazione Web** che include un esempio di Razor Pages. Infine scegliere **Crea**.

   ![Finestra "Crea una nuova applicazione Web ASP.NET Core"](./media/vs-2019/csharp-create-aspnet-core-razor-pages-app.png)

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

### <a name="about-your-solution"></a>Informazioni sulla soluzione

Questa soluzione segue lo schema progettuale **Pagina Razor**. È diverso dallo schema progettuale [Model-View-Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x), in quanto è semplificato in modo da includere il codice del modello e del controller all'interno della pagina Razor stessa.

## <a name="tour-your-solution"></a>Presentazione della soluzione

 1. Il modello di progetto crea una soluzione con un unico progetto ASP.NET Core denominato _MyCoreApp_. Scegliere la scheda **Esplora soluzioni** per visualizzarne il contenuto.

    ![Esplora soluzioni di ASP.NET in Visual Studio per la soluzione Razor Pages denominata MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Espandere la cartella **Pagine** e quindi espandere *About.cshtml*.

     ![File About.cshtml in Esplora soluzioni in Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Visualizzare il file **About.cshtml** nell'editor del codice.

     ![Visualizzare il file About.cshtml nell'editor del codice di Visual Studio](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Scegliere il file **About.cshtml.cs**.

     ![Scegliere il file About.cshtml.cs nell'editor del codice di Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Visualizzare il file **About.cshtml.cs** nell'editor del codice.

     ![Visualizzare il file About.cshtml nell'editor del codice di Visual Studio](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Il progetto contiene una cartella **wwwroot** che rappresenta la radice del sito Web. Espandere la cartella per visualizzarne il contenuto.

     ![Cartella wwwroot in Esplora soluzioni in Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    È possibile inserire il contenuto statico del sito &mdash;ad esempio CSS, immagini e librerie JavaScript&mdash; direttamente nei percorsi desiderati.

 1. Il progetto contiene anche file di configurazione che gestiscono l'app Web in fase di esecuzione. La [configurazione](/aspnet/core/fundamentals/configuration) predefinita dell'applicazione è archiviata in *appsettings.json*. È possibile eseguire comunque l'override di queste impostazioni con *appsettings.Development.json*. Per visualizzare il file **appsettings.Development.json**, espandere il file **appsettings.json**.

     ![File di configurazione in Esplora soluzioni in Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Esecuzione, debug e modifiche

1. Scegliere il pulsante **IIS Express** nell'IDE per compilare ed eseguire l'app in modalità di debug. In alternativa, premere **F5**, oppure scegliere **Debug** > **Avvia debug** dalla barra dei menu.

     ![Selezionare il pulsante IIS Express in Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Se viene visualizzato il messaggio di errore **Non è possibile connettersi al server Web 'IIS Express'**, chiudere Visual Studio e quindi aprirlo usando l'opzione **Esegui come amministratore** dal menu di scelta rapida. Eseguire quindi di nuovo l'applicazione.
     >
     > Potrebbe essere visualizzato un messaggio in cui si chiede se accettare un certificato SSL di IIS Express. Per visualizzare il codice in un Web browser, scegliere **Yes** (Sì), quindi scegliere **Yes** (Sì) se si riceve un messaggio di avviso di sicurezza per il completamento. 

1. Visual Studio apre una finestra del browser. Dovrebbero essere disponibili le pagine **Home**, **About** e **Contact** nella barra dei menu. (In caso contrario, scegliere la voce di menu "Hamburger" per visualizzarle.)

    ![Selezionare la voce di menu "Hamburger" dalla barra dei menu nell'app Web](media/csharp-aspnet-razor-browser-page.png)

     > [!TIP]
     > Non è possibile modificare il codice nell'editor di codice di Visual Studio quando il progetto è aperto in una finestra del browser. 

1. Scegliere **About** dalla barra dei menu.

   ![Selezionare About nella barra dei menu della finestra del browser per l'app](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Oltre ad altre operazioni, la pagina **About** nel browser esegue il rendering del testo impostato nel file *About.cshtml*.

   ![Visualizzare il testo nella pagina informazioni su](media/csharp-aspnet-razor-browser-page-about.png)

1. Mantenere aperta la finestra del browser e tornare a Visual Studio.

1. In Visual Studio scegliere **About.cshtml**. Eliminare quindi la parola _additional_ e aggiungere al suo posto le parole _file and directory_.

    ![Modificare il testo nel file About.cshtml](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. Scegliere **About.cshtml.cs**. Eliminare poi le direttive `using` all'inizio del file usando il metodo veloce seguente:

   Scegliere una qualsiasi delle direttive `using` disattivate e una lampadina [Azioni rapide](../../ide/quick-actions.md) verrà visualizzata sotto il punto di inserimento o nel margine sinistro. Scegliere la lampadina e quindi **Rimuovi istruzioni using non necessarie**.

   ![Rimuovere le istruzioni using non necessarie nel file About.cshtml.cs](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio elimina le direttive `using` non necessarie dal file.

1. Nel metodo `OnGet()` modificare quindi il corpo con il codice seguente:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
     }
    ```
1. Si noti che vengono visualizzate due sottolineature ondulate sotto ad **Ambiente** e **Stringa** perché questi tipi non sono inclusi nell'ambito.

   ![Errori contrassegnati con sottolineature ondulate nel metodo OnGet](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Aprire la barra degli strumenti **Elenco errori** per visualizzare gli errori. (Se non viene visualizzata la barra degli strumenti **Elenco errori**, scegliere **Visualizza** > **Elenco errori** dalla barra dei menu in alto.)

   ![Elenco errori in Visual Studio](media/csharp-aspnet-razor-error-list.png)

1. Per correggere questo errore, nell'editor del codice posizionare il cursore su una riga che contiene l'errore e quindi scegliere la lampadina delle azioni rapide nel margine sinistro. Nel menu a discesa scegliere quindi **using System;** per aggiungere questa direttiva all'inizio del file e risolvere gli errori.

   ![Aggiungere la direttiva "using System;"](media/csharp-aspnet-razor-add-usings.png)

1. Premere **CTRL**+**S** per salvare le modifiche e aggiornare l'app nel Web browser.

1. Nella parte superiore del sito Web scegliere **About** per visualizzare le modifiche.

   ![Visualizzare la pagina About aggiornata che include le modifiche apportate](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Chiudere il Web browser, premere **MAIUSC**+**F5** per interrompere la modalità di debug e quindi chiudere Visual Studio.

## <a name="quick-answers-faq"></a>Domande frequenti con risposta rapida

Ecco una rapida serie di domande frequenti per evidenziare alcuni concetti chiave.

### <a name="what-is-c"></a>Che cos'è C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) è un linguaggio di programmazione indipendente dai tipi e orientato agli oggetti progettato per garantire solidità e facilità di apprendimento.

### <a name="what-is-aspnet-core"></a>Che cos'è ASP.NET Core?

ASP.NET Core è un framework open source e multipiattaforma per la compilazione di applicazioni connesse a Internet, ad esempio applicazioni e servizi Web. Le app ASP.NET Core possono essere eseguite in .NET Core o in .NET Framework. È possibile sviluppare ed eseguire app ASP.NET Core multipiattaforma in Windows, Mac e Linux. ASP.NET Core è disponibile open source in [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>Che cos'è Visual Studio?

Visual Studio è una suite integrata per lo sviluppo di strumenti di produttività per gli sviluppatori. Si può immaginare Visual Studio come un programma utilizzabile per creare programmi e applicazioni.

## <a name="next-steps"></a>Passaggi successivi

L'esercitazione è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di C#, ASP.NET Core e dell'IDE di Visual Studio. Per altre informazioni sulla creazione di un'app Web o di un sito Web con C# e ASP.NET, continuare con le esercitazioni seguenti:

> [!div class="nextstepaction"]
> [Creare un'app Web Razor Pages con ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>Vedere anche

[Publish your web app to Azure App Service by using Visual Studio](../../deployment/quickstart-deploy-to-azure.md) (Pubblicare l'app Web in Servizio app di Azure con Visual Studio)
