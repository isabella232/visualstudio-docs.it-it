---
title: 'Esercitazione: Introduzione a C# e ASP.NET Core'
titleSuffix: ''
description: Informazioni dettagliate su come creare un'app web ASP.NET Core in Visual Studio con C#.
ms.custom: vs-acquisition, get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 8a7d6b0d29181ea464c8e98325e0c1ade53a45dd
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128426955"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Esercitazione: introduzione a C# e ad ASP.NET Core in Visual Studio

In questa esercitazione per lo sviluppo in C# con ASP.NET Core tramite Visual Studio si creerà un'app Web ASP.NET Core in C#, si apporteranno modifiche, si esploreranno alcune funzionalità dell'ambiente IDE e quindi si eseguirà l'app.

## <a name="prerequisites"></a>Prerequisiti

1. Installare Visual Studio
   ::: moniker range="vs-2017"
   
   Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.
   
   ::: moniker-end
   
   ::: moniker range=">=vs-2019"
   
   Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.
   
   ::: moniker-end

1. Aggiornare Visual Studio: se è già stato installato Visual Studio, assicurarsi di eseguire la versione più recente. Per altre informazioni su come aggiornare l'installazione, vedere la [pagina Aggiornamento Visual Studio alla versione più](../../install/update-visual-studio.md) recente.

1. Scegliere il tema (facoltativo): questa esercitazione include screenshot che usano il tema scuro. È possibile [personalizzare l'IDE Visual Studio e la pagina Editor](../../ide/quickstart-personalize-the-ide.md) per altre informazioni.

## <a name="create-a-project"></a>Creare un progetto

Prima di tutto è necessario creare un progetto ASP.NET Core. Il tipo di progetto include fin dall'inizio tutti i file modello necessari per un sito Web completo funzionante.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Nella barra dei menu superiore scegliere **File** > **Nuovo** > **Project**.

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

1. Uscire dalla finestra di dialogo **Nuovo progetto**. Quindi, nella barra dei menu superiore scegliere **Strumenti**  >  **Ottieni strumenti e funzionalità**.

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web** e quindi scegliere **Modifica**.

   (Potrebbe essere necessario chiudere Visual Studio prima di continuare l'installazione del nuovo carico di lavoro.)

### <a name="add-a-project-template"></a>Aggiungere un modello di progetto

1. Nella finestra di dialogo **Nuova applicazione Web ASP.NET Core** scegliere il modello di progetto **Applicazione Web**.

1. Verificare che **ASP.NET Core 2.1** venga visualizzato nel menu a discesa in alto. Scegliere quindi **OK.**

   ![Finestra di dialogo Nuova applicazione Web ASP.NET Core](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Se **ASP.NET Core 2.1** non è presente nel menu a discesa in alto, verificare se sia un uso la versione più recente di Visual Studio. Per altre informazioni su come aggiornare l'installazione, vedere la [pagina Aggiornamento Visual Studio alla versione più](../../install/update-visual-studio.md) recente.

::: moniker-end

::: moniker range="vs-2019"

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

   :::image type="content" source="../../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="Screenshot che mostra la Visual Studio iniziale con l'opzione &quot;Crea un nuovo progetto&quot; evidenziata.":::

1. Nella finestra **Crea un nuovo progetto** scegliere **C#** dall'elenco Linguaggio. Scegliere quindi **Windows** dall'elenco Piattaforma e **Web** dall'elenco dei tipi di progetto.

      Dopo aver applicato i filtri del linguaggio, della piattaforma e del tipo di progetto, **scegliere il modello app Web ASP.NET Core** e quindi scegliere **Avanti.**

   :::image type="content" source="./media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="Screenshot che mostra il ASP.NET Core di progetto app Web evidenziato nella finestra di dialogo Project nuova app.":::

   > [!NOTE]
   > Se il modello app **Web ASP.NET Core** non è visualizzato, è possibile installarlo dalla finestra Crea un **nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Screenshot che mostra il collegamento "Installa altri strumenti e funzionalità" che fa parte del messaggio "Non è possibile trovare ciò che si sta cercando".](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > A questo punto scegliere il carico di lavoro **Sviluppo ASP.NET e Web** nel programma di installazione di Visual Studio.
   >
   > ![Screenshot che mostra il carico di lavoro Sviluppo multipiattaforma .NET Core nella Programma di installazione di Visual Studio.](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Se viene chiesto di salvare, procedere. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *MyCoreApp* nella casella **Nome del progetto**. Scegliere quindi **Avanti.**

   :::image type="content" source="./media/vs-2019/csharp-name-your-aspnet-app.png" alt-text="Screenshot che mostra la finestra &quot;Configura il nuovo progetto&quot; con &quot;MyCoreApp&quot; immesso nel Project nome.":::

1. Nella finestra **Informazioni aggiuntive** verificare che **.NET Core 3.1** sia visualizzato nel menu a discesa in alto. Si noti che è possibile scegliere di abilitare il supporto di Docker selezionando la casella. È anche possibile aggiungere il supporto per l'autenticazione facendo clic sul pulsante Cambia autenticazione. Da qui è possibile scegliere tra:
    - Nessuna: nessuna autenticazione.
    - Singoli account: vengono archiviati in un database locale o basato su Azure.
    - Microsoft Identity Platform: questa opzione usa Active Directory, Azure AD o Microsoft 365 per l'autenticazione.
    - Windows: adatto per le applicazioni Intranet.
    
    Lasciare **deselezionata la casella Abilita Docker** e selezionare **Nessuno per** Tipo di autenticazione. Scegliere quindi **Create** (Crea).

   :::image type="content" source="./media/vs-2019/aspnet-core-additional-information.png" alt-text="Screenshot che mostra le impostazioni predefinite nella finestra &quot;Informazioni aggiuntive&quot;. Il valore framework è '.NET Core 3.1'.":::

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

::: moniker range=">=vs-2022"

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

   :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="Screenshot che mostra la Visual Studio iniziale con l'opzione &quot;Crea un nuovo progetto&quot; evidenziata.":::

1. Nella finestra **Crea un nuovo progetto** scegliere **C#** dall'elenco Linguaggio. Scegliere quindi **Windows** dall'elenco Piattaforma e **Web** dall'elenco dei tipi di progetto.

      Dopo aver applicato i filtri del linguaggio, della piattaforma e del tipo di progetto, **scegliere il modello app Web ASP.NET Core** e quindi scegliere **Avanti.**

   :::image type="content" source="media/vs-2022/csharp-create-new-project-aspnet-core.png" alt-text="Screenshot che mostra il ASP.NET Core di progetto app Web evidenziato nella finestra di dialogo Project nuova app.":::

   > [!NOTE]
   > Se il modello app **Web ASP.NET Core** non è visualizzato, è possibile installarlo dalla finestra Crea un **nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > :::image type="content" source="media/vs-2022/not-finding-what-looking-for.png" alt-text="Screenshot che mostra il collegamento &quot;Installa altri strumenti e funzionalità&quot; che fa parte del messaggio &quot;Non è possibile trovare ciò che si sta cercando&quot;.":::
   >
   > A questo punto scegliere il carico di lavoro **Sviluppo ASP.NET e Web** nel programma di installazione di Visual Studio.
   >
   > :::image type="content" source="media/vs-2022/aspnet-core-web-dev-workload.png" alt-text="Screenshot che mostra il carico ASP.NET di sviluppo Web nel Programma di installazione di Visual Studio.":::
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Se viene chiesto di salvare, procedere. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *MyCoreApp* nella casella **Nome del progetto**. Scegliere quindi **Avanti.**

   :::image type="content" source="media/vs-2022/csharp-name-your-aspnet-app.png" alt-text="Screenshot che mostra la finestra &quot;Configura il nuovo progetto&quot; con &quot;MyCoreApp&quot; immesso nel Project nome.":::

1. Nella finestra **Informazioni aggiuntive** verificare che nel campo **Framework** sia visualizzato **.NET 6.0.** In questa finestra è possibile scegliere di abilitare il supporto di Docker selezionando la casella. È anche possibile aggiungere il supporto per l'autenticazione selezionando un valore **dall'elenco** a discesa Tipo di autenticazione . Da qui è possibile scegliere tra:

    - Nessuna: nessuna autenticazione.
    - Account singoli: autenticazioni archiviate in un database locale o basato su Azure.
    - Microsoft Identity Platform: questa opzione usa Active Directory, Azure AD o Microsoft 365 per l'autenticazione.
    - Windows: adatto per le applicazioni Intranet.
    
    Lasciare **deselezionata la casella Abilita Docker** e selezionare **Nessuno per** Tipo di autenticazione. Scegliere quindi **Create** (Crea).

   :::image type="content" source="media/vs-2022/aspnet-core-additional-information.png" alt-text="Screenshot che mostra le impostazioni predefinite nella finestra &quot;Informazioni aggiuntive&quot;. Il valore framework è '.NET 6.0'.":::

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

### <a name="about-your-solution"></a>Informazioni sulla soluzione

Questa soluzione segue lo schema progettuale **Pagina Razor**. È diverso dallo schema progettuale [Model-View-Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x&preserve-view=true), in quanto è semplificato in modo da includere il codice del modello e del controller all'interno della pagina Razor stessa.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Presentazione della soluzione

 1. Il modello di progetto crea una soluzione con un unico progetto ASP.NET Core denominato _MyCoreApp_. Scegliere la scheda **Esplora soluzioni** per visualizzarne il contenuto.

    ![Esplora soluzioni di ASP.NET in Visual Studio per la soluzione Razor Pages denominata MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Espandere la cartella **Pagine** e quindi espandere *About.cshtml*.

     ![File About.cshtml in Esplora soluzioni in Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Visualizzare il file **About.cshtml** nell'editor del codice.

     ![Screenshot che mostra le prime dieci righe del file About.cshtml nell'editor Visual Studio codice.](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Scegliere il file **About.cshtml.cs**.

     ![Scegliere il file About.cshtml.cs nell'editor del codice di Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Visualizzare il file **About.cshtml.cs** nell'editor del codice.

     ![Screenshot che mostra le prime 18 righe del file About.cshtml.cs nell'editor Visual Studio codice. ](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Il progetto contiene una cartella **wwwroot** che rappresenta la radice del sito Web. Espandere la cartella per visualizzarne il contenuto.

     ![Cartella wwwroot in Esplora soluzioni in Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    È possibile inserire il contenuto statico del sito &mdash;ad esempio CSS, immagini e librerie JavaScript&mdash; direttamente nei percorsi desiderati.

 1. Il progetto contiene anche file di configurazione che gestiscono l'app Web in fase di esecuzione. La [configurazione](/aspnet/core/fundamentals/configuration) predefinita dell'applicazione è archiviata in *appsettings.json*. È possibile eseguire comunque l'override di queste impostazioni con *appsettings.Development.json*. Per visualizzare il file **appsettings.Development.json**, espandere il file **appsettings.json**.

     ![File di configurazione in Esplora soluzioni in Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Esecuzione, debug e modifiche

1. Scegliere il pulsante **IIS Express** nell'IDE per compilare ed eseguire l'app in modalità di debug. In alternativa, premere **F5**, oppure scegliere **Debug** > **Avvia debug** dalla barra dei menu.

     ![Selezionare il pulsante IIS Express in Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Se viene visualizzato il messaggio di errore Impossibile connettersi al server Web **'IIS Express',** chiudere  Visual Studio e quindi aprirlo usando l'opzione Esegui come amministratore dal menu di scelta rapida o dal menu di scelta rapida. Eseguire quindi di nuovo l'applicazione.
     >
     > Potrebbe essere visualizzato un messaggio in cui si chiede se accettare un certificato SSL di IIS Express. Per visualizzare il codice in un Web browser, scegliere **Yes** (Sì), quindi scegliere **Yes** (Sì) se si riceve un messaggio di avviso di sicurezza per il completamento.

1. Visual Studio apre una finestra del browser. Dovrebbero essere disponibili le pagine **Home**, **About** e **Contact** nella barra dei menu. (In caso contrario, scegliere la voce di menu "Hamburger" per visualizzarle.)

    ![Selezionare la voce di menu "Hamburger" dalla barra dei menu nell'app Web](media/csharp-aspnet-razor-browser-page.png)

1. Scegliere **About** dalla barra dei menu.

   ![Selezionare About nella barra dei menu della finestra del browser per l'app](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Oltre ad altre operazioni, la pagina **About** nel browser esegue il rendering del testo impostato nel file *About.cshtml*.

   ![Visualizzare il testo nella pagina informazioni su](media/csharp-aspnet-razor-browser-page-about.png)

1. Tornare a Visual Studio e quindi premere **MAIUSC+F5** per interrompere la modalità di debug. Verrà anche chiuso il progetto nella finestra del browser.

1. In Visual Studio scegliere **About.cshtml**. Eliminare quindi la parola _un'altra_ e al suo posto aggiungere il file delle parole _e la directory_.

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

1. Premere **CTRL** + **S** per salvare le modifiche e quindi **premere F5** per aprire il progetto nel Web browser.

1. Nella parte superiore del sito Web scegliere **About** per visualizzare le modifiche.

   ![Visualizzare la pagina About aggiornata che include le modifiche apportate](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Chiudere il Web browser, premere + **MAIUSC F5** per arrestare la modalità di debug e quindi chiudere Visual Studio.

::: moniker-end

::: moniker range="=vs-2019"

## <a name="tour-your-solution"></a>Presentazione della soluzione

 1. Il modello di progetto crea una soluzione con un unico progetto ASP.NET Core denominato _MyCoreApp_. Scegliere la scheda **Esplora soluzioni** per visualizzarne il contenuto.

    ![Screenshot del Esplora soluzioni in Visual Studio il contenuto del progetto ASP.NET core denominato "MyCoreApp".](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Espandere la **cartella** Pagine.

     ![Screenshot del Esplora soluzioni in Visual Studio il contenuto della cartella Pages per "MyCoreApp".](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Visualizzare il file **Index.cshtml** nell'editor di codice.

     ![Screenshot che mostra il file Index.cshtml aperto nell'editor Visual Studio codice.](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. A ogni file con estensione cshtml è associato un file di codice. Per aprire il file di codice nell'editor, espandere il nodo **Index.cshtml** in Esplora soluzioni e scegliere il file **Index.cshtml.cs.**

     ![Screenshot dell'Esplora soluzioni in Visual Studio che mostra il file Index.cshtml.cs selezionato.](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Visualizzare il file **Index.cshtml.cs** nell'editor di codice.

     ![Screenshot che mostra il file Index.cshtml.cs aperto nell'editor Visual Studio di codice.](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Il progetto contiene una cartella **wwwroot** che rappresenta la radice del sito Web. Espandere la cartella per visualizzarne il contenuto.

     ![Screenshot dell'Esplora soluzioni nella Visual Studio che mostra il contenuto della cartella "wwwroot".](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    È possibile inserire il contenuto statico del sito &mdash;ad esempio CSS, immagini e librerie JavaScript&mdash; direttamente nei percorsi desiderati.

 1. Il progetto contiene anche file di configurazione che gestiscono l'app Web in fase di esecuzione. La [configurazione](/aspnet/core/fundamentals/configuration) predefinita dell'applicazione è archiviata in *appsettings.json*. È possibile eseguire comunque l'override di queste impostazioni con *appsettings.Development.json*. Per visualizzare il file **appsettings.Development.json**, espandere il file **appsettings.json**.

     ![Screenshot del Esplora soluzioni in Visual Studio che mostra il file appsettings.json selezionato ed espanso per visualizzare appsettings. File Development.json.](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Esecuzione, debug e modifiche

1. Scegliere il pulsante **IIS Express** nell'IDE per compilare ed eseguire l'app in modalità di debug. In alternativa, premere **F5**, oppure scegliere **Debug** > **Avvia debug** dalla barra dei menu.

     ![Screenshot che mostra il pulsante IIS Express evidenziato nell'IDE Visual Studio.](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Se viene visualizzato il messaggio di errore Impossibile connettersi al server Web **'IIS Express',** chiudere  Visual Studio e quindi aprirlo usando l'opzione Esegui come amministratore dal menu di scelta rapida o dal menu di scelta rapida. Eseguire quindi di nuovo l'applicazione.
     >
     > Potrebbe essere visualizzato un messaggio in cui si chiede se accettare un certificato SSL di IIS Express. Per visualizzare il codice in un Web browser, scegliere **Yes** (Sì), quindi scegliere **Yes** (Sì) se si riceve un messaggio di avviso di sicurezza per il completamento.

1. Visual Studio apre una finestra del browser. Nella barra dei menu dovrebbero essere quindi presenti **le pagine** **Home** e Privacy.

1. Scegliere **Privacy** dalla barra dei menu.

   La **pagina Privacy** nel browser esegue il rendering del testo impostato nel file *Privacy.cshtml.*

   ![Screenshot che mostra la pagina MyCoreApp Privacy con il testo "Use this page to detail your site's privacy policy".](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Tornare a Visual Studio e quindi premere **MAIUSC+F5** per interrompere la modalità di debug. Verrà anche chiuso il progetto nella finestra del browser.

1. In Visual Studio aprire **Privacy.cshtml per** la modifica. Eliminare quindi le parole Use this page to _detail your site's privacy policy_ (Usare questa pagina per dettagliare l'informativa sulla privacy del sito) e al suo posto aggiungere le parole This page is under construction as of ["TimeStamp"] (Questa pagina è in costruzione a _@ViewData ["TimeStamp"]_).

    ![Screenshot che mostra il file Privacy.cshtml aperto nell'editor Visual Studio codice con il testo aggiornato.](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. A questo punto, apportare una modifica al codice. Scegliere **Privacy.cshtml.cs.** Eliminare poi le direttive `using` all'inizio del file usando il metodo veloce seguente:

   Scegliere una qualsiasi delle direttive `using` disattivate e una lampadina [Azioni rapide](../../ide/quick-actions.md) verrà visualizzata sotto il punto di inserimento o nel margine sinistro. Scegliere la lampadina e quindi passare il mouse su **Rimuovi using non necessari.**

   ![Screenshot che mostra il file Privacy.cshtml nell'editor Visual Studio codice con la finestra di dialogo "Rimuovi using non necessari" aperta.](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Scegliere ora **Anteprima modifiche** per vedere cosa cambierà.

   ![Screenshot che mostra la finestra di dialogo Anteprima modifiche che mostra il nuovo elenco di 'Usings' e il codice nel file Privacy.cshtml.](media/vs-2019/csharp-aspnet-preview-changes.png)

   Scegliere **Applica**. Visual Studio elimina le direttive `using` non necessarie dal file.

1. Nel metodo `OnGet()` modificare quindi il corpo con il codice seguente:

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. Si noti che in DateTime vengono visualizzate due sottolineature **ondulate.** Le sottolineature ondulate vengono visualizzate perché questo tipo non è nell'ambito.

   ![Screenshot che mostra gli errori contrassegnati con sottolineature ondulate nel metodo OnGet.](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Aprire la barra degli strumenti **Elenco errori** per visualizzare gli errori. (Se non viene visualizzata la barra degli strumenti **Elenco errori**, scegliere **Visualizza** > **Elenco errori** dalla barra dei menu in alto.)

   ![Elenco errori in Visual Studio](media/vs-2019/csharp-aspnet-error-list.png)

1. Per correggere questo errore, nell'editor del codice posizionare il cursore su una riga che contiene l'errore e quindi scegliere la lampadina delle azioni rapide nel margine sinistro. Nel menu a discesa scegliere quindi **using System;** per aggiungere questa direttiva all'inizio del file e risolvere gli errori.

   ![Screenshot che mostra il menu Azioni rapide con un suggerimento per aggiungere la direttiva 'using System'.](media/vs-2019/csharp-aspnet-add-usings.png)

1. Premere **F5** per aprire il progetto nel Web browser.

1. Nella parte superiore del sito Web scegliere **Privacy per** visualizzare le modifiche.

   ![Screenshot che mostra la pagina Privacy aggiornata che include le modifiche apportate.](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Chiudere il Web browser, premere + **MAIUSC F5** per arrestare la modalità di debug e quindi chiudere Visual Studio.
::: moniker-end

::: moniker range=">=vs-2022"

## <a name="tour-your-solution"></a>Presentazione della soluzione

 1. Il modello di progetto crea una soluzione con un unico progetto ASP.NET Core denominato *MyCoreApp*. Scegliere la scheda **Esplora soluzioni** per visualizzarne il contenuto.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-solution-explorer-mycoreapp.png" alt-text="Screenshot del Esplora soluzioni in Visual Studio il contenuto del progetto ASP.NET core denominato &quot;MyCoreApp&quot;.":::

 1. Espandere la **cartella** Pagine.

     :::image type="content" source="media/vs-2022/csharp-aspnet-solution-explorer-pages.png" alt-text="Screenshot del Esplora soluzioni in Visual Studio che mostra il contenuto della cartella Pages per &quot;MyCoreApp&quot;.":::

 1. Visualizzare il file **Index.cshtml** nell'editor di codice.

     :::image type="content" source="media/vs-2022/csharp-aspnet-index-cshtml.png" alt-text="Screenshot che mostra il file Index.cshtml aperto nell'editor Visual Studio codice.":::

 1. A ogni file con estensione cshtml è associato un file di codice. Per aprire il file di codice nell'editor, espandere il nodo **Index.cshtml** in Esplora soluzioni e scegliere il file **Index.cshtml.cs.**

     :::image type="content" source="media/vs-2022/csharp-aspnet-choose-index-cshtml.png" alt-text="Screenshot dell'Esplora soluzioni in Visual Studio che mostra il file Index.cshtml.cs selezionato.":::

 1. Visualizzare il file **Index.cshtml.cs** nell'editor di codice.

     :::image type="content" source="media/vs-2022/csharp-aspnet-index-cshtml-editing.png" alt-text="Screenshot che mostra il file Index.cshtml.cs aperto nell'editor Visual Studio codice.":::

 1. Il progetto contiene una cartella **wwwroot** che rappresenta la radice del sito Web. Espandere la cartella per visualizzarne il contenuto.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-solution-explorer-wwwroot.png" alt-text="Screenshot del Esplora soluzioni in Visual Studio il contenuto della cartella &quot;wwwroot&quot;.":::

    È possibile inserire il contenuto statico del sito &mdash;ad esempio CSS, immagini e librerie JavaScript&mdash; direttamente nei percorsi desiderati.

 1. Il progetto contiene anche file di configurazione che gestiscono l'app Web in fase di esecuzione. La [configurazione](/aspnet/core/fundamentals/configuration) predefinita dell'applicazione è archiviata in *appsettings.json*. È possibile eseguire comunque l'override di queste impostazioni con *appsettings.Development.json*. Per visualizzare il file **appsettings.Development.json**, espandere il file **appsettings.json**.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-solution-explorer-appsettingsjson.png" alt-text="Screenshot del Esplora soluzioni in Visual Studio che mostra il file appsettings.json selezionato ed espanso per visualizzare appsettings. File Development.json.":::

## <a name="run-debug-and-make-changes"></a>Esecuzione, debug e modifiche

1. Scegliere il pulsante **IIS Express** nell'IDE per compilare ed eseguire l'app in modalità di debug. In alternativa, premere **F5**, oppure scegliere **Debug** > **Avvia debug** dalla barra dei menu.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-iisexpress.png" alt-text="Screenshot che mostra il pulsante IIS Express evidenziato nell'IDE Visual Studio.":::

     > [!NOTE]
     > Se viene visualizzato il messaggio di errore Impossibile connettersi al server Web **'IIS Express',** chiudere Visual Studio  e quindi aprirlo usando l'opzione Esegui come amministratore dal menu di scelta rapida o dal menu di scelta rapida. Eseguire quindi di nuovo l'applicazione.
     >
     > Potrebbe essere visualizzato un messaggio in cui si chiede se accettare un certificato SSL di IIS Express. Per visualizzare il codice in un Web browser, scegliere **Yes** (Sì), quindi scegliere **Yes** (Sì) se si riceve un messaggio di avviso di sicurezza per il completamento.

1. Visual Studio apre una finestra del browser. Nella barra dei menu dovrebbero essere quindi presenti **le pagine** **Home** e Privacy.

1. Scegliere **Privacy** dalla barra dei menu.

   La **pagina Privacy** nel browser esegue il rendering del testo impostato nel file *Privacy.cshtml.*

   :::image type="content" source="media/vs-2022/csharp-aspnet-browser-page-privacy.png" alt-text="Screenshot che mostra la pagina MyCoreApp Privacy con il testo &quot;Use this page to detail your site's privacy policy&quot;.":::

1. Tornare a Visual Studio e quindi premere **MAIUSC+F5** per interrompere la modalità di debug. Verrà anche chiuso il progetto nella finestra del browser.

1. In Visual Studio aprire **Privacy.cshtml per** la modifica. Eliminare quindi le parole Use this page to *detail your site's privacy policy* (Usare questa pagina per dettagliare l'informativa sulla privacy del sito) e al suo posto aggiungere le parole This page is under construction as of ["TimeStamp"] (Questa pagina è in costruzione a *@ViewData ["TimeStamp"]*).

   :::image type="content" source="media/vs-2022/csharp-aspnet-privacy-cshtml-code-changed.png" alt-text="Screenshot che mostra il file Privacy.cshtml aperto nell'editor Visual Studio codice con il testo aggiornato.":::

1. A questo punto, apportare una modifica al codice. Scegliere **Privacy.cshtml.cs.** Pulire quindi le direttive `using` all'inizio del file selezionando il collegamento seguente:

   Scegliere una qualsiasi delle direttive `using` disattivate e una lampadina [Azioni rapide](../../ide/quick-actions.md) verrà visualizzata sotto il punto di inserimento o nel margine sinistro. Scegliere la lampadina e quindi passare il mouse su **Rimuovi using non necessari.**

   :::image type="content" source="media/vs-2022/csharp-aspnet-remove-unnecessary-usings.png" alt-text="Screenshot che mostra il file Privacy.cshtml nell'editor Visual Studio codice con la finestra di dialogo &quot;Rimuovi using non necessari&quot; aperta.":::

   Scegliere ora **Anteprima modifiche** per vedere cosa cambierà.

   :::image type="content" source="media/vs-2022/csharp-aspnet-preview-changes.png" alt-text="Screenshot che mostra la finestra di dialogo Anteprima modifiche con il nuovo elenco 'Usings' e il codice nel file Privacy.cshtml.":::

   Scegliere **Applica**. Visual Studio elimina le direttive `using` non necessarie dal file.

1. Creare quindi una stringa per la data corrente formattata per le impostazioni cultura o l'area usando il [metodo DateTime.ToString.](xref:System.DateTime.ToString%2A)

   - Il primo argomento per il metodo specifica come deve essere visualizzata la data. In questo esempio viene utilizzato l'identificatore di formato ( `d` ) che indica il formato di data breve. 
   - Il secondo argomento è [l'oggetto CultureInfo](/dotnet/api/system.globalization.cultureinfo) che specifica le impostazioni cultura o l'area geografica per la data. Questo argomento determina, tra le altre cose, la lingua di qualsiasi parola nella data e il tipo di separatori usati.
 
Modificare il corpo del `OnGet()` metodo nel codice seguente:

   ```csharp
   public void OnGet()
   {
      string dateTime = DateTime.Now.ToString("d", new CultureInfo("en-US"));
      ViewData["TimeStamp"] = dateTime;
   }
   ```

1. Si noti che in CultureInfo vengono visualizzate due **sottolineature ondulate.** Le sottolineature ondulate vengono visualizzate perché questo tipo non è nell'ambito.

   :::image type="content" source="media/vs-2022/csharp-aspnet-add-new-onget-method.png" alt-text="Screenshot che mostra il metodo OnGet nell'editor di codice con una sottolineatura ondulata sotto l'oggetto CultureInfo.":::

    Aprire la barra degli strumenti **Elenco errori** per visualizzare gli errori. (Se non viene visualizzata la barra degli strumenti **Elenco errori**, scegliere **Visualizza** > **Elenco errori** dalla barra dei menu in alto.)

   :::image type="content" source="media/vs-2022/csharp-aspnet-error-list.png" alt-text="Screenshot che mostra la finestra Elenco errori in Visual Studio. Nel tipo 'CultureInfo' manca una direttiva using.":::

1. Per correggere questo errore, nell'editor del codice posizionare il cursore su una riga che contiene l'errore e quindi scegliere la lampadina delle azioni rapide nel margine sinistro. Scegliere quindi using **System.Globalization** dal menu a discesa per aggiungere la direttiva all'inizio del file e risolvere gli errori.

   :::image type="content" source="media/vs-2022/csharp-aspnet-add-usings.png" alt-text="Screenshot che mostra il menu Azioni rapide con un suggerimento per aggiungere la direttiva 'using System.Globalization'.":::

1. Premere **F5** per aprire il progetto nel Web browser.

1. Nella parte superiore del sito Web scegliere **Privacy per** visualizzare le modifiche.

   :::image type="content" source="media/vs-2022/csharp-aspnet-browser-page-privacy-changed.png" alt-text="Screenshot che mostra la pagina Privacy di MyCoreApp che include le modifiche apportate per aggiungere la data.":::

1. Chiudere il Web browser, premere + **MAIUSC F5** per arrestare la modalità di debug e quindi chiudere Visual Studio.

::: moniker-end

## <a name="quick-answers-faq"></a>Domande frequenti con risposta rapida

Ecco una rapida serie di domande frequenti per evidenziare alcuni concetti chiave.

### <a name="what-is-c"></a>Che cos'è C#?

[C#](/dotnet/csharp/tour-of-csharp/) è un linguaggio di programmazione indipendente dai tipi e orientato agli oggetti progettato per garantire solidità e facilità di apprendimento.

### <a name="what-is-aspnet-core"></a>Che cos'è ASP.NET Core?

ASP.NET Core è un framework open source e multipiattaforma per la compilazione di applicazioni connesse a Internet, ad esempio applicazioni e servizi Web. Le app ASP.NET Core possono essere eseguite in .NET Core o in .NET Framework. È possibile sviluppare ed eseguire app ASP.NET Core multipiattaforma in Windows, Mac e Linux. ASP.NET Core è disponibile open source in [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>Che cos'è Visual Studio?

Visual Studio è una suite integrata per lo sviluppo di strumenti di produttività per gli sviluppatori. Si può immaginare Visual Studio come un programma utilizzabile per creare programmi e applicazioni.

## <a name="next-steps"></a>Passaggi successivi

L'esercitazione è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di C#, ASP.NET Core e dell'IDE di Visual Studio. Per altre informazioni sulla creazione di un'app Web o di un sito Web con C# e ASP.NET, continuare con l'esercitazione seguente:

> [!div class="nextstepaction"]
> [Creare un'app Web Razor Pages con ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)

In altre informazioni su come creare contenitori per l'app Web con Docker:

> [!div class="nextstepaction"]
> [Strumenti contenitore in Visual Studio](../../containers/overview.md)

## <a name="see-also"></a>Vedi anche

[Eseguire la pubblicazione di un'app Web in Servizio app di Azure con Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
