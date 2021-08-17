---
title: Eseguire il debug di app in un contenitore Docker | Microsoft Docs
description: Informazioni su come modificare un'app in esecuzione in un contenitore Docker locale, aggiornare il contenitore tramite Modifica e aggiornamento e quindi impostare punti di interruzione di debug.
ms.author: ghogen
author: ghogen
manager: jmartens
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: how-to
ms.workload: multiple
ms.date: 03/08/2021
ms.technology: vs-container-tools
ms.openlocfilehash: 7faf85d07d0c6de4f559e038b47e1935886ac0c3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122098"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Eseguire il debug di app in un contenitore Docker locale

Visual Studio modo coerente per sviluppare contenitori Docker e convalidare l'applicazione in locale.
È possibile eseguire ed eseguire il debug delle app in contenitori Linux o Windows in esecuzione nel desktop Windows locale con Docker installato e non è necessario riavviare il contenitore ogni volta che si apporta una modifica al codice.

Questo articolo illustra come usare Visual Studio un'app in un contenitore Docker locale, apportare modifiche e quindi aggiornare il browser per visualizzare le modifiche. Questo articolo illustra anche come impostare punti di interruzione per il debug per le app in contenitori. I tipi di progetto supportati .NET Framework app Web e console .NET Core. In questo articolo vengono usate ASP.NET Core web e .NET Framework console.

Se si ha già un progetto di un tipo supportato, Visual Studio creare un Dockerfile e configurare il progetto per l'esecuzione in un contenitore. Vedere [Strumenti contenitore in Visual Studio](overview.md).

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

Per eseguire i contenitori Docker in locale, è necessario disporre di un client Docker locale. È possibile usare [Docker per Windows](https://www.docker.com/get-docker), che usa Hyper-V e richiede Windows 10.

I contenitori Docker sono disponibili per i .NET Framework e .NET Core. Di seguito sono riportati due esempi. Prima di tutto, si osserva un'app Web .NET Core. Si analerà quindi un'.NET Framework console.

## <a name="create-a-web-app"></a>Creare un'app Web

Se si ha un progetto ed è stato aggiunto il supporto di Docker come descritto nella [panoramica,](overview.md)ignorare questa sezione.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Modificare il codice e aggiornarlo

Per eseguire rapidamente l'iterazione delle modifiche, è possibile avviare l'applicazione in un contenitore. Continuare quindi a apportare modifiche, visualizzandole come si farebbe con IIS Express.

1. Assicurarsi che Docker sia configurato per l'uso del tipo di contenitore (Linux o Windows) in uso. Fare clic con il pulsante destro del mouse sull'icona Docker sulla barra delle applicazioni e scegliere Passa a contenitori **Linux** o Passa Windows **contenitori in** base alle esigenze.

1. (solo .NET Core 3 e versioni successive) La modifica del codice e l'aggiornamento del sito in esecuzione come descritto in questa sezione non sono abilitati nei modelli predefiniti in .NET Core >= 3.0. Per abilitarlo, aggiungere il pacchetto NuGet [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). In *Startup.cs* aggiungere una chiamata al metodo di `IMvcBuilder.AddRazorRuntimeCompilation` estensione al codice nel metodo `ConfigureServices` . Questa opzione è necessaria solo in modalità DEBUG, quindi codificarla come segue:

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

   Per altre informazioni, vedere [Compilazione di file Razor in ASP.NET Core](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1&preserve-view=true).

1. Impostare **Configurazione soluzione** su **Debug**. Premere quindi **CTRL** + **F5** per compilare l'immagine Docker ed eseguirla in locale.

    Quando l'immagine del contenitore viene compilata e in esecuzione in un contenitore Docker, Visual Studio avvia l'app Web nel browser predefinito.

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
4. Per avviare il debug e raggiunto il punto di interruzione, premere F5.
5. Passare a Visual Studio per visualizzare il punto di interruzione. Esaminare i valori.

   ![Screenshot che mostra parte del codice per Index.cshtml.cs in Visual Studio con un punto di interruzione impostato a sinistra di una riga di codice evidenziata in giallo.](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app&quot;></a>Creare un'app console .NET Framework

Quando si usano .NET Framework di app console, l'opzione per aggiungere il supporto Docker senza orchestrazione non è supportata. È comunque possibile usare la procedura seguente, anche se si usa un solo progetto Docker.

1. Creare un nuovo progetto .NET Framework app console.
1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e quindi scegliere **Aggiungi supporto**  >  **orchestrazione contenitori**.  Nella finestra di dialogo visualizzata selezionare **Docker Compose**. Un Dockerfile viene aggiunto al progetto e viene aggiunto un Docker Compose con i file di supporto associati.

### <a name=&quot;debug-with-breakpoints&quot;></a>Eseguire il debug con punti di interruzione

1. In Esplora soluzioni aprire *Program.cs.*
2. Sostituire il contenuto del metodo `Main` con il codice seguente:

   ```csharp
       System.Console.WriteLine(&quot;Hello, world!");
   ```

3. Impostare un punto di interruzione a sinistra della riga di codice.
4. Premere F5 per avviare il debug e premere il punto di interruzione.
5. Passare a Visual Studio per visualizzare il punto di interruzione ed esaminare i valori.

   ![Screenshot della finestra del codice per Program.cs in Visual Studio con un punto di interruzione impostato a sinistra di una riga di codice evidenziata in giallo.](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Riutilizzo del contenitore

Durante il ciclo di sviluppo, Visual Studio ricompila solo le immagini del contenitore e il contenitore stesso quando si modifica dockerfile. Se non si modifica il Dockerfile, Visual Studio riutilizzo del contenitore da un'esecuzione precedente.

Se il contenitore è stato modificato manualmente e si vuole riavviare con un'immagine del contenitore pulita, usare il comando Compila pulisci in Visual Studio e quindi compilare  >   come di consueto.

## <a name="troubleshoot"></a>Risolvere problemi

Informazioni su come [risolvere i Visual Studio sviluppo di Docker.](troubleshooting-docker-errors.md)

## <a name="next-steps"></a>Passaggi successivi

Per altri dettagli, vedere How Visual Studio builds containerized apps (Come [Visual Studio compila le app in contenitori).](container-build.md)

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Altre informazioni su Docker con Visual Studio, Windows e Azure

* Altre informazioni sullo sviluppo [di contenitori con Visual Studio](./index.yml).
* Per compilare e distribuire un contenitore Docker, vedere [Integrazione di Docker per Azure Pipelines](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Per un indice degli articoli Windows Server e Nano Server, vedere Windows [contenitore](/virtualization/windowscontainers/).
* Informazioni su [servizio Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/) ed esaminare la documentazione [servizio Azure Kubernetes .](/azure/aks)
