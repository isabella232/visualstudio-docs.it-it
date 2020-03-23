---
title: Esercitazione multicontenitore con Docker Compose & ASP.NET CoreMulticontainer tutorial using Docker Compose & ASP.NET Core
author: ghogen
description: Informazioni su come usare più contenitori con Docker Compose
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: b9e1a2fc7c9027c34aeb8a0e0d1d44fdb0211e65
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027323"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Esercitazione: Creare un'app multicontenitore con Docker ComposeTutorial: Create a multi-container app with Docker Compose

In this tutorial, you'll learn how to manage more than one container and communicate between them when using Container Tools in Visual Studio.  La gestione di più contenitori richiede *l'orchestrazione* dei contenitori e richiede un agente di orchestrazione, ad esempio Docker Compose, Kubernetes o Service Fabric.Managing multiple containers requires container orchestration and requires an orchestrator such as Docker Compose, Kubernetes, or Service Fabric. Qui, useremo Docker Compose. Docker Compose è ideale per il debug locale e test nel corso del ciclo di sviluppo.

## <a name="prerequisites"></a>Prerequisites

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con il carico di lavoro **di sviluppo Web,** **Azure Tools** o **.NET Core cross-platform Development**
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* [Strumenti di sviluppo per .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) per lo sviluppo con .NET Core 2.2
* Strumenti di [sviluppo .NET Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.1) per lo sviluppo con .NET Core 3.1.
::: moniker-end

## <a name="create-a-web-application-project"></a>Creare un progetto di applicazione Web

In Visual Studio creare un progetto di `WebFrontEnd`applicazione Web ASP.NET **core,** denominato . Selezionare **Applicazione Web** per creare un'applicazione Web con pagine Razor. 
  
::: moniker range="vs-2017"

Non selezionare **Abilita supporto Docker**. Si aggiungerà il supporto Docker in un secondo momento.

![Screenshot della creazione del progetto Web](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Screenshot della creazione del progetto Web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

Non selezionare **Abilita supporto Docker**. Si aggiungerà il supporto Docker in un secondo momento.

![Screenshot della creazione del progetto Web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Creare un progetto API Web

Aggiungere un progetto alla stessa soluzione e chiamarlo *MyWebAPI*. Selezionare **API** come tipo di progetto e deselezionare la casella di controllo **Configura per HTTPS**. In questa progettazione, utilizziamo SSL solo per la comunicazione con il client, non per la comunicazione da un contenitore all'altro nella stessa applicazione Web. Richiede `WebFrontEnd` solo HTTPS e il codice negli esempi presuppone che sia stata deselezionata la casella di controllo.

::: moniker range="vs-2017"
   ![Screenshot della creazione del progetto API Web](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Screenshot della creazione del progetto API Web](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Aggiungere codice per chiamare l'API WebAdd code to call the Web API

1. Nel `WebFrontEnd` progetto aprire il *file Index.cshtml.cs* `OnGet` e sostituire il metodo con il codice seguente.

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
    > Nel codice reale, non è consigliabile eliminare `HttpClient` dopo ogni richiesta. Per le procedure consigliate, vedere [Utilizzare HttpClientFactory per implementare richieste HTTP resilienti.](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests)

   Per .NET Core 3.1 in Visual Studio 2019 o versioni successive, il modello di API Web utilizza un'API WeatherForecast, quindi rimuovere il commento tale riga e commentare la riga per ASP.NET 2.x.

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

1. (solo ASP.NET 2.x) Nel progetto API Web aggiungere codice al controller Values per personalizzare il messaggio restituito dall'API per la chiamata aggiunta da *webfrontend*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    Con .NET Core 3.1, non è necessario, perché è possibile utilizzare l'API WeatherForecast già presente. Tuttavia, è necessario impostare <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> come `Configure` commento la chiamata a nel metodo in *Startup.cs*, poiché questo codice utilizza HTTP, non HTTPS, per chiamare l'API Web.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. Nel `WebFrontEnd` progetto scegliere **Aggiungi > supporto dell'orchestratore di contenitori**. Viene visualizzata la finestra di dialogo **Opzioni di supporto Docker.**

1. Scegliere **Componi Docker**.

1. Scegliere il sistema operativo di destinazione, ad esempio Linux.Choose your Target OS, for example, Linux.

   ![Screenshot della scelta del sistema operativo di destinazione](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio crea un file *docker-compose.yml* e un file *.dockerignore* nel nodo **docker-compose** nella soluzione e tale progetto mostra in grassetto, che indica che si tratta del progetto di avvio.

   ![Screenshot di Esplora soluzioni con l'aggiunta di un progetto docker-compose](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   Il *docker-compose.yml* appare come segue:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   Il file *.dockerignore* contiene tipi di file ed estensioni che non si desidera vengano inclusi da Docker nel contenitore. Questi file sono in genere associati all'ambiente di sviluppo e al controllo del codice sorgente, non fanno parte dell'app o del servizio che si sta sviluppando.

   Esaminare la sezione **Strumenti contenitore** del riquadro di output per i dettagli dei comandi in esecuzione.  È possibile vedere lo strumento della riga di comando docker-compose viene utilizzato per configurare e creare i contenitori di runtime.

1. Nel progetto API Web fare nuovamente clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi** > **supporto orchestratore contenitore**. Scegliere **Docker Compose**, quindi selezionare lo stesso sistema operativo di destinazione.  

    > [!NOTE]
    > In this step, Visual Studio will offer to create a Dockerfile. Se si esegue questa operazione su un progetto che dispone già del supporto Docker, viene richiesto se si desidera sovrascrivere il file Dockerfile esistente. Se sono state apportate modifiche al Dockerfile che si desidera mantenere, scegliere No.

    Visual Studio apporta alcune modifiche al file YML di docker. Ora entrambi i servizi sono inclusi.

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

1. Eseguire il sito in locale ora (F5 o Ctrl -F5) per verificare che funzioni come previsto. Se tutto è configurato correttamente con la versione di .NET Core 2.x, viene visualizzato il messaggio "Hello from webfrontend e webapi (con valore 1)."  Con .NET Core 3 vengono visualizzati i dati delle previsioni meteo.

   Il primo progetto utilizzato quando si aggiunge l'orchestrazione del contenitore è configurato per essere avviato quando si esegue o si esegue il debug. È possibile configurare l'azione di avvio nelle proprietà del **progetto** per il progetto docker-compose.  Nel nodo del progetto docker-compose fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida, quindi scegliere **Proprietà**oppure utilizzare ALT .  La schermata seguente mostra le proprietà desiderate per la soluzione utilizzata qui.  Ad esempio, è possibile modificare la pagina caricata personalizzando la proprietà **URL servizio.**

   ![Screenshot della composizione delle proprietà del progetto docker](media/tutorial-multicontainer/launch-action.png)

   Ecco cosa si vede quando viene lanciato (la versione di .NET Core 2.x):

   ![Screenshot dell'app Web in esecuzione](media/tutorial-multicontainer/webfrontend.png)

   L'app Web per .NET 3.1 mostra i dati meteo in formato JSON.

## <a name="next-steps"></a>Passaggi successivi

Esaminare le opzioni per la distribuzione dei [contenitori in Azure](/azure/containers).

## <a name="see-also"></a>Vedere anche
  
[Modello di Docker Compose](https://docs.docker.com/compose/)  
[Strumenti contenitore](/visualstudio/containers/)
