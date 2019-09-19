---
title: Eseguire il debug di app in un contenitore Docker locale | Microsoft Docs
description: Informazioni su come modificare un'app in esecuzione in un contenitore Docker locale, aggiornare il contenitore tramite modifica e aggiornamento, quindi impostare i punti di interruzione di debug.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 5af092bbcb987f45b10121f37d40eaa5466c3da5
ms.sourcegitcommit: 2db01751deeee7b2bdb1db25419ea6706e6fcdf8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71062178"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Eseguire il debug di app in un contenitore Docker locale

Visual Studio offre un modo coerente per sviluppare in un contenitore Docker e convalidare l'applicazione in locale. Non è necessario riavviare il contenitore ogni volta che si esegue una modifica del codice.

Questo articolo illustra come usare Visual Studio per avviare un'app Web ASP.NET Core in un contenitore Docker locale, apportare modifiche e quindi aggiornare il browser per visualizzare le modifiche. Questo articolo illustra anche come impostare i punti di interruzione per il debug di app Web ASP.NET Core in contenitori e di .NET Framework app console.

## <a name="prerequisites"></a>Prerequisiti

Per eseguire il debug di app in un contenitore Docker locale, è necessario installare gli strumenti seguenti:

::: moniker range="vs-2017"

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con il carico di lavoro sviluppo Web installato

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro sviluppo Web installato

::: moniker-end

Per eseguire localmente i contenitori Docker, è necessario disporre di un client Docker locale. È possibile usare la [casella degli strumenti di Docker](https://www.docker.com/products/docker-toolbox), che richiede la disabilitazione di Hyper-V. È anche possibile usare [Docker per Windows](https://www.docker.com/get-docker), che usa Hyper-V e richiede Windows 10. 

I contenitori Docker sono disponibili per i progetti .NET Framework e .NET Core. Di seguito sono riportati due esempi. Prima di tutto, viene esaminata un'app Web .NET Core. Viene quindi esaminata un'app console .NET Framework.

## <a name="create-a-web-app"></a>Creare un'app Web

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Modificare il codice e aggiornare

Per eseguire rapidamente l'iterazione delle modifiche, è possibile avviare l'applicazione in un contenitore. Quindi, continuare a apportare le modifiche, visualizzandole come si farebbe con IIS Express.

1. Impostare la **configurazione della soluzione** di cui eseguire il **debug**. Premere quindi **CTRL**+**F5** per compilare l'immagine Docker ed eseguirla localmente.

    Quando l'immagine del contenitore viene compilata e in esecuzione in un contenitore Docker, Visual Studio avvia l'app Web nel browser predefinito.

2. Passare alla pagina di *Indice* . Verranno apportate modifiche in questa pagina.
3. Tornare a Visual Studio e aprire *index. cshtml*.
4. Aggiungere il contenuto HTML seguente alla fine del file e quindi salvare le modifiche.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

5. Nella finestra output, al termine della compilazione .NET e vengono visualizzate le righe seguenti, tornare al browser e aggiornare la pagina:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Le modifiche sono state applicate.

### <a name="debug-with-breakpoints"></a>Eseguire il debug con punti di interruzione

Spesso le modifiche richiedono un ulteriore controllo. Per questa attività è possibile usare le funzionalità di debug di Visual Studio.

1. In Visual Studio aprire *index.cshtml.cs*.
2. Sostituire il contenuto del `OnGet` metodo con il codice seguente:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. A sinistra della riga di codice, impostare un punto di interruzione.
4. Per avviare il debug e raggiungere il punto di interruzione, premere F5.
5. Passare a Visual Studio per visualizzare il punto di interruzione. Controllare i valori.

   ![Punto di interruzione](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Creare un'app console .NET Framework

Quando si usa .NET Framework progetti di app console, l'opzione per aggiungere il supporto di Docker senza orchestrazione non è supportata. È comunque possibile usare la procedura seguente, anche se si usa un unico progetto docker.

1. Creare un nuovo progetto di app console .NET Framework.
1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto, quindi scegliere **Aggiungi** > **supporto dell'orchestrazione del contenitore**.  Nella finestra di dialogo visualizzata selezionare **Docker compose**. Un Dockerfile viene aggiunto al progetto e viene aggiunto un progetto Docker Compose con i file di supporto associati.

### <a name="debug-with-breakpoints"></a>Eseguire il debug con punti di interruzione

1. In Esplora soluzioni aprire *Program.cs*.
2. Sostituire il contenuto del `Main` metodo con il codice seguente:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Impostare un punto di interruzione a sinistra della riga di codice.
4. Premere F5 per avviare il debug e raggiungere il punto di interruzione.
5. Passare a Visual Studio per visualizzare il punto di interruzione ed esaminare i valori.

   ![Punto di interruzione](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Riutilizzo del contenitore

Durante il ciclo di sviluppo, Visual Studio ricompila solo le immagini del contenitore e il contenitore stesso quando si modifica il Dockerfile. Se non si modifica il Dockerfile, Visual Studio riutilizza il contenitore da un'esecuzione precedente.

Se il contenitore è stato modificato manualmente e si vuole riavviare con un'immagine del contenitore pulita, usare il comando **Compila** > **Pulisci** in Visual Studio e compilare come di consueto.

## <a name="troubleshoot"></a>Risolvere problemi

Informazioni su come [risolvere i problemi di sviluppo di Docker in Visual Studio](troubleshooting-docker-errors.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Altre informazioni su Docker con Visual Studio, Windows e Azure

* Scopri di più sullo [sviluppo di contenitori con Visual Studio](/visualstudio/containers).
* Per compilare e distribuire un contenitore Docker, vedere [integrazione di Docker per Azure Pipelines](https://aka.ms/dockertoolsforvsts).
* Per un indice degli articoli su Windows Server e nano server, vedere [informazioni sui contenitori di Windows](https://aka.ms/containers).
* Informazioni sul [servizio Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/) e sulla [documentazione del servizio Kubernetes di Azure](/azure/aks).
