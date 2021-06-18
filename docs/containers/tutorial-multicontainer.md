---
title: Usare più contenitori usando Docker Compose
author: ghogen
description: Informazioni su come usare più contenitori con Docker Compose
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 03/15/2021
ms.technology: vs-azure
ms.topic: tutorial
ms.openlocfilehash: 78af96eaa8f340129b2b445dd92419f84cf91ab1
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307817"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Esercitazione: Creare un'app a più contenitori con Docker Compose

In questa esercitazione si apprenderà come gestire più contenitori e comunicare tra di essi quando si usano gli strumenti contenitore in Visual Studio.  La gestione di più contenitori richiede *l'orchestrazione* dei contenitori e un agente di orchestrazione, ad esempio Docker Compose, Kubernetes o Service Fabric. In questo caso si userà Docker Compose. Docker Compose è ideale per il debug e i test locali nel corso del ciclo di sviluppo.

## <a name="prerequisites"></a>Prerequisiti

::: moniker range="vs-2017"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017 con il carico](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) di lavoro Sviluppo **Web,** Strumenti di **Azure** o **Sviluppo multipiattaforma .NET Core** installato
::: moniker-end

::: moniker range="vs-2019"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* [Strumenti di sviluppo per .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) per lo sviluppo con .NET Core 2.2
* [Strumenti di sviluppo .NET Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.1) per lo sviluppo con .NET Core 3.1.
::: moniker-end

::: moniker range=">=vs-2022"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) con il carico di lavoro Sviluppo **Web,** Strumenti di **Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* [Strumenti di sviluppo .NET Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.1) per lo sviluppo con .NET Core 3.1.
* [.NET 5 Development Toos](https://dotnet.microsoft.com/download/dotnet-core/5.0) for development with .NET 5 (Toos per lo sviluppo con .NET 5).
::: moniker-end

## <a name="create-a-web-application-project"></a>Creare un progetto di applicazione Web

In Visual Studio creare un **progetto di app Web ASP.NET Core,** denominato , per creare `WebFrontEnd` un'applicazione Web con pagine Razor.
  
::: moniker range="vs-2017"

Non selezionare **Abilita supporto Docker**. Il supporto di Docker verrà aggiunto in un secondo momento.

![Screenshot della creazione del progetto Web](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Creare ASP.NET di app Web Core](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

Non selezionare **Abilita supporto Docker**. Il supporto di Docker verrà aggiunto in un secondo momento.

![Screenshot della schermata Informazioni aggiuntive durante la creazione di un progetto Web. L'opzione Abilita supporto Docker non è selezionata.](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Creare un progetto API Web

Aggiungere un progetto alla stessa soluzione e chiamarlo *MyWebAPI.* Selezionare **API** come tipo di progetto e deselezionare la casella di controllo **Configura per HTTPS.** In questa progettazione viene utilizzato solo SSL per la comunicazione con il client, non per la comunicazione tra contenitori nella stessa applicazione Web. È necessario solo HTTPS e il codice negli esempi presuppone che la casella di controllo `WebFrontEnd` sia stata deselezionata. In generale, i certificati per sviluppatori .NET usati da Visual Studio sono supportati solo per le richieste da esterno a contenitore, non per le richieste da contenitore a contenitore.

::: moniker range="vs-2017"
   ![Screenshot della creazione del progetto API Web](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Screenshot della creazione del progetto API Web](./media/tutorial-multicontainer/vs-2019/create-webapi-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Aggiungere il codice per chiamare l'API Web

1. Nel progetto `WebFrontEnd` aprire il file *Index.cshtml.cs* e sostituire il `OnGet` metodo con il codice seguente.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          // request.RequestUri = new Uri("http://mywebapi/WeatherForecast"); // ASP.NET 3 (VS 2019 only)
          request.RequestUri = new Uri("http://mywebapi/api/values/1"); // ASP.NET 2.x
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > Nel codice reale non è consigliabile eliminare dopo `HttpClient` ogni richiesta. Per le procedure consigliate, vedere [Usare HttpClientFactory per implementare richieste HTTP resilienti.](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests)

   Per .NET Core 3.1 in Visual Studio 2019 o versioni successive, il modello api Web usa un'API WeatherForecast, quindi rimuovere il commento da tale riga e impostare come commento la riga per ASP.NET 2.x.

1. Nel file *index.cshtml* aggiungere una riga per visualizzare `ViewData["Message"]` in modo che il file abbia un aspetto simile al codice seguente:
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. (ASP.NET solo 2.x) Nel progetto API Web aggiungere ora il codice al controller Values per personalizzare il messaggio restituito dall'API per la chiamata aggiunta da *webfrontend.*
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    Con .NET Core 3.1 non è necessario perché è possibile usare l'API WeatherForecast già presente. Tuttavia, è necessario impostare come commento la chiamata a nel metodo in Startup.cs , perché questo codice usa <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> `Configure` HTTP, non HTTPS, per chiamare l'API Web. 

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. Nel progetto `WebFrontEnd` scegliere Add > Container **Orchestrator Support**. Verrà visualizzata la finestra di dialogo Opzioni di supporto di **Docker.**

1. Scegliere **Docker Compose**.

1. Scegliere il sistema operativo di destinazione, ad esempio Linux.

   ![Screenshot della scelta del sistema operativo di destinazione](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio crea un file *docker-compose.yml* e un file con estensione *dockerignore* nel nodo **docker-compose** nella soluzione e il progetto viene visualizzato in grassetto, che indica che si tratta del progetto di avvio.

   ![Screenshot della Esplora soluzioni con il progetto docker-compose aggiunto](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   Il *file docker-compose.yml* viene visualizzato come segue:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   Il file *con estensione dockerignore* contiene i tipi di file e le estensioni che docker non deve includere nel contenitore. Questi file sono in genere associati all'ambiente di sviluppo e al controllo del codice sorgente, non all'app o al servizio che si sta sviluppando.

   Per informazioni **dettagliate sui comandi in** esecuzione, vedere la sezione Strumenti contenitore del riquadro di output.  È possibile vedere che lo strumento da riga di comando docker-compose viene usato per configurare e creare i contenitori di runtime.

1. Nel progetto API Web fare di nuovo clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Add**  >  Container Orchestrator Support (Aggiungi **supporto agente di orchestrazione contenitori).** Scegliere **Docker Compose** e quindi selezionare lo stesso sistema operativo di destinazione.  

    > [!NOTE]
    > In questo passaggio verrà Visual Studio creare un Dockerfile. Se si fa questo in un progetto che dispone già del supporto per Docker, viene chiesto se si vuole sovrascrivere il Dockerfile esistente. Se sono state apportate modifiche al Dockerfile che si vuole mantenere, scegliere No.

    Visual Studio apporta alcune modifiche al file docker compose YML. A questo punto sono inclusi entrambi i servizi.

    ```yaml
    version: '3.4'
    
    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
    
      mywebapi:
        image: ${DOCKER_REGISTRY-}mywebapi
        build:
          context: .
          dockerfile: MyWebAPI/Dockerfile
    ```

1. Eseguire ora il sito in locale (F5 o CTRL+F5) per verificare che funzioni come previsto. Se tutti gli elementi sono configurati correttamente con la versione .NET Core 2.x, viene visualizzato il messaggio "Hello from webfrontend and webapi (with value 1)".  Con .NET Core 3 vengono visualizzati i dati delle previsioni meteo.

   Il primo progetto che si usa quando si aggiunge l'orchestrazione del contenitore è configurato per l'avvio quando si esegue o si esegue il debug. È possibile configurare l'azione di avvio in **Proprietà progetto** per il progetto docker-compose.  Nel nodo del progetto docker-compose fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida e quindi scegliere Proprietà **oppure** premere ALT+INVIO.  Lo screenshot seguente mostra le proprietà desiderate per la soluzione usata qui.  Ad esempio, è possibile modificare la pagina caricata personalizzando la **proprietà URL servizio.**

   ![Screenshot delle proprietà del progetto docker-compose](media/tutorial-multicontainer/launch-action.png)

   Ecco cosa viene visualizzato all'avvio (versione .NET Core 2.x):

   ![Screenshot dell'app Web in esecuzione](media/tutorial-multicontainer/webfrontend.png)

   L'app Web per .NET 3.1 mostra i dati meteo in formato JSON.

## <a name="next-steps"></a>Passaggi successivi

Esaminare le opzioni per la distribuzione dei [contenitori in Azure.](/azure/containers)

Per un maggiore controllo sui servizi avviati durante una sessione di debug, vedere come usare i profili di avvio Docker Compose per configurare quali servizi vengono eseguiti durante il debug. Vedere [Gestire i profili di avvio per Docker Compose](launch-profiles.md)

## <a name="see-also"></a>Vedi anche
  
[Modello di Docker Compose](https://docs.docker.com/compose/)  
[Strumenti contenitore](./index.yml)