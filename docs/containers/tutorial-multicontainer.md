---
title: Esercitazione su più contenitori con Docker Compose & ASP.NET Core
author: ghogen
description: Informazioni su come usare più contenitori con Docker Compose
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: b9e1a2fc7c9027c34aeb8a0e0d1d44fdb0211e65
ms.sourcegitcommit: b2fc9ac7d73c847508f6ed082bed026476bb3955
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2020
ms.locfileid: "77027323"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Esercitazione: creare un'app a più contenitori con Docker Compose

In questa esercitazione si apprenderà come gestire più di un contenitore e comunicare tra loro quando si usano gli strumenti contenitore in Visual Studio.  La gestione di più contenitori richiede l' *orchestrazione del contenitore* e richiede un agente di orchestrazione, ad esempio Docker compose, Kubernetes o Service Fabric. In questo caso verrà usato Docker Compose. Docker Compose è ideale per il debug e il test locali nel corso del ciclo di sviluppo.

## <a name="prerequisites"></a>Prerequisites

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con lo **sviluppo Web**, il carico di lavoro **degli strumenti di Azure** o il carico di lavoro **sviluppo multipiattaforma .NET Core** installato
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* [Strumenti di sviluppo per .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) per lo sviluppo con .NET Core 2.2
* [Strumenti di sviluppo .NET Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.1) per lo sviluppo con .net core 3,1.
::: moniker-end

## <a name="create-a-web-application-project"></a>Creare un progetto di applicazione Web

In Visual Studio creare un progetto di **applicazione Web ASP.NET Core** , denominato `WebFrontEnd`. Selezionare **applicazione Web** per creare un'applicazione Web con Razor Pages. 
  
::: moniker range="vs-2017"

Non selezionare **Abilita supporto Docker**. Verrà aggiunto il supporto Docker in un secondo momento.

![Screenshot della creazione del progetto Web](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Screenshot della creazione del progetto Web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

Non selezionare **Abilita supporto Docker**. Verrà aggiunto il supporto Docker in un secondo momento.

![Screenshot della creazione del progetto Web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Creare un progetto API Web

Aggiungere un progetto alla stessa soluzione e chiamarlo *MyWebAPI*. Selezionare **API** come tipo di progetto e deselezionare la casella di controllo **Configura per HTTPS**. In questa progettazione viene usato solo SSL per la comunicazione con il client e non per la comunicazione tra i contenitori nella stessa applicazione Web. Solo `WebFrontEnd` richiede HTTPS e il codice negli esempi presuppone che sia stata cancellata tale casella di controllo.

::: moniker range="vs-2017"
   ![Screenshot della creazione del progetto API Web](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Screenshot della creazione del progetto API Web](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Aggiungere il codice per chiamare l'API Web

1. Nel progetto `WebFrontEnd` aprire il file *index.cshtml.cs* e sostituire il metodo `OnGet` con il codice seguente.

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
    > Nel codice del mondo reale non è necessario eliminare `HttpClient` dopo ogni richiesta. Per le procedure consigliate, vedere [usare HttpClientFactory per implementare richieste http resilienti](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

   Per .NET Core 3,1 in Visual Studio 2019 o versioni successive, il modello di API Web usa un'API WeatherForecast, quindi rimuovere il commento dalla riga e impostare come commento la riga per ASP.NET 2. x.

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

1. (Solo ASP.NET 2. x) A questo punto, nel progetto API Web aggiungere il codice al controller dei valori per personalizzare il messaggio restituito dall'API per la chiamata aggiunta da *WebFrontEnd*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    Con .NET Core 3,1, questa operazione non è necessaria perché è possibile usare l'API WeatherForecast già presente. Tuttavia, è necessario impostare come commento la chiamata a <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> nel metodo `Configure` in *Startup.cs*, perché questo codice USA http, non HTTPS, per chiamare l'API Web.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. Nel progetto `WebFrontEnd` scegliere **aggiungi > supporto**per l'agente di orchestrazione dei contenitori. Viene visualizzata la finestra di dialogo **Opzioni di supporto Docker** .

1. Scegliere **Docker compose**.

1. Scegliere il sistema operativo di destinazione, ad esempio Linux.

   ![Screenshot della scelta del sistema operativo di destinazione](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio crea un file *Docker-compose. yml* e un file con *estensione dockerignore* nel nodo **Docker-compose** della soluzione e il progetto viene visualizzato nel tipo di carattere grassetto, che indica che si tratta del progetto di avvio.

   ![Screenshot della Esplora soluzioni con il progetto Docker-compose aggiunto](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *Docker-compose. yml* viene visualizzato come segue:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   Il file *. dockerignore* contiene i tipi di file e le estensioni che non si vuole includere nel contenitore da Docker. Questi file sono in genere associati all'ambiente di sviluppo e al controllo del codice sorgente, non fanno parte dell'app o del servizio che si sta sviluppando.

   Per informazioni dettagliate sui comandi in esecuzione, vedere la sezione **strumenti contenitore** del riquadro di output.  Per configurare e creare i contenitori di runtime è possibile vedere lo strumento da riga di comando Docker-compose.

1. Nel progetto API Web fare nuovamente clic con il pulsante destro del mouse sul nodo del progetto e scegliere **aggiungi** > supporto per l'agente di **orchestrazione dei contenitori**. Scegliere **Docker compose**, quindi selezionare lo stesso sistema operativo di destinazione.  

    > [!NOTE]
    > In questo passaggio, in Visual Studio verrà offerta la creazione di un Dockerfile. Se si esegue questa operazione in un progetto che ha già il supporto per Docker, viene chiesto se si vuole sovrascrivere il Dockerfile esistente. Se sono state apportate modifiche al Dockerfile che si vuole salvare, scegliere No.

    Visual Studio apporta alcune modifiche al file di Docker compose YML. Sono ora inclusi entrambi i servizi.

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

1. Esegui il sito localmente adesso (F5 o CTRL + F5) per verificare che funzioni come previsto. Se tutti gli elementi sono configurati correttamente con la versione di .NET Core 2. x, viene visualizzato il messaggio "Hello from WebFrontEnd and WebAPI (with value 1)".  Con .NET Core 3, vengono visualizzati i dati relativi alle previsioni meteorologiche.

   Il primo progetto utilizzato per l'aggiunta dell'orchestrazione del contenitore viene configurato per essere avviato quando si esegue o si esegue il debug. È possibile configurare l'azione di avvio nelle **proprietà del progetto** per il progetto Docker-compose.  Nel nodo del progetto Docker-compose, fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida, quindi scegliere **Proprietà**oppure premere ALT + INVIO.  Lo screenshot seguente mostra le proprietà che si desidera usare per la soluzione.  Ad esempio, è possibile modificare la pagina che viene caricata personalizzando la proprietà **URL servizio** .

   ![Screenshot delle proprietà del progetto Docker-compose](media/tutorial-multicontainer/launch-action.png)

   Ecco cosa viene visualizzato all'avvio (la versione di .NET Core 2. x):

   ![Screenshot dell'esecuzione dell'app Web](media/tutorial-multicontainer/webfrontend.png)

   L'app Web per .NET 3,1 Mostra i dati meteo in formato JSON.

## <a name="next-steps"></a>Passaggi successivi

Vedere le opzioni per la distribuzione dei [contenitori in Azure](/azure/containers).

## <a name="see-also"></a>Vedere anche
  
[Docker Compose](https://docs.docker.com/compose/)  
[Strumenti contenitore](/visualstudio/containers/)
