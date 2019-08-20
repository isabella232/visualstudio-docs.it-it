---
title: Creazione di applicazioni ASP.NET Core
description: In questo articolo viene descritto come iniziare a usare ASP.NET in Visual Studio per Mac, incluse le procedure di installazione e creazione di un nuovo progetto.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: 345111144e0e209d91d34e53fefcd7d1207d9a8a
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872561"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Creazione di applicazioni ASP.NET Core in Visual Studio per Mac

ASP.NET Core è un framework open source multipiattaforma per la creazione di applicazioni moderne, basate sul cloud e connesse a Internet, ad esempio app e servizi Web, app IoT e back-end per dispositivi mobili. Le app ASP.NET Core possono essere eseguite in [.NET Core](https://www.microsoft.com/net/core/platform) o nei runtime di .NET Framework. È stato progettato per offrire un framework di sviluppo ottimizzato per le app distribuite nel cloud o eseguite in locale. È costituito da componenti modulari con un overhead minimo, in modo da mantenere flessibilità durante la creazione di soluzioni. È possibile sviluppare ed eseguire app ASP.NET Core multipiattaforma in Windows, Mac e Linux. ASP.NET Core è disponibile open source in [GitHub](https://github.com/aspnet/home).

In questo lab si creerà ed esplorerà un'applicazione ASP.NET Core con Visual Studio per Mac.

## <a name="objectives"></a>Obiettivi

> [!div class="checklist"]
> * Creare un'app Web ASP.NET Core
> * Esplorare il modello di hosting, configurazione e middleware di ASP.NET Core
> * Eseguire il debug di un'app Web ASP.NET Core

## <a name="prerequisites"></a>Prerequisiti

- [Visual Studio per Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Destinatari del documento

Questo lab è destinato agli sviluppatori che hanno familiarità con C#, anche se non è necessaria una vasta esperienza.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Attività 1: Creazione di una nuova applicazione ASP.NET Core

1. Avviare **Visual Studio per Mac**.

2. Selezionare **File > Nuova soluzione**.

3. Selezionare la categoria **.NET Core > App** e il modello **App Web ASP.NET Core (C#)** . Scegliere **Avanti**.

    ![](media/netcore-image1.png)

4. Immettere **"CoreLab"** come nome e fare clic su **Crea** per creare il progetto. Il completamento dell'operazione potrebbe richiedere qualche istante.

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Attività 2: Esplorazione della soluzione

1. Il modello predefinito genera una soluzione con un unico progetto ASP.NET Core denominato **CoreLab**. Espandere il nodo del progetto per esporne il contenuto.

    ![](media/netcore-image3.png)

2. Questo progetto segue il paradigma MVC (Model-View-Controller) per una precisa ripartizione dei compiti tra i dati (modelli), la presentazione (viste) e le funzionalità (controller). Aprire il file **HomeController.cs** dalla cartella **Controller**.

    ![](media/netcore-image4.png)

3. La convenzione di classificazione **HomeController** gestisce tutte le richieste in ingresso che iniziano con **/Home**. Il metodo **Index** gestisce le richieste alla radice della directory, come `http://site.com/Home`, e altri metodi gestiscono le richieste al percorso denominato in base alla convenzione. Ad esempio, **About ()** gestisce le richieste a `http://site.com/Home/About`. Naturalmente, tutto questo è configurabile. Un concetto importante da tenere presente è dato dal fatto che in un nuovo progetto **HomeController** è il controller predefinito e pertanto le richieste inviate alla radice del sito (`http://site.com`) passano attraverso il metodo **Index()** di **HomeController**, proprio come le richieste a `http://site.com/Home` o `http://site.com/Home/Index`.

    ![](media/netcore-image5.png)

4. Il progetto ha anche una cartella **Visualizzazioni** in cui sono incluse altre cartelle mappate a ogni controller, oltre a una cartella per le visualizzazioni **condivise**. Ad esempio, il file CSHTML (estensione del linguaggio HTML) di visualizzazione per il percorso **/Home/About** si troverebbe in **Visualizzazioni/Home/About.cshtml**. Aprire il file.

    ![](media/netcore-image6.png)

5. Questo file CSHTML usa la sintassi Razor per eseguire il rendering HTML in base a una combinazione di tag standard e C# inline. Per altre informazioni su questo modello, vedere la [documentazione online](https://docs.microsoft.com/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![](media/netcore-image7.png)

6. La soluzione contiene anche una cartella **wwwroot** che sarà la radice per il sito Web. È possibile inserire contenuto statico del sito, ad esempio fogli di stile CSS, immagini e librerie JavaScript, direttamente nei percorsi ad essi destinati al momento della distribuzione del sito stesso.

    ![](media/netcore-image8.png)

7. Sono presenti anche diversi file di configurazione che consentono di gestire il progetto, i pacchetti di questo e l'applicazione in fase di runtime. La [configurazione](https://docs.microsoft.com/aspnet/core/fundamentals/configuration) predefinita dell'applicazione, ad esempio, è archiviata in **appsettings.json**. È tuttavia possibile ignorare alcune di queste impostazioni, oppure ignorarle tutte, a seconda dell'ambiente, ad esempio tramite un file **appsettings.Development.json** per l'ambiente **Development**.

    ![](media/netcore-image9.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Attività 3: Comprensione della modalità di hosting dell'applicazione

1. In **Esplora soluzioni** aprire **Program.cs**. Questo è il programma di bootstrap che eseguirà l'applicazione.

    ![](media/netcore-image10.png)

2. Anche se sono presenti solo due righe di codice, la loro importanza è fondamentale. Si esamineranno ora in dettaglio queste righe. Prima di tutto, viene creato un nuovo **WebHostBuilder**. Le app ASP.NET Core richiedono un host per l'esecuzione. L'host deve implementare l'interfaccia **IWebHost**, che espone raccolte di funzionalità e servizi, e un metodo **Start**. L'host viene in genere creato tramite un'istanza di **WebHostBuilder**, che crea e restituisce un'istanza di **WebHost**. L'istanza di **WebHost** fa riferimento al server che gestirà le richieste.

    ![](media/netcore-image11.png)

3. **WebHostBuilder** ha il compito di creare l'host che eseguirà il bootstrap del server per l'app e al tempo stesso richiede di specificare un server per l'implementazione di **IServer**. Per impostazione predefinita viene usato **[Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)** , un server Web multipiattaforma per ASP.NET Core basato su **libuv**, una libreria di I/O asincrona multipiattaforma.

    ![](media/netcore-image12.png)

4. A questo punto viene impostata la radice del contenuto del server. Questa impostazione determina il percorso in cui cercare i file di contenuto, ad esempio i file di visualizzazione MVC. La radice predefinita del contenuto è costituita dalla cartella da cui viene eseguita l'applicazione.

    ![](media/netcore-image13.png)

5. Se l'app deve interagire con il server Web IIS (Internet Information Services), come parte del codice per la compilazione dell'host deve essere chiamato il metodo **UseIISIntegration**. A differenza di **UseKestrel**, questo metodo non configura un server. Per usare IIS con ASP.NET Core, è necessario specificare sia **UseKestrel** che **UseIISIntegration**. **Kestrel** è stato progettato per essere eseguito dietro un proxy e non deve essere distribuito con accesso diretto a Internet. **UseIISIntegration** specifica IIS come server proxy inverso, ma è rilevante solo quando viene eseguito su computer in cui è installato IIS. Se si distribuisce l'applicazione in Windows, lasciarlo lì. Negli altri casi non crea comunque problemi.

    ![](media/netcore-image14.png)

6. Per una procedura più lineare, è consigliabile separare il caricamento delle impostazioni dal bootstrap dell'applicazione. Per ottenere facilmente questo risultato, viene chiamato **UseStartup** per specificare che è necessario chiamare la classe **Startup** per il caricamento delle impostazioni e altre attività di avvio, come l'inserimento di middleware nella pipeline HTTP. È possibile eseguire più chiamate a **UseStartup** con la previsione che ciascuna sovrascriva le impostazioni precedenti come necessario.

    ![](media/netcore-image15.png)

7. L'ultimo passaggio per la creazione di **IWebHost** consiste nell'esecuzione di una chiamata a **Build**.

    ![](media/netcore-image16.png)

8. Anche se le classi **IWebHost** sono necessarie per implementare il metodo **Start** non bloccante, i progetti ASP.NET Core dispongono di un metodo di estensione denominato **Run** che esegue il wrapping di **Start** con codice bloccante, evitando così di dover impedire manualmente la chiusura immediata del metodo.

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Attività 4: Esecuzione e debug dell'applicazione

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto **CoreLab** e scegliere **Opzioni**.

    ![](media/netcore-image18.png)

2. La finestra di dialogo **Opzioni progetto** include tutto il necessario per regolare la modalità di compilazione ed esecuzione dell'applicazione. Selezionare il nodo **Esegui > Configurazioni > Predefinite** nel pannello di sinistra.

3. Selezionare **Esegui in console esterna** e deselezionare **Sospendi output della console**. La console non è in genere visibile nell'applicazione self-hosted, ma in alternativa i risultati dell'applicazione vengono registrati nel riquadro **Output**. Ai fini di questo lab, la console verrà visualizzata in una finestra separata, anche se questo non è necessario durante le normali attività di sviluppo.

4. Fare clic su **OK**.

    ![](media/netcore-image19.png)

5. Premere **F5** per compilare ed eseguire l'applicazione. In alternativa, è possibile selezionare **Esegui > Avvia debug**.

6. Visual Studio per Mac avvierà due finestre. La prima è una finestra di console in cui è visualizzato il contenuto dell'applicazione server self-hosted.

    ![](media/netcore-image20.png)

7. La seconda è una normale finestra del browser per testare il sito. Dal punto di vista del browser, l'applicazione potrebbe essere ospitata ovunque. Fare clic su **About** (Informazioni) per passare a tale pagina.

    ![](media/netcore-image21.png)

8. Tra le altre cose, la pagina delle informazioni visualizza il testo impostato nel controller.

    ![](media/netcore-image22.png)

9. Tenere aperte entrambe le finestre e tornare a Visual Studio per Mac. Aprire il file **Controller/HomeController.cs** se non è già aperto.

    ![](media/netcore-image23.png)

10. Impostare un punto di interruzione nella prima riga del metodo **About**. Per eseguire questa operazione, fare clic sul margine o posizionare il cursore sulla riga e premere **F9**. Questa riga imposta alcuni dati nella raccolta **ViewData** di cui viene eseguito il rendering della pagina CSHTML in **Visualizzazioni/Home/About.cshtml**.

    ![](media/netcore-image24.png)

11. Tornare al browser e aggiornare la pagina delle informazioni. Questa operazione attiverà il punto di interruzione in Visual Studio per Mac.

12. Passare il puntatore del mouse sopra il membro **ViewData** per visualizzarne i dati. È anche possibile espandere i relativi membri figlio per visualizzare i dati annidati.

    ![](media/netcore-image25.png)

13. Rimuovere il punto di interruzione dell'applicazione con lo stesso metodo usato per aggiungerlo.

14. Aprire **Visualizzazioni/Home/About.cshtml**.

15. Modificare il testo **"additional"** in **"changed"** e salvare il file.

    ![](media/netcore-image26.png)

16. Fare clic sul pulsante **Continua** per continuare l'esecuzione.

    ![](media/netcore-image27.png)

17. Tornare alla finestra del browser per visualizzare il testo aggiornato. Questa modifica può essere eseguita in qualsiasi momento e non richiede necessariamente un punto di interruzione del debugger. Se la modifica non viene visualizzata immediatamente, aggiornare il browser.

    ![](media/netcore-image28.png)

18. Chiudere la console dell'applicazione e la finestra del browser di test. In questo modo verrà arrestato anche il processo di debug.

## <a name="task-5-application-startup-configuration"></a>Attività 5: Configurazione dell'avvio dell'applicazione

1. In **Esplora soluzioni** aprire **Startup.cs**. È possibile notare inizialmente alcune righe rosse a zigzag mentre i pacchetti NuGet vengono ripristinati in background e il compilatore Roslyn genera un quadro completo delle dipendenze del progetto.

    ![](media/netcore-image29.png)

2. Individuare il metodo **Startup**. Questa sezione definisce la configurazione iniziale per l'applicazione ed è densa di informazioni. Si esamineranno ora in dettaglio i dati della configurazione.

    ![](media/netcore-image30.png)

3. Il metodo inizia con l'inizializzazione di un oggetto **ConfigurationBuilder** e l'impostazione del relativo percorso di base.

    ![](media/netcore-image31.png)

4. Prosegue quindi con il caricamento di un file **appsettings.json** obbligatorio.

    ![](media/netcore-image32.png)

5. Dopo questa operazione, prova a caricare un file **appsettings.json** specifico dell'ambiente, che eseguirà l'override delle impostazioni esistenti. Questo è ad esempio un file **appsettings.Development.json** predefinito che viene usato per l'ambiente specifico. Per altre informazioni sulla configurazione in ASP.NET Core, consultare la [documentazione](https://docs.microsoft.com/aspnet/core/fundamentals/configuration).

    ![](media/netcore-image34.png)

6. Vengono infine aggiunte le variabili di ambiente al generatore della configurazione e la configurazione viene creata e impostata per l'uso.

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Attività 6: Inserimento del middleware dell'applicazione

1. Individuare il metodo **Configure** nella classe **Startup**. In questa classe viene configurato tutto il middleware in modo che possa essere inserito nella pipeline HTTP e usato per elaborare ogni richiesta inviata al server. Anche se questo metodo viene chiamato una sola volta, il contenuto dei metodi, ad esempio **UseStaticFiles**, può essere eseguito per ogni richiesta.

    ![](media/netcore-image36.png)

2. È anche possibile aggiungere altro middleware da eseguire come parte della pipeline. Aggiungere il codice seguente dopo **app.UseStaticFiles** per aggiungere automaticamente un'intestazione **X-Test** a ogni risposta in uscita. IntelliSense aiuterà a completare il codice durante la digitazione.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Premere **F5** per compilare ed eseguire il progetto.

4. Per verificare che siano state aggiunte le intestazioni è possibile usare il browser. Nelle istruzioni riportate di seguito è previsto l'uso di Safari, ma è possibile eseguire la stessa procedura in [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) o [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console).

5. Dopo che il browser ha caricato il sito, selezionare **Safari > Preferenze**.

6. Nella scheda **Avanzate** selezionare **Mostra menu Sviluppo nella barra dei menu** e chiudere la finestra di dialogo.

    ![](media/netcore-image37.png)

7. Selezionare **Sviluppo > Mostra risorse pagina**.

8. Aggiornare la finestra del browser in modo che gli strumenti di sviluppo appena aperti possano monitorare e analizzare il traffico e il contenuto.

9. La pagina HTML localhost eseguita dal server sarà l'elemento selezionato per impostazione predefinita.

    ![](media/netcore-image38.png)

10. Espandere la **barra laterale dei dettagli**.

    ![](media/netcore-image39.png)

11. Scorrere fino alla parte inferiore della barra laterale per visualizzare l'intestazione della risposta aggiunta in precedenza nel codice.

    ![](media/netcore-image40.png)

12. Dopo aver letto le informazioni desiderate, chiudere la finestra del browser e la console.

## <a name="summary"></a>Riepilogo

In questo lab si è appreso come iniziare a sviluppare app ASP.NET Core con Visual Studio per Mac. Se si vogliono approfondire le conoscenze sullo sviluppo di un'applicazione di database di film più completa, vedere l'esercitazione [Introduzione ad ASP.NET Core MVC](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/start-mvc).
