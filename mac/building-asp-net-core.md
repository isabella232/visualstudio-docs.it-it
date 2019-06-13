---
title: Compilazione di applicazioni in Visual Studio per Mac ASP.NET Core
description: In questo articolo viene descritto come iniziare a usare ASP.NET in Visual Studio per Mac, incluse le procedure di installazione e creazione di un nuovo progetto.
author: asb3993
ms.author: amburns
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: fb70966dd24c4d22d473b552297a60ddebdce106
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836180"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Compilazione di applicazioni in Visual Studio per Mac ASP.NET Core 


ASP.NET Core è un framework open source e multipiattaforma per la compilazione di moderni basati sul cloud connesso a internet applicazioni, ad esempio App web e servizi, App IoT e back-end per dispositivi mobili. App ASP.NET Core possono essere eseguite [.NET Core](https://www.microsoft.com/net/core/platform) o i runtime di .NET Framework. È stato progettato per offrire un framework di sviluppo ottimizzato per le app distribuite nel cloud o eseguito in locale. È costituito da componenti modulari con un overhead minimo, in modo da mantenere flessibilità durante la creazione di soluzioni. È possibile sviluppare ed eseguire app ASP.NET Core multipiattaforma in Windows, Mac e Linux. ASP.NET Core è disponibile open source in [GitHub](https://github.com/aspnet/home).

In questo laboratorio, verrà creato ed esplorare un'applicazione ASP.NET Core con Visual Studio per Mac.

## <a name="objectives"></a>Obiettivi


> [!div class="checklist"]
> * Creare un'app Web ASP.NET Core
> * Esplorazione di ASP.NET Core che ospita, configurazione e il modello di middleware
> * Eseguire il debug di un'app web ASP.NET Core

## <a name="prerequisites"></a>Prerequisiti

- [Visual Studio per Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Destinatari

Questa esercitazione è destinata agli sviluppatori che hanno familiari con C#, anche se non è necessaria una vasta esperienza.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Attività 1: Crea una nuova applicazione ASP.NET Core

1. Avviare **Visual Studio per Mac**.

2. Selezionare **File > Nuova soluzione**.

3. Selezionare il **.NET Core > App** categoria e il **App Web ASP.NET Core (C#)** modello. Scegliere **Avanti**.

    ![](media/netcore-image1.png)

4. Immettere il nome **"CoreLab"** e fare clic su **crea** per creare il progetto. È necessario dedicare un momento per completare.

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Attività 2: Touring la soluzione

1. Il modello predefinito produce una soluzione con un unico progetto ASP.NET Core denominato **CoreLab**. Espandere il nodo del progetto per esporne il contenuto.

    ![](media/netcore-image3.png)

2. Questo progetto segue il paradigma di model-view-controller (MVC) per fornire una divisione chiara delle responsabilità tra i dati (modelli), presentazione (viste) e le funzionalità (controller). Aprire il file **HomeController.cs** dalla cartella **Controller**.

    ![](media/netcore-image4.png)

3. Il **HomeController** classe by convenzione-gestisce tutte le richieste in ingresso che iniziano con **/Home**. Il **indice** metodo gestisce le richieste per la radice della directory (ad esempio http://site.com/Home) e altri metodi gestiscono le richieste per il percorso denominato basato su convenzione, ad esempio **About ()** gestisce le richieste per **http://site.com/Home/About** . Naturalmente, questo è tutto configurabile. Un importante dei quali è che il **HomeController** è il controller predefinito in un nuovo progetto, pertanto, le richieste alla radice del sito ( **http://site.com** ) passiamo alla **Index ()** del **HomeController** esattamente come le richieste al **http://site.com/Home** oppure **http://site.com/Home/Index** .

    ![](media/netcore-image5.png)

4. Ha anche un **viste** cartella che contiene altre cartelle mappate a ogni controller (oltre a una per **condiviso** viste. Ad esempio, il file CSHTML (estensione del linguaggio HTML) di visualizzazione per il percorso **/Home/About** si troverebbe in **Visualizzazioni/Home/About.cshtml**. Aprire il file.

    ![](media/netcore-image6.png)

5. Questo file CSHTML usa la sintassi Razor per eseguire il rendering HTML in base a una combinazione di tag standard e C# inline. Sono disponibili ulteriori informazioni, vedere la [documentazione online](https://docs.microsoft.com/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![](media/netcore-image7.png)

6. La soluzione contiene anche un **wwwroot** cartella che sarà la radice del sito web. È possibile inserire contenuto statico del sito, ad esempio fogli di stile CSS, immagini e librerie JavaScript, direttamente nei percorsi ad essi destinati al momento della distribuzione del sito stesso.

    ![](media/netcore-image8.png)

7. Sono presenti anche diversi file di configurazione che consentono di gestire il progetto, i pacchetti di questo e l'applicazione in fase di runtime. La [configurazione](https://docs.microsoft.com/aspnet/core/fundamentals/configuration) predefinita dell'applicazione, ad esempio, è archiviata in **appsettings.json**. È tuttavia possibile ignorare alcune di queste impostazioni, oppure ignorarle tutte, a seconda dell'ambiente, ad esempio tramite un file **appsettings.Development.json** per l'ambiente **Development**.

    ![](media/netcore-image9.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Attività 3: Informazioni sulle modalità in cui è ospitata l'applicazione

1. Dal **Esplora soluzioni**aprire **Program.cs**. Questo è il programma di bootstrap che eseguirà l'applicazione.

    ![](media/netcore-image10.png)

2. Anche se sono presenti solo due righe di codice in questo caso, risultano sostanziale. È possibile suddividere le attività. Per prima cosa, un nuovo **WebHostBuilder** viene creato. Le app ASP.NET Core richiedono un host in cui si desidera eseguire. Un host deve implementare il **IWebHost** interfaccia, che espone gli insiemi di funzionalità e servizi, e una **avviare** (metodo). L'host viene generalmente creato usando un'istanza di un **WebHostBuilder**, che crea e restituisce un **WebHost** istanza. Il **WebHost** faccia riferimento al server che gestirà le richieste.

    ![](media/netcore-image11.png)

3. Mentre il **WebHostBuilder** ha la responsabilità per la creazione dell'host che sarà eseguire il bootstrap del server per l'app, richiede di specificare un server che implementa **IServer**. Per impostazione predefinita, si tratta  **[Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)** , un server web multipiattaforma per ASP.NET Core basato sul **libuv**, che è una libreria dei / o asincrona multipiattaforma.

    ![](media/netcore-image12.png)

4. Successivamente, viene impostato radice del contenuto del server. Questa impostazione determina in cui cercare file di contenuto, ad esempio file di visualizzazione MVC. La radice del contenuto predefinito è la cartella da cui viene eseguita l'applicazione.

    ![](media/netcore-image13.png)

5. Se l'app è necessario collaborare con il server web Internet Information Services (IIS), il **UseIISIntegration** metodo deve essere chiamato come parte della compilazione dell'host. Che questo non configura un server, ad esempio **UseKestrel** viene. Per usare IIS con ASP.NET Core, è necessario specificare entrambe **UseKestrel** e **UseIISIntegration**. **Kestrel** è progettato per essere eseguito dietro un proxy e non devono essere distribuiti direttamente connessi a internet. **UseIISIntegration** specifica IIS come server proxy inverso, ma è rilevante solo quando viene eseguito su macchine che dispongono di IIS. Se si distribuisce l'applicazione per Windows, è necessario lasciarla nel. Non ridurre in caso contrario.

    ![](media/netcore-image14.png)

6. È una procedura più lineare per separare il caricamento delle impostazioni dall'avvio dell'applicazione. A tale scopo semplice, **UseStartup** viene chiamato per specificare che le **avvio** classe deve essere chiamato per il caricamento delle impostazioni e altre attività di avvio, ad esempio l'inserimento di middleware nella pipeline HTTP. Si possono disporre di più **UseStartup** chiamate con l'aspettativa che ognuno di essi sovrascrive le impostazioni precedenti in base alle esigenze.

    ![](media/netcore-image15.png)

7. L'ultimo passaggio nella creazione di **IWebHost** consiste nel chiamare **compilazione**.

    ![](media/netcore-image16.png)

8. Anche se **IWebHost** classi necessarie per implementare il non bloccante **avviare**, i progetti ASP.NET Core dispongono di un metodo di estensione denominato **eseguire** che esegue il wrapping  **Avviare** con il blocco di codice in modo che non è necessario per impedire che il metodo venga chiuso immediatamente.

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Attività 4: In esecuzione e debug dell'applicazione

1. Nella **Esplora soluzioni**, fare doppio clic il **CoreLab** nodo del progetto e selezionare **opzioni**.

    ![](media/netcore-image18.png)

2. Il **opzioni progetto** finestra di dialogo include tutto ciò che occorre per regolare la modalità compilata, per eseguire l'applicazione. Selezionare il **Esegui > configurazioni > predefinito** nodo dal Pannello di sinistra.

3. Controllare **Esegui in console esterna** e deselezionare **Sospendi output della console**. In genere l'applicazione self-hosted non avrebbe relativa console visibile, ma sarebbe invece accedere i risultati con il **Output** riempimento. Ai fini di questa esercitazione, si vedrà, in una finestra separata, anche se non è necessario eseguire questa operazione durante lo sviluppo normale.

4. Fare clic su **OK**.

    ![](media/netcore-image19.png)

5. Premere **F5** per compilare ed eseguire l'applicazione. In alternativa, è possibile selezionare **Esegui > Avvia debug**.

6. Visual Studio per Mac avvierà due finestre. Il primo è una finestra della console che offre una visualizzazione all'applicazione server self-hosted.

    ![](media/netcore-image20.png)

7. La seconda è una normale finestra del browser per testare il sito. Per quanto riguarda il browser sa, l'applicazione potrebbe essere ospitata ovunque. Fare clic su **sulle** per passare alla pagina.

    ![](media/netcore-image21.png)

8. Tra le altre cose, le informazioni sulla pagina esegue il rendering del testo impostato nel controller.

    ![](media/netcore-image22.png)

9. Consente di mantenere entrambe le finestre di aprono e tornare a Visual Studio per Mac. Aprire il file **Controller/HomeController.cs** se non è già aperto.

    ![](media/netcore-image23.png)

10. Impostare un punto di interruzione nella prima riga del metodo **About**. È possibile farlo facendo clic sul margine o impostando il cursore sulla riga e premendo **F9**. Questa riga imposta alcuni dati nella raccolta **ViewData** di cui viene eseguito il rendering della pagina CSHTML in **Visualizzazioni/Home/About.cshtml**.

    ![](media/netcore-image24.png)

11. Tornare al browser e aggiornare le informazioni sulla pagina. Verrà attivato il punto di interruzione in Visual Studio per Mac.

12. Sposta il mouse sopra il **ViewData** membro per visualizzarne i dati. È anche possibile espandere i relativi membri figlio per visualizzare i dati nidificati.

    ![](media/netcore-image25.png)

13. Rimuovere il punto di interruzione dell'applicazione con lo stesso metodo usato per aggiungerlo.

14. Aprire **Visualizzazioni/Home/About.cshtml**.

15. Modificare il testo **"additional"** in **"changed"** e salvare il file.

    ![](media/netcore-image26.png)

16. Premere il **continuazione** pulsante per continuare l'esecuzione.

    ![](media/netcore-image27.png)

17. Tornare alla finestra del browser per visualizzare il testo aggiornato. Questa modifica può essere eseguita in qualsiasi momento e non necessariamente richiede un punto di interruzione. Se non viene visualizzata la modifica riflessa immediatamente, aggiornare il browser.

    ![](media/netcore-image28.png)

18. Chiudere la finestra e l'applicazione console del browser dei test. Anche il debug verrà interrotta.

## <a name="task-5-application-startup-configuration"></a>Attività 5: Configurazione di avvio dell'applicazione

1. Dal **Esplora soluzioni**aprire **Startup.cs**. È possibile notare alcune righe rosse a zigzag inizialmente come pacchetti NuGet vengono ripristinati in background e il compilatore Roslyn sta realizzando un quadro completo delle dipendenze del progetto.

    ![](media/netcore-image29.png)

2. Individuare il **avvio** (metodo). In questa sezione definisce la configurazione iniziale per l'applicazione e viene densamente. Vediamo in dettaglio.

    ![](media/netcore-image30.png)

3. Il metodo inizia con l'inizializzazione di una **ConfigurationBuilder** e impostando il percorso di base.

    ![](media/netcore-image31.png)

4. Successivamente, viene caricato un necessaria **appSettings. JSON** file.

    ![](media/netcore-image32.png)

5. Successivamente, tenta di caricare un specifici dell'ambiente **appSettings. JSON** file, che eseguirà l'override delle impostazioni esistenti. Ad esempio, questo è un oggetto fornito **appsettings. Development.JSON** file utilizzato per quell'ambiente specifico. Per altre informazioni sulla configurazione in ASP.NET Core, consultare [documentazione](https://docs.microsoft.com/aspnet/core/fundamentals/configuration).

    ![](media/netcore-image34.png)

6. Infine, le variabili di ambiente vengono aggiunti al generatore di configurazione e la configurazione viene compilata e impostata per l'utilizzo.

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Attività 6: Inserimento dell'applicazione middleware

1. Individuare il **Configure** metodo nella **avvio** classe. Si tratta in cui tutto il middleware viene configurato in modo che possa essere inserito nella pipeline HTTP e usata per elaborare ogni richiesta al server. Sebbene questo metodo viene chiamato una sola volta, il contenuto dei metodi (ad esempio **UseStaticFiles**) può essere eseguita su tutte le richieste.

    ![](media/netcore-image36.png)

2. È anche possibile aggiungere altro middleware per essere eseguito come parte della pipeline. Aggiungere il codice seguente dopo **app. UseStaticFiles** per aggiungere automaticamente un **X-Test** intestazione a ogni risposta in uscita. IntelliSense consente di completare il codice durante la digitazione.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Premere **F5** per compilare ed eseguire il progetto.

4. È possibile usare il browser per esaminare le intestazioni per verificare che vengano aggiunte. Le istruzioni riportate di seguito sono per Safari, ma è possibile eseguire la stessa [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) oppure [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console).

5. Una volta che il browser ha caricato il sito, selezionare **Safari > Preferenze**.

6. Nel **avanzate** scheda, check **Show Develop menu nella barra dei menu** e chiudere la finestra di dialogo.

    ![](media/netcore-image37.png)

7. Selezionare **sviluppare > Mostra le risorse Page**.

8. Aggiornare la finestra del browser in modo che gli strumenti di sviluppo appena aperta possono monitorare e analizzare il traffico e il contenuto.

9. La pagina HTML localhost eseguita dal server sarà l'elemento selezionato per impostazione predefinita.

    ![](media/netcore-image38.png)

10. Espandere la **nella barra laterale informazioni dettagliate**.

    ![](media/netcore-image39.png)

11. Scorrere fino alla parte inferiore della barra laterale per visualizzare l'intestazione della risposta aggiunto in precedenza nel codice.

    ![](media/netcore-image40.png)

12. Chiudere la finestra del browser e console quando non soddisfatto.

## <a name="summary"></a>Riepilogo

In questo laboratorio, si è appreso come iniziare a sviluppare App ASP.NET Core con Visual Studio per Mac. Se si vuole esplorare lo sviluppo di un'applicazione di database di film più completa, vedere la [Introduzione a ASP.NET Core MVC](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/start-mvc) esercitazione.
