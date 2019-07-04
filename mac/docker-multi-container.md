---
title: Esercitazione - Creare un'app multi-contenitore con Docker Compose
description: Informazioni su come gestire più di un contenitore e consentire la comunicazione tra di essi in Visual Studio per Mac
author: bytesguy
ms.author: adhartle
ms.date: 06/17/2019
ms.openlocfilehash: df130e86de7f35c43459a70a12c0e9cfafbbe3a4
ms.sourcegitcommit: fd5a5b057df3d733f5224c305096907989811f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2019
ms.locfileid: "67196106"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Creare un'app multi-contenitore con Docker Compose

In questa esercitazione si imparerà a gestire più di un contenitore e consentire la comunicazione tra di essi quando si usa Docker Compose in Visual Studio per Mac.

## <a name="prerequisites"></a>Prerequisiti

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio per Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Creare un'applicazione Web ASP.NET Core e aggiungere il supporto Docker

1. Creare una nuova soluzione selezionando **File > Nuova soluzione**.
1. In **.NET Core > App** scegliere il modello **Applicazione Web**: ![Creare una nuova applicazione ASP.NET](media/docker-quickstart-1.png)
1. Selezionare il framework di destinazione. In questo esempio si userà .NET Core 2.2: ![Impostare il framework di destinazione](media/docker-quickstart-2.png)
1. Immettere i dettagli del progetto, inclusi il nome del progetto (in questo esempio _DockerDemoFrontEnd_) e il nome della soluzione (_DockerDemo_). Il progetto creato contiene tutte le informazioni di base necessarie per compilare ed eseguire un sito Web ASP.NET Core.
1. Nel riquadro della soluzione fare clic con il pulsante destro del mouse sul progetto DockerDemoFrontEnd e selezionare **Aggiungi > Supporto Docker**: ![Aggiungere il supporto Docker](media/docker-quickstart-3.png)

Visual Studio per Mac aggiungerà automaticamente alla soluzione un nuovo progetto denominato **docker-compose** e un **Dockerfile** al progetto esistente.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Creare un'API Web ASP.NET Core e aggiungere il supporto Docker

Si creerà ora un secondo progetto che svolgerà la funzione di API back-end. Il modello **API .NET Core** include un controller che consente di gestire richieste RESTful.

1. Aggiungere un nuovo progetto alla soluzione esistente facendo clic con il pulsante destro del mouse sulla soluzione e scegliendo **Aggiungi > Aggiungi nuovo progetto**.
1. In **.NET Core > App** scegliere il modello **API**.
1. Selezionare il framework di destinazione. In questo esempio si userà .NET Core 2.2.
1. Immettere i dettagli del progetto, tra cui il nome del progetto (in questo esempio, _DockerDemoAPI_).
1. Dopo aver creato il progetto, accedere al riquadro della soluzione, fare clic con il pulsante destro del mouse sul progetto DockerDemoAPI e selezionare **Aggiungi > Supporto Docker**.

Il file **docker-compose.yml** del progetto **docker-compose** verrà automaticamente aggiornato in modo da includere il progetto API oltre al progetto App Web esistente. Quando si compila e si esegue il progetto **docker-compose**, ognuno di questi progetti verrà distribuito in un contenitore Docker separato.

```
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  dockerdemoapi:
    image: ${DOCKER_REGISTRY-}dockerdemoapi
    build:
      context: .
      dockerfile: DockerDemoAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Integrare i due contenitori

Nella soluzione sono ora presenti due progetti ASP.NET, entrambi configurati con il supporto Docker. Si aggiungeranno ora alcune porzioni di codice.

1. Nel progetto `DockerDemoFrontEnd` aprire ile file *Index.cshtml.cs* e sostituire il metodo `OnGet` con il codice seguente:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://dockerdemoapi/api/values/1");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```

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

1. Nel progetto API Web aggiungere ora codice al controller Values in modo da personalizzare il messaggio restituito dall'API per la chiamata aggiunta da *webfrontend*:
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```
1. Impostare il progetto `docker-compose` come progetto di avvio e selezionare **Esegui > Avvia debug**. Se tutto è configurato correttamente, viene visualizzato il messaggio "Salve da webfrontend e da webapi (con valore 1).":

![Soluzione con più contenitori Docker in esecuzione](media/docker-multicontainer-debug.png)
