---
title: Creare un'app Web ASP.NET Core in C#
description: Informazioni dettagliate su come creare un'app Web Hello World in Visual Studio con C# e ASP.NET Core.
ms.custom: vs-acquisition
ms.date: 11/06/2019
ms.topic: quickstart
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 974f6bf70d6866893a61a14f9e2999ba265fb166
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635980"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Guida introduttiva: Usare Visual Studio per creare la prima app Web ASP.NET Core

In questa introduzione di 5-10 minuti che spiega come usare Visual Studio viene creata un'app Web "Hello World" semplice tramite un modello di progetto ASP.NET e il linguaggio di programmazione C#.

## <a name="before-you-begin"></a>Prima di iniziare

### <a name="install-visual-studio"></a>Installare Visual Studio

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2022"

Se non è già stato installato Visual Studio 2022 Preview, passare alla pagina dei download di [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) per installarlo gratuitamente.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Scegliere il tema (facoltativo)

Questa esercitazione introduttiva include screenshot in cui viene usato il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](quickstart-personalize-the-ide.md).

## <a name="create-a-project"></a>Creare un progetto

Per iniziare, creare un progetto di applicazione Web ASP.NET Core. Il tipo di progetto include fin dall'inizio tutti i file di modello necessari per creare un'app Web.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

1. Nella barra dei menu superiore scegliere **File** > **Nuovo** > **Project**.

1. Nel riquadro a sinistra della finestra di dialogo **Nuovo progetto** espandere **Visual C#** e scegliere **.NET Core**. Nel riquadro centrale scegliere **Applicazione Web ASP.NET Core**. <br/><br/>Denominare il file `HelloWorld` e scegliere **OK**.

   ![Creare un progetto dell'applicazione Web ASP.NET Core per C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Se non viene visualizzata la categoria dei modelli di progetto **.NET Core** scegliere il collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro. A seconda delle impostazioni di visualizzazione, potrebbe essere necessario scorrere la pagina per visualizzarla.
   >
   > ![Aprire Programma di installazione di Visual Studio dalla finestra di dialogo Nuovo progetto](../ide/media/open-visual-studio-installer.png)
   >
   > Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web** e quindi scegliere **Modifica**.
   >
   > ![Carico di lavoro ASP.NET nel programma di installazione di Visual Studio](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Potrebbe essere necessario chiudere Visual Studio prima di continuare l'installazione del nuovo carico di lavoro.)

1. Nella finestra di dialogo **Nuova applicazione Web ASP.NET Core** selezionare **ASP.NET Core 2.1** nel menu a discesa in alto. Scegliere quindi **Applicazione Web** e **OK**.

   ![Finestra di dialogo Nuova applicazione Web ASP.NET Core](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Se **ASP.NET Core 2.1** non è visualizzato, assicurarsi di usare la versione più recente di Visual Studio. Per altre informazioni su come aggiornare l'installazione, vedere la pagina [Aggiornare Visual Studio alla versione più recente](../install/update-visual-studio.md).

Dopo pochi istanti, Visual Studio apre il file di progetto.

::: moniker-end

::: moniker range=">=vs-2019"

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

   :::image type="content" source="../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="Visualizzare la finestra Crea un nuovo progetto":::

1. Nella finestra **Crea un nuovo progetto** scegliere **C#** dall'elenco Linguaggio. Scegliere quindi **Windows** dall'elenco Piattaforma e **Web** dall'elenco dei tipi di progetto.

      Dopo aver applicato i filtri del linguaggio, della piattaforma e del tipo di progetto, **scegliere il ASP.NET Core app Web** e quindi scegliere **Avanti.**

   :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="Scegliere il modello C# per l'ASP.NET Core Web":::

   > [!NOTE]
   > Se il modello app  Web ASP.NET Core non è visualizzato, è possibile installarlo dalla finestra **Crea un nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > A questo punto scegliere il carico di lavoro **Sviluppo ASP.NET e Web** nel programma di installazione di Visual Studio.
   >
   > ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Se viene chiesto di salvare, procedere. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *HelloWorld* nella casella **Nome del progetto**. Scegliere quindi **Avanti.**

    :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png" alt-text="nella finestra &quot;Configura il nuovo progetto&quot;, denominare il progetto &quot;MyCoreApp&quot;":::

1. Nella finestra **Informazioni aggiuntive** verificare che **.NET Core 3.1** sia visualizzato nel menu a discesa in alto. Si noti che è possibile scegliere di abilitare il supporto di Docker selezionando la casella. È anche possibile aggiungere il supporto per l'autenticazione facendo clic sul pulsante Cambia autenticazione. Da qui è possibile scegliere tra:
    - Nessuna: nessuna autenticazione.
    - Singoli account: vengono archiviati in un database locale o basato su Azure.
    - Microsoft Identity Platform: questa opzione usa Active Directory, Azure AD o Microsoft 365 per l'autenticazione.
    - Windows: adatto per le applicazioni Intranet.
    
    Lasciare **deselezionata la casella Abilita Docker** e selezionare **Nessuno per** Tipo di autenticazione. Scegliere quindi **Create** (Crea).

   :::image type="content" source="../get-started/csharp/media/vs-2019/aspnet-core-additional-information.png" alt-text="Nella finestra &quot;Informazioni aggiuntive&quot; assicurarsi che sia selezionato .NET Core 3.1 e lasciare tutte le impostazioni predefinite":::

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-and-run-the-app"></a>Creare ed eseguire l'app

::: moniker range="vs-2017"

1. In **Esplora soluzioni** espandere la cartella **Pagine** e quindi scegliere **About.cshtml**.

   ![Screenshot della Visual Studio Esplora soluzioni che mostra i file nel progetto HelloWorld. La cartella Pages viene espansa ed è selezionato About.cshtml.](../ide/media/csharp-aspnet-about-page-html-file.png)

   Questo file corrisponde a una pagina denominata **Informazioni su** nell'app Web, eseguita in un Web browser.

   ![Pagina di informazioni nell'app Web](../ide/media/csharp-aspnet-about-page.png)

   Nell'editor viene visualizzato il codice HTML per l'area delle "informazioni aggiuntive" della pagina **Informazioni su**.

   ![Codice HTML per l'area delle informazioni aggiuntive nell'editor di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Modificare il testo "informazioni aggiuntive" in "**Hello World!**".

   ![Modifica del codice HTML predefinito per l'area delle informazioni aggiuntive nell'editor di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. In **Esplora soluzioni** espandere **About.cshtml** e quindi scegliere **About.cshtml**. Questo file corrisponde anche alla pagina **Informazioni su** di un Web browser.

   ![Screenshot della Visual Studio Esplora soluzioni che mostra i file nel progetto HelloWorld. About.cshtml viene espanso ed è selezionato About.cshtml.cs.](../ide/media/csharp-aspnet-about-page-code-file.png)

   Nell'editor si noterà il codice C# che include il testo per l'area della "descrizione dell'applicazione" della pagina **Informazioni su**.

   ![Codice C# per l'area della descrizione dell'applicazione nell'editor di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Modificare il testo del messaggio "descrizione dell'applicazione" in "**Qual è il mio messaggio?**".

   ![Modifica del testo del messaggio predefinito per l'area della descrizione dell'applicazione nell'editor di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Scegliere **IIS Express** o premere **CTRL**+**F5** per eseguire l'app e aprirla in un Web browser.

   ![Selezionare il pulsante IIS Express in Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Se viene visualizzato il messaggio di errore **Impossibile connettersi al server Web "IIS Express"** o un messaggio di errore in cui viene indicato un certificato SSL, chiudere Visual Studio. Aprire quindi Visual Studio usando l'opzione **Esegui come amministratore** dal menu di scelta rapida. Eseguire quindi di nuovo l'applicazione.

1. Nel Web browser verificare che la pagina **Informazioni su** includa il testo aggiornato.

   ![Visualizzare la pagina About aggiornata che include le modifiche apportate](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Chiudere il Web browser.

### <a name="review-your-work"></a>Esaminare il lavoro

Visualizzare l'animazione seguente per verificare il lavoro completato nella sezione precedente.

  ![Visualizzare il file animato con estensione gif che illustra come creare ed eseguire una semplice app Web ASP.NET Core C# in Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di C#, ASP.NET Core e dell'IDE (ambiente di sviluppo integrato) di Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Nel **Esplora soluzioni** espandere la **cartella Pages** e quindi scegliere **Index.cshtml.**

   ![Scegliere il file Index.cshtml dal Esplora soluzioni](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Questo file corrisponde a una pagina denominata **Home** nell'app Web, che viene eseguita in un Web browser.

   ![Pagina di informazioni nell'app Web](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   Nell'editor verrà visualizzato il codice HTML per il testo visualizzato nella **home** page.

   ![Codice HTML nel file Index.cshtml per la home page nell Visual Studio editor](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. Modificare il testo "Welcome" (Benvenuto) in "**Hello World!**".

   ![Nell'editor Visual Studio modificare il codice HTML predefinito che indica il Hello World invece](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Scegliere **IIS Express** o premere **CTRL**+**F5** per eseguire l'app e aprirla in un Web browser.

   ![Selezionare il pulsante IIS Express in Visual Studio](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > Se viene visualizzato il messaggio di errore **Impossibile connettersi al server Web "IIS Express"** o un messaggio di errore in cui viene indicato un certificato SSL, chiudere Visual Studio. Aprire quindi Visual Studio usando l'opzione **Esegui come amministratore** dal menu di scelta rapida. Eseguire quindi di nuovo l'applicazione.

1. Nel Web browser verificare che la **home** page includa il testo aggiornato.

   ![Visualizzare la home page aggiornata che include le modifiche apportate](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Chiudere il Web browser.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulla creazione di ASP.NET web, continuare con l'esercitazione seguente:

> [!div class="nextstepaction"]
> [Introduzione a C# e ad ASP.NET Core in Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

In caso contrario, informazioni su come contenitorizzare l'app Web con Docker:

> [!div class="nextstepaction"]
> [Strumenti contenitore in Visual Studio](../containers/overview.md)

## <a name="see-also"></a>Vedi anche

[Eseguire la pubblicazione di un'app Web in Servizio app di Azure con Visual Studio](../deployment/quickstart-deploy-to-azure.md)
