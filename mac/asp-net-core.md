---
title: Introduzione ad ASP.NET Core
description: In questo articolo viene descritto come iniziare a usare ASP.NET in Visual Studio per Mac, incluse le procedure di installazione e creazione di un nuovo progetto.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/06/2020
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: a2f45069967df412f9245f8044c53ef425a00fdf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710494"
---
# <a name="getting-started-with-aspnet-core"></a>Introduzione ad ASP.NET Core

 Visual Studio per Mac semplifica lo sviluppo del servizio dell'app con il supporto per la piattaforma di sviluppo Web ASP.NET Core più recente. Il funzionamento di ASP.NET Core si basa su .NET Core, l'evoluzione più recente di .NET Framework e del runtime. È stata ottimizzata per prestazioni veloci, fattorizzata per piccole dimensioni di installazione e rivisinata per l'esecuzione in Linux e macOS, nonché Windows.

## <a name="installing-net-core"></a>Installazione di .NET Core

.NET Core 3.1 viene installato automaticamente quando si installa Visual Studio per Mac. Per altre informazioni sulle versioni di .NET Core supportate in Visual Studio per Mac, vedere [Supporto di .NET Core.](./net-core-support.md)

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Creazione di un'app ASP.NET Core in Visual Studio per Mac

Aprire Visual Studio per Mac. Nella schermata iniziale selezionare **Nuovo progetto...**

![Finestra di dialogo Nuovo progetto](media/asp-net-core-2019-new-asp-core.png)

Verrà visualizzata la finestra di dialogo Nuovo progetto, che consente di selezionare un modello per la creazione dell'applicazione.

Alcuni progetti offrono un modello predefinito utilizzabile per iniziare a creare l'applicazione ASP.NET Core. Si tratta di:

- **.NET Core > Vuoto**
- **.NET Core > API**
- **.NET Core > Applicazione Web**
- **.NET Core > Applicazione Web (Model-View-Controller)**
- **.NET Core > Blazor Server App**
- **App > .NET Core Blazor WebAssembly**

![Opzioni di progetto ASP.NET](media/asp-net-core-2019-new-asp-core.png)

Selezionare **Progetto ASP.NET Core vuoto** e premere **Avanti**. Assegnare un nome al progetto e premere **Crea**. Verrà creata una nuova ASP.NET Core app. Nel riquadro sinistro della finestra della soluzione espandere la seconda freccia e quindi selezionare **Startup.cs.** Dovrebbe essere simile all'immagine seguente:

![Vista del nuovo progetto ASP.NET Core vuoto](media/asp-net-core-2019-empty-project.png)

Il ASP.NET Core vuoto crea un'applicazione Web con due file predefiniti: **Program.cs** e **Startup.cs,** illustrati di seguito. Crea anche una cartella Dependencies, che contiene le dipendenze del pacchetto NuGet del progetto, ad esempio ASP.NET Core, .NET Core Framework e le destinazioni MSBuild che compilano il progetto:

![Finestra della soluzione che visualizza le dipendenze](media/asp-net-core-2019-solution-dependencies.png)

### <a name="programcs"></a>Program.cs

Aprire ed esaminare il file **Program.cs** nel progetto. Si noti che nel metodo `Main`, il punto di inizio dell'app, avvengono diverse cose:

```csharp
    public class Program
    {
        public static void Main(string[] args)
        {
            CreateWebHostBuilder(args).Build().Run();
        }

        public static IWebHostBuilder CreateWebHostBuilder(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseStartup<Startup>();
    }
```

Un ASP.NET Core app crea un server Web nel metodo main configurando e avviando un host tramite un'istanza di [`WebHostBuilder`](/aspnet/core/fundamentals/hosting) . Questo generatore offre alcuni metodi che consentono la configurazione dell'host. Nell'app modello vengono usate le configurazioni seguenti:

* `.UseStartup<Startup>()`: specifica la classe di avvio.

Tuttavia, è anche possibile aggiungere altre configurazioni, ad esempio:

* `UseKestrel`: specifica il server Kestrel che verrà usato dall'app
* `UseContentRoot(Directory.GetCurrentDirectory())`: usa la cartella radice del progetto Web come radice del contenuto dell'app quando quest'ultima viene avviata da questa cartella
* `.UseIISIntegration()`: specifica che l'app deve funzionare con IIS. Per usare IIS con ASP.NET Core, è necessario specificare sia `UseKestrel` che `UseIISIntegration`.

### <a name="startupcs"></a>Startup.cs

La classe di avvio dell'app viene specificata nel metodo `UseStartup()` in `CreateWebHostBuilder`. È in questa classe che si specifica la pipeline di gestione delle richieste e si configurano eventuali servizi.

Aprire ed esaminare il file **Startup.cs** nel progetto:

```csharp
    public class Startup
    {
        // This method gets called by the runtime. Use this method to add services to the container.
        // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
        public void ConfigureServices(IServiceCollection services)
        {
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IHostingEnvironment env)
        {
            if (env.IsDevelopment())
            {
                app.UseDeveloperExceptionPage();
            }

            app.Run(async (context) =>
            {
                await context.Response.WriteAsync("Hello World!");
            });
        }
    }
```

La classe di avvio deve sempre rispettare le regole seguenti:

- Deve essere sempre pubblica
- Deve contenere i due metodi pubblici `ConfigureServices` e `Configure`

Il metodo `ConfigureServices` consente di definire i servizi che verranno usati dall'app.

Il metodo `Configure` consente di comporre pipeline delle richieste tramite [middleware](/aspnet/core/fundamentals/middleware). Si tratta di componenti usati all'interno delle pipeline delle applicazioni ASP.NET per la gestione delle richieste e delle risposte. La pipeline HTTP è costituita da un certo numero di delegati di richiesta, chiamati in sequenza. Ogni delegato può scegliere di gestire la richiesta o di passarla al delegato successivo.

È possibile configurare i delegati tramite i metodi `Run`,`Map` e `Use` in `IApplicationBuilder`. Il metodo `Run`, tuttavia, non chiama mai il delegato successivo e deve essere sempre usato alla fine della pipeline.

Il metodo `Configure` del modello predefinito è destinato all'esecuzione di alcune operazioni. Prima configura una pagina di gestione delle eccezioni da usare durante lo sviluppo. Quindi invia una risposta alla pagina Web di richiesta con la semplice frase "Hello World".

Questo semplice progetto "Hello World"può ora essere eseguito senza l'aggiunta di altro codice. Per eseguire l'app, è possibile selezionare il browser in cui eseguire l'app usando l'elenco a discesa a destra del pulsante Riproduci oppure fare semplicemente clic sul pulsante Riproduci (triangolare) per usare il browser predefinito:

![Esecuzione del browser](media/asp-net-web-picker.png)

Per avviare il progetto Web, Visual Studio per Mac usa una porta casuale. Per scoprire quale porta si tratta, aprire l'output dell'applicazione, elencato nel menu Visualizza > **altro Windows.** L'output dovrebbe essere simile a quello illustrato di seguito:

![Output applicazione con la porta di ascolto](media/asp-net-core-image6.png)

Quando il progetto è in esecuzione, il Web browser predefinito viene avviato e si collega all'URL elencato nell'output dell'applicazione. In alternativa, è possibile aprire un browser a scelta e immettere `http://localhost:5000/`, sostituendo `5000` con la porta presente nell'output di Visual Studio visualizzato nell'output dell'applicazione. Dovrebbe essere visualizzato il testo `Hello World!`:

![Browser con il testo](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Aggiunta di un controller

Le app ASP.NET Core usano lo schema progettuale Model-View-Controller (MVC) per stabilire una separazione logica delle responsabilità di ogni parte dell'app. Lo schema progettuale MVC è costituito dai concetti seguenti:

- **Model** (Modello): classe che rappresenta i dati dell'app.
- **View** (Vista): visualizza l'interfaccia utente dell'app. Spesso corrisponde ai dati del modello.
- **Controller**: classe che gestisce le richieste del browser e risponde all'input e all'interazione dell'utente.

Per altre informazioni sull'uso di MVC, vedere [panoramica di ASP.NET Core MVC.](/aspnet/core/mvc/overview)

Per aggiungere un controller, eseguire le operazioni seguenti:

1. Fare clic con il pulsante destro del mouse sul nome del progetto e selezionare **Aggiungi > Nuovo file**. Selezionare **Generale > Classe vuota** e quindi immettere un nome di controller:

    ![Finestra di dialogo Nuovo file](media/asp-net-core-image8.png)

2. Aggiungere al nuovo controller il codice seguente:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using System.Text.Encodings.Web;

    namespace Hello_ASP
    {
        public class HelloWorldController : Controller
        {
            //
            // GET: /HelloWorld/

            public string Index()
            {
                return "This is my default action...";
            }

        }
    }
    ```

3. Aggiungere la dipendenza `Microsoft.AspNetCore.Mvc` al progetto facendo clic con il pulsante destro del mouse sulla cartella **Dependency** (Dipendenza) e selezionando **Aggiungi pacchetto...**.

4. Usare la casella di ricerca per cercare `Microsoft.AspNetCore.Mvc` all'interno della libreria NuGet e selezionare **Aggiungi pacchetto**. L'installazione potrebbe richiedere alcuni minuti e potrebbe essere richiesto di accettare diverse licenze per le dipendenze necessarie:

    ![Aggiungi Nuget](media/asp-net-core-image9.png)

5. Nella classe di avvio rimuovere l'espressione lambda `app.Run` e impostare come illustrato di seguito la logica di routing degli URL usata da MVC per determinare il codice da chiamare:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Assicurarsi di rimuovere l'espressione lambda `app.Run`, poiché questa eseguirebbe l'override della logica di routing.

    Per determinare il codice da eseguire, MVC usa il formato seguente:

    `/[Controller]/[ActionName]/[Parameters]`

    Quando si aggiunge il frammento di codice precedente, si indica all'app di usare come impostazioni predefinite il controller `HelloWorld` e il metodo di azione `Index`.

6. Aggiungere la chiamata a `services.AddMvc();` al metodo `ConfigureServices`, come illustrato di seguito:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    È anche possibile passare le informazioni per i parametri dall'URL al controller.

7. Aggiungere un altro metodo a HelloWorldController, come illustrato di seguito:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Se ora si esegue l'app, il browser dovrebbe aprirsi automaticamente:

    ![Esecuzione dell'app nel browser](media/asp-net-core-image13.png)

9. Tentare di passare a `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` (sostituire `xxxx` con la porta corretta). Dovrebbe essere visualizzato quanto segue:

    ![Esecuzione dell'app nel browser con argomenti](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se è necessario installare manualmente .NET Core in macOS 10.12 (Sierra) e versioni successive, eseguire le operazioni seguenti:

1. Prima di iniziare l'installazione di .NET Core, assicurarsi che siano stati eseguiti tutti gli aggiornamenti del sistema operativo fino alla versione stabile più recente. Per eseguire questa verifica, passare all'applicazione App Store e selezionare la scheda Aggiornamenti.

2. Seguire i passaggi elencati nel [sito .NET Core](https://www.microsoft.com/net/core#macos).

Per installare correttamente .NET Core, assicurarsi che tutti i passaggi vengano completati in modo appropriato.

## <a name="summary"></a>Riepilogo

Questa guida offre un'introduzione ad ASP.NET Core. Descrive che cos'è e quando usarlo e fornisce informazioni per l'uso in Visual Studio per Mac.
Per altre informazioni sui passaggi successivi da qui, vedere le guide seguenti:
- [ASP.NET Core](/aspnet/core/) docs.
- [Creating Backend Services for Native Mobile Applications](/aspnet/core/mobile/native-mobile-backend) (Creazione di servizi back-end per applicazioni per dispositivi mobili native), che illustra come creare un servizio REST tramite ASP.NET Core per un'app Xamarin.Forms.
- [ASP.NET Core hands-on lab](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started) (Esercitazione pratica su ASP.NET Core).

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]