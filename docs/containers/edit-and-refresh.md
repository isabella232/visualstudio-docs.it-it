---
title: Eseguire il debug di app in un contenitore Docker | Microsoft Docs
description: Informazioni su come modificare un'app in esecuzione in un contenitore Docker locale, aggiornare il contenitore tramite Modifica e aggiornamento e quindi impostare punti di interruzione del debug.
ms.author: ghogen
author: ghogen
manager: jmartens
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: how-to
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 8fb821acb48dd05aa09723fe5c6c254e7d1ca648
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306384"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Eseguire il debug di app in un contenitore Docker locale

Visual Studio un modo coerente per sviluppare contenitori Docker e convalidare l'applicazione in locale.
È possibile eseguire le app ed eseguirne il debug in contenitori Linux o Windows in esecuzione nel desktop locale di Windows con Docker installato e non è necessario riavviare il contenitore ogni volta che si apporta una modifica al codice.

Questo articolo illustra come usare Visual Studio per avviare un'app in un contenitore Docker locale, apportare modifiche e quindi aggiornare il browser per visualizzare le modifiche. Questo articolo illustra anche come impostare punti di interruzione per il debug per le app in contenitori. I tipi di progetto supportati includono .NET Framework e app Web e console .NET Core. In questo articolo vengono usate le app ASP.NET Core e le .NET Framework console.

Se si dispone già di un progetto di un tipo supportato, Visual Studio possibile creare un Dockerfile e configurare il progetto per l'esecuzione in un contenitore. Vedere [Strumenti contenitore in Visual Studio](overview.md).

## <a name="prerequisites"></a>Prerequisiti

Per eseguire il debug delle app in un contenitore Docker locale, è necessario installare gli strumenti seguenti:

::: moniker range="vs-2017"

* [Visual Studio 2017 con il](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) carico di lavoro Sviluppo Web installato

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019 con il](https://visualstudio.microsoft.com/downloads) carico di lavoro Sviluppo Web installato

::: moniker-end

::: moniker range="vs-2022"

* [Visual Studio 2022 Preview con]() il carico di lavoro Sviluppo Web installato

::: moniker-end

Per eseguire i contenitori Docker in locale, è necessario un client Docker locale. È possibile usare [Docker per Windows](https://www.docker.com/get-docker), che usa Hyper-V e richiede Windows 10.

I contenitori Docker sono disponibili per .NET Framework e per i progetti .NET Core. Di seguito sono riportati due esempi. In primo luogo, si osserva un'app Web .NET Core. Verrà quindi osservata un'.NET Framework console.

## <a name="create-a-web-app"></a>Creare un'app Web

Se si ha un progetto e si è aggiunto il supporto di Docker come descritto nella [panoramica,](overview.md)ignorare questa sezione.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Modificare il codice e aggiornarlo

Per eseguire rapidamente l'iterazione delle modifiche, è possibile avviare l'applicazione in un contenitore. Continuare quindi ad apportare modifiche, visualizzandole come si farebbe con IIS Express.

1. Assicurarsi che Docker sia configurato per l'uso del tipo di contenitore (Linux o Windows) in uso. Fare clic con il pulsante destro del mouse sull'icona di Docker sulla barra delle applicazioni e scegliere Passa a contenitori **Linux** o **Passa ai contenitori Windows** in base alle esigenze.

1. (solo .NET Core 3 e versioni successive) La modifica del codice e l'aggiornamento del sito in esecuzione come descritto in questa sezione non sono abilitati nei modelli predefiniti in .NET Core >= 3.0. Per abilitarla, aggiungere il pacchetto NuGet [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). In *Startup.cs* aggiungere una chiamata al metodo di `IMvcBuilder.AddRazorRuntimeCompilation` estensione al codice nel metodo `ConfigureServices` . Questa opzione è necessaria solo in modalità DEBUG, quindi codificarla come segue:

    ```csharp
    public IWebHostEnvironment Env { get; set; }

    public void ConfigureServices(IServiceCollection services)
    {
        IMvcBuilder builder = services.AddRazorPages();

    #if DEBUG
        if (Env.IsDevelopment())
        {
            builder.AddRazorRuntimeCompilation();
        }
    #endif

        // code omitted for brevity
    }
    ```

    Modificare il `Startup` metodo come segue:

    ```csharp
    public Startup(IConfiguration configuration, IWebHostEnvironment webHostEnvironment)
    {
        Configuration = configuration;
        Env = webHostEnvironment;
    }
    ```

   Per altre informazioni, vedere [Compilazione di file Razor in ASP.NET Core.](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1&preserve-view=true)

1. Impostare **Configurazione soluzione su** **Debug**. Premere quindi **CTRL** + **F5 per** compilare l'immagine Docker ed eseguirla in locale.

    Quando l'immagine del contenitore viene compilata ed eseguita in un contenitore Docker, Visual Studio avvia l'app Web nel browser predefinito.

1. Passare alla *pagina* Indice. In questa pagina verranno apportate modifiche.
1. Tornare a Visual Studio aprire *Index.cshtml.*
1. Aggiungere il contenuto HTML seguente alla fine del file e quindi salvare le modifiche.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Nella finestra di output, al termine della compilazione .NET e vengono visualizzati le righe seguenti, tornare al browser e aggiornare la pagina:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Le modifiche sono state applicate.

### <a name="debug-with-breakpoints"></a>Eseguire il debug con punti di interruzione

Spesso, le modifiche richiedono un'ulteriore ispezione. È possibile usare le funzionalità di debug di Visual Studio per questa attività.

1. In Visual Studio aprire *Index.cshtml.cs*.
2. Sostituire il contenuto del metodo `OnGet` con il codice seguente:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. A sinistra della riga di codice impostare un punto di interruzione.
4. Per avviare il debug e selezionare il punto di interruzione, premere F5.
5. Passare all'Visual Studio per visualizzare il punto di interruzione. Controllare i valori.

   ![Screenshot che mostra parte del codice per Index.cshtml.cs in Visual Studio con un punto di interruzione impostato a sinistra di una riga di codice evidenziata in giallo.](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app&quot;></a>Creare un'app console .NET Framework

Quando si usano .NET Framework di app console, l'opzione per aggiungere il supporto di Docker senza orchestrazione non è supportata. È comunque possibile usare la procedura seguente, anche se si usa un solo progetto Docker.

1. Creare un nuovo progetto .NET Framework app Console.
1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e quindi scegliere **Aggiungi supporto**  >  **orchestrazione contenitori**.  Nella finestra di dialogo visualizzata selezionare **Docker Compose**. Un Dockerfile viene aggiunto al progetto e viene aggiunto un Docker Compose con i file di supporto associati.

### <a name=&quot;debug-with-breakpoints&quot;></a>Eseguire il debug con punti di interruzione

1. In Esplora soluzioni aprire *Program.cs.*
2. Sostituire il contenuto del metodo `Main` con il codice seguente:

   ```csharp
       System.Console.WriteLine(&quot;Hello, world!");
   ```

3. Impostare un punto di interruzione a sinistra della riga di codice.
4. Premere F5 per avviare il debug e premere il punto di interruzione.
5. Passare all'Visual Studio per visualizzare il punto di interruzione ed esaminare i valori.

   ![Screenshot della finestra del codice per Program.cs in Visual Studio con un punto di interruzione impostato a sinistra di una riga di codice evidenziata in giallo.](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Riutilizzo dei contenitori

Durante il ciclo di sviluppo, Visual Studio ricompila solo le immagini del contenitore e il contenitore stesso quando si modifica il Dockerfile. Se non si modifica il Dockerfile, Visual Studio riutilizza il contenitore da un'esecuzione precedente.

Se il contenitore è stato modificato manualmente e si vuole riavviarlo con un'immagine del contenitore pulita, usare il comando Build Clean (Pulisci) in Visual Studio e quindi eseguire la compilazione  >   come di consueto.

## <a name="troubleshoot"></a>Risolvere problemi

Informazioni su come risolvere [i problemi Visual Studio sviluppo di Docker.](troubleshooting-docker-errors.md)

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, vedere [How Visual Studio builds containerized apps](container-build.md)(Come creare app in contenitori).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Altre informazioni su Docker con Visual Studio, Windows e Azure

* Altre informazioni sullo sviluppo [di contenitori con Visual Studio](./index.yml).
* Per compilare e distribuire un contenitore Docker, vedere [Integrazione di Docker per Azure Pipelines](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Per un indice degli articoli su Windows Server e Nano Server, vedere Informazioni [sul contenitore Windows.](/virtualization/windowscontainers/)
* Informazioni su [servizio Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/) ed esaminare la [documentazione servizio Azure Kubernetes .](/azure/aks)
