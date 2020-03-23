---
title: Eseguire il debug di app in un contenitore Docker locale. Documenti Microsoft
description: Informazioni su come modificare un'app in esecuzione in un contenitore Docker locale, aggiornare il contenitore tramite Modifica e aggiornamento e quindi impostare punti di interruzione di debug.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 9f1d80d540e9a25a3ef62ee0819c6f6655b9b3ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916530"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Eseguire il debug di app in un contenitore Docker localeDebug apps in a local Docker container

Visual Studio fornisce un modo coerente per sviluppare contenitori Docker e convalidare l'applicazione in locale. È possibile eseguire ed eseguire il debug delle app in contenitori Linux o Windows in esecuzione sul desktop di Windows locale con Docker installato e non è necessario riavviare il contenitore ogni volta che si apporta una modifica al codice.

Questo articolo illustra come usare Visual Studio per avviare un'app in un contenitore Docker locale, apportare modifiche e quindi aggiornare il browser per visualizzare le modifiche. Questo articolo illustra anche come impostare punti di interruzione per il debug per le app con contenitori. I tipi di progetto supportati includono le app Web e console di .NET Framework e .NET Core.Supported project types include .NET Framework and .NET Core web and console apps. In questo articolo vengono usate app Web di base ASP.NET core e app console di .NET Framework.

Se si dispone già di un progetto di un tipo supportato, Visual Studio può creare un Dockerfile e configurare il progetto per l'esecuzione in un contenitore. Vedere [Strumenti contenitore in Visual Studio](overview.md).

## <a name="prerequisites"></a>Prerequisites

Per eseguire il debug delle app in un contenitore Docker locale, è necessario installare gli strumenti seguenti:To debug apps in a local Docker container, the following tools must be installed:

::: moniker range="vs-2017"

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con il carico di lavoro di sviluppo Web installato

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro di sviluppo Web installato

::: moniker-end

Per eseguire i contenitori Docker in locale, è necessario disporre di un client Docker locale. È possibile utilizzare [la casella degli strumenti Docker](https://www.docker.com/products/docker-toolbox), che richiede la disabilitazione di Hyper-V. È anche possibile usare [Docker per Windows](https://www.docker.com/get-docker), che utilizza Hyper-V e richiede Windows 10.

I contenitori Docker sono disponibili per i progetti .NET Framework e .NET Core. Di seguito sono riportati due esempi. In primo luogo, esaminiamo un'app web .NET Core. Quindi, esaminiamo un'app console di .NET Framework.

## <a name="create-a-web-app"></a>Creare un'app Web

Se si dispone di un progetto e si è aggiunto il supporto Docker come descritto nella [panoramica](overview.md), ignorare questa sezione.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Modificare il codice e aggiornarlo

Per scorrere rapidamente le modifiche, è possibile avviare l'applicazione in un contenitore. Quindi, continuare ad apportare modifiche, visualizzarle come si farebbe con IIS Express.

1. Assicurarsi che Docker sia configurato per l'utilizzo del tipo di contenitore (Linux o Windows) in uso. Fare clic con il pulsante destro del mouse sull'icona Docker sulla barra delle applicazioni e scegliere **Passa a contenitori Linux** o Passa a **contenitori Windows** in base alle esigenze.

1. (solo .NET Core 3 e versioni successive) La modifica del codice e l'aggiornamento del sito in esecuzione come descritto in questa sezione non sono abilitati nei modelli predefiniti in .NET Core >3.0. Per abilitarlo, aggiungere il pacchetto NuGet [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). In *Startup.cs*aggiungere una chiamata `IMvcBuilder.AddRazorRuntimeCompilation` al metodo di `ConfigureServices` estensione al codice nel metodo . Questa opzione è necessaria solo in modalità DEBUG, pertanto è possibile codificarla come segue:

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

   Per ulteriori informazioni, consultate Compilazione di [file Razor in ASP.NET Core](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1).

1. Impostare **Configurazione soluzione su** **Debug**. Quindi, premere **Ctrl**+**F5** per compilare l'immagine Docker ed eseguirla localmente.

    Quando l'immagine del contenitore viene compilata e in esecuzione in un contenitore Docker, Visual Studio avvia l'app Web nel browser predefinito.

1. Vai alla pagina *Indice.* Apportiamo modifiche in questa pagina.
1. Tornare a Visual Studio e aprire *Index.cshtml*.
1. Aggiungere il seguente contenuto HTML alla fine del file e quindi salvare le modifiche.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Nella finestra di output, al termine della compilazione di .NET e vengono visualizzate le righe seguenti, tornare al browser e aggiornare la pagina:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Le modifiche sono state applicate.

### <a name="debug-with-breakpoints"></a>Eseguire il debug con punti di interruzione

Spesso, i cambiamenti richiedono un'ulteriore ispezione. È possibile utilizzare le funzionalità di debug di Visual Studio per questa attività.

1. In Visual Studio aprire *Index.cshtml.cs*.
2. Sostituire il contenuto `OnGet` del metodo con il codice seguente:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. A sinistra della riga di codice, impostare un punto di interruzione.
4. Per avviare il debug e raggiungere il punto di interruzione, premere F5.
5. Passare a Visual Studio per visualizzare il punto di interruzione. Esaminare i valori.

   ![Punto di interruzione](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Creare un'app console .NET Framework

Quando si usano i progetti di app console di .NET Framework, l'opzione per aggiungere il supporto Docker senza orchestrazione non è supportata. È comunque possibile utilizzare la procedura seguente, anche se si utilizza un solo progetto Docker.

1. Creare un nuovo progetto di app Console .NET Framework.Create a new .NET Framework Console app project.
1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto, quindi scegliere **Aggiungi** > **supporto orchestrazione contenitore**.  Nella finestra di dialogo visualizzata selezionare **Composizione docker**. Un Dockerfile viene aggiunto al progetto e viene aggiunto un progetto Docker Compose con file di supporto associati.

### <a name="debug-with-breakpoints"></a>Eseguire il debug con punti di interruzione

1. In Esplora soluzioni aprire *Program.cs*.
2. Sostituire il contenuto `Main` del metodo con il codice seguente:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Impostare un punto di interruzione a sinistra della riga di codice.
4. Premere F5 per avviare il debug e raggiungere il punto di interruzione.
5. Passare a Visual Studio per visualizzare il punto di interruzione ed esaminare i valori.

   ![Punto di interruzione](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Riutilizzo del contenitore

Durante il ciclo di sviluppo, Visual Studio ricompila solo le immagini del contenitore e il contenitore stesso quando si modifica il Dockerfile. Se non si modifica il Dockerfile, Visual Studio riutilizza il contenitore da un'esecuzione precedente.

Se il contenitore è stato modificato manualmente e si desidera riavviare con un'immagine del contenitore pulito, usare il comando **Compila** > **pulizia** in Visual Studio e quindi compilare normalmente.

## <a name="troubleshoot"></a>Risolvere problemi

Informazioni su come [risolvere i problemi di sviluppo di Visual Studio Docker](troubleshooting-docker-errors.md).

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni, leggere [Come Visual Studio compila le app con contenitori](container-build.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Altre informazioni su Docker con Visual Studio, Windows e Azure

* Ulteriori informazioni sullo [sviluppo di contenitori con Visual Studio](/visualstudio/containers).
* Per compilare e distribuire un contenitore Docker, vedere [Integrazione di Docker per le pipeline](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker)di Azure.To build and deploy a Docker container, see Docker integration for Azure Pipelines .
* Per un indice degli articoli di Windows Server e Nano Server, vedere [Informazioni sui contenitori Windows](/virtualization/windowscontainers/).
* Informazioni sul [servizio Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/) ed esaminare la documentazione relativa al [servizio Azure Kubernetes.](/azure/aks)
