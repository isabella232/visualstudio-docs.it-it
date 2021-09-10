---
title: App multi-contenitore con Docker Compose
description: Informazioni su come gestire più di un contenitore e consentire la comunicazione tra di essi in Visual Studio per Mac
ms.custom: SEO-VS-2020
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/03/2020
ms.topic: tutorial
ms.openlocfilehash: f2c5154e2f35c57b46817c36ea669c6a9d0f5797
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964407"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Creare un'app multi-contenitore con Docker Compose

In questa esercitazione si imparerà a gestire più di un contenitore e consentire la comunicazione tra di essi quando si usa Docker Compose in Visual Studio per Mac.

## <a name="prerequisites"></a>Prerequisiti

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio per Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Creare un'applicazione Web ASP.NET Core e aggiungere il supporto Docker

1. Creare una nuova soluzione selezionando **File > Nuova soluzione**.
1. In **App web e console > scegliere** il modello Applicazione **Web:** ![ Crea una nuova ASP.NET applicazione](media/docker-quickstart-1.png)
1. Selezionare il framework di destinazione. In questo esempio si userà .NET Core 3.1: ![ Impostare il framework di destinazione](media/docker-quickstart-2.png)
1. Immettere i dettagli del progetto, inclusi il nome del progetto (in questo esempio _DockerDemoFrontEnd_) e il nome della soluzione (_DockerDemo_). Il progetto creato contiene tutte le informazioni di base necessarie per compilare ed eseguire un sito Web ASP.NET Core.
1. Nella finestra della soluzione fare clic con il pulsante destro del mouse sul progetto DockerDemoFrontEnd e scegliere Aggiungi > Aggiungi supporto **Docker:** ![ Aggiungi supporto Docker](media/docker-quickstart-3.png)

Visual Studio per Mac aggiungerà automaticamente alla soluzione un nuovo progetto denominato **docker-compose** e un **Dockerfile** al progetto esistente.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Creare un'API Web ASP.NET Core e aggiungere il supporto Docker

Si creerà ora un secondo progetto che svolgerà la funzione di API back-end. Il modello **API .NET Core** include un controller che consente di gestire richieste RESTful.

1. Aggiungere un nuovo progetto alla soluzione esistente facendo clic con il pulsante destro del mouse sulla soluzione e scegliendo **Aggiungi > Aggiungi nuovo progetto**.
1. In **App web e console >** scegliere il modello DI **API.**
1. Selezionare il framework di destinazione. In questo esempio si userà .NET Core 3.1.
1. Immettere i dettagli del progetto, ad esempio Project nome (_MyWebAPI_ in questo esempio).
1. Dopo la creazione, passare alla finestra della soluzione e fare clic con il pulsante destro del mouse sul progetto MyWebAPI e > **Aggiungi supporto Docker.**

Il file **docker-compose.yml** del progetto **docker-compose** verrà automaticamente aggiornato in modo da includere il progetto API oltre al progetto App Web esistente. Quando si compila e si esegue il progetto **docker-compose**, ognuno di questi progetti verrà distribuito in un contenitore Docker separato.

```yaml
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  mywebapi:
    image: ${DOCKER_REGISTRY-}mywebapi
    build:
      context: .
      dockerfile: MyWebAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Integrare i due contenitori

Nella soluzione sono ora presenti due progetti ASP.NET, entrambi configurati con il supporto Docker. Si aggiungeranno ora alcune porzioni di codice.

1. Nel `DockerDemoFrontEnd` progetto aprire il file *Pages/Index.cshtml.cs* e sostituire il `OnGet` metodo con il codice seguente:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/WeatherForecast");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > Nel codice di produzione non è consigliabile eliminare `HttpClient` dopo ogni richiesta. Per le procedure consigliate, vedere [Usare HttpClientFactory per implementare richieste HTTP resilienti.](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests)

1. Nel file *index.cshtml* aggiungere una riga per visualizzare `ViewData["Message"]` in modo che il file abbia un aspetto simile al codice seguente:

      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }

      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```
  
1. Nei progetti front-end e API Web impostare come commento la chiamata a [Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection](/dotnet/api/microsoft.aspnetcore.builder.httpspolicybuilderextensions.usehttpsredirection) nel metodo in Startup.cs , perché questo codice di esempio usa HTTP, non HTTPS, per chiamare `Configure` l'API Web. 

      ```csharp
                  //app.UseHttpsRedirection();
      ```

1. Impostare il progetto `docker-compose` come progetto di avvio e selezionare **Esegui > Avvia debug**. Se tutto è configurato correttamente, viene visualizzato il messaggio "Salve da webfrontend e da webapi (con valore 1).":

![Soluzione con più contenitori Docker in esecuzione](media/docker-multicontainer-debug.png)