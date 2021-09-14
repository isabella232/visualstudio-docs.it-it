---
title: Visual Studio Strumenti contenitore per Docker in Windows
description: Informazioni sugli strumenti disponibili in Visual Studio per l'uso di Docker
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 08/24/2021
ms.technology: vs-container-tools
ms.openlocfilehash: 24a10d43e14beed22f2817b8a6c5a237a34416ad
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631703"
---
# <a name="visual-studio-container-tools-for-docker"></a>Visual Studio Strumenti contenitore per Docker

Gli strumenti inclusi in Visual Studio per lo sviluppo con contenitori Docker sono facili da usare e semplificano notevolmente la compilazione, il debug e la distribuzione per le applicazioni in contenitori. È possibile usare un contenitore per un singolo progetto o usare l'orchestrazione dei contenitori con Docker Compose o Service Fabric per usare più servizi nei contenitori.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Prerequisiti

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* Per pubblicare in Registro Azure Container, una sottoscrizione di Azure. [Iscriversi per ottenere una versione di valutazione gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Supporto di Docker in Visual Studio

Il supporto di Docker è disponibile per ASP.NET, ASP.NET Core, Funzioni di Azure, .NET Core e .NET Framework console.

Il supporto per Docker in Visual Studio è cambiato nel corso di varie versioni in risposta alle esigenze dei clienti. Esistono due livelli di supporto di Docker che è possibile aggiungere a un progetto e le opzioni supportate variano a seconda del tipo di progetto e della versione di Visual Studio. Con alcuni tipi di progetto supportati, se si vuole semplicemente un contenitore per un singolo progetto, senza usare l'orchestrazione, è possibile farlo aggiungendo il supporto di Docker.  Il livello successivo è rappresentato dal supporto dell'orchestrazione dei contenitori, che aggiunge i file di supporto appropriati per lo specifico agente di orchestrazione scelto.

Con Visual Studio 2017, è possibile usare Docker Compose e Service Fabric come servizi di orchestrazione dei contenitori.

> [!NOTE]
> Se si usa una versione di Visual Studio 2017 precedente alla 15.8 o si usa il modello di progetto .NET Framework (non .NET Core), quando si aggiunge il supporto di Docker viene aggiunto automaticamente il supporto dell'orchestrazione con Docker Compose. 

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>Prerequisiti

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* [Strumenti di sviluppo .NET Core](https://dotnet.microsoft.com/download/dotnet-core/) per lo sviluppo con .NET Core.
* Per pubblicare in Registro Azure Container, una sottoscrizione di Azure. [Iscriversi per ottenere una versione di valutazione gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Supporto di Docker in Visual Studio

Il supporto di Docker è disponibile per i progetti ASP.NET, i progetti ASP.NET Core e i progetti di console .NET Core e .NET Framework.

Il supporto per Docker in Visual Studio è cambiato nel corso di varie versioni in risposta alle esigenze dei clienti. Esistono due livelli di supporto di Docker che è possibile aggiungere a un progetto e le opzioni supportate variano a seconda del tipo di progetto e della versione di Visual Studio. Con alcuni tipi di progetto supportati, se si vuole semplicemente un contenitore per un singolo progetto, senza usare l'orchestrazione, è possibile farlo aggiungendo il supporto di Docker.  Il livello successivo è rappresentato dal supporto dell'orchestrazione dei contenitori, che aggiunge i file di supporto appropriati per lo specifico agente di orchestrazione scelto.

Con Visual Studio 2019 è possibile usare Docker Compose, Kubernetes e Service Fabric come servizi di orchestrazione dei contenitori.

> [!NOTE]
> Se si usa il modello di progetto console .NET Framework completo, l'opzione supportata è Aggiungi supporto di **Container Orchestrator** dopo la creazione del progetto, con opzioni per usare Service Fabric o Docker Compose. L'aggiunta del supporto per la creazione del progetto e l'aggiunta del supporto **Docker** per un singolo progetto senza orchestrazione non sono opzioni disponibili.

In Visual Studio 2019 versione 16.4 e  successive è disponibile la finestra Contenitori, che consente di visualizzare i contenitori in esecuzione, esplorare le immagini disponibili, visualizzare le variabili di ambiente, i log e i mapping delle porte, esaminare il file system, collegare un debugger o aprire una finestra del terminale all'interno dell'ambiente contenitore. Vedere [Usare la finestra Contenitori](view-and-diagnose-containers.md).

::: moniker-end

### <a name="adding-docker-support"></a>Aggiunta del supporto per Docker

È possibile abilitare il supporto di Docker durante la creazione del progetto selezionando **Abilita supporto Docker** quando si crea un nuovo progetto, come illustrato nello screenshot seguente:

::: moniker range="vs-2017"
![Abilitare il supporto di Docker per la nuova app Web ASP.NET Core in Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Abilitare il supporto di Docker per la nuova app Web ASP.NET Core in Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> Per i progetti .NET Framework (non .NET Core) sono disponibili solo i contenitori di Windows.

È possibile aggiungere il supporto di Docker a un progetto esistente selezionando **Aggiungi**  >  **supporto Docker** in **Esplora soluzioni**. I comandi **Aggiungi > Supporto Docker** e **Aggiungi > Supporto per l'agente di orchestrazione del contenitore** sono disponibili nel menu di scelta rapida del nodo di progetto per un progetto ASP.NET Core in **Esplora soluzioni**, come illustrato nello screenshot seguente:

![Opzione di menu Aggiungi Supporto Docker in Visual Studio](./media/overview/add-docker-support-menu.png)

Quando si aggiunge o si abilita il supporto di Docker, Visual Studio aggiunge quanto segue al progetto:

- Un file *Dockerfile*
- Un file con estensione dockerignore
- Un riferimento al pacchetto NuGet per Microsoft.VisualStudio.Azure.Containers.Tools.Targets

Il Dockerfile aggiunto sarà simile al codice seguente. In questo esempio il progetto è denominato `WebApplication-Docker` .

```Dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /src
COPY ["WebApplication-Docker/WebApplication-Docker.csproj", "WebApplication-Docker/"]
RUN dotnet restore "WebApplication-Docker/WebApplication-Docker.csproj"
COPY . .
WORKDIR "/src/WebApplication-Docker"
RUN dotnet build "WebApplication-Docker.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication-Docker.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication-Docker.dll"]
```

::: moniker range="vs-2017"
> [!NOTE]
> Quando si abilita il supporto di Docker durante la creazione del progetto per un progetto ASP.NET (.NET Framework, non un progetto .NET Core), come illustrato nello screenshot seguente, viene aggiunto anche il supporto dell'orchestrazione dei contenitori.

![Abilitare il supporto di Docker Compose per un progetto ASP.NET](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="use-the-containers-window"></a>Usare la finestra Contenitori

La **finestra Contenitori** consente di visualizzare contenitori e immagini nel computer e di vedere cosa succede con essi. È possibile visualizzare il file system, i volumi montati, le variabili di ambiente, le porte usate ed esaminare i file di log.

Aprire la **finestra Contenitori** usando l'avvio rapido (**CTRL** + **Q**) e `containers` digitando . È possibile usare i controlli di ancoraggio per inserire la finestra in un punto qualsiasi. A causa della larghezza della finestra, funziona meglio se ancorata nella parte inferiore dello schermo.

Selezionare un contenitore e usare le schede per visualizzare le informazioni disponibili. Per verificarlo, eseguire l'app abilitata per Docker, aprire la scheda **File** ed espandere la cartella **dell'app** per visualizzare l'app distribuita nel contenitore.

![Screenshot della finestra Contenitori](media/overview/vs-2019/container-tools-window-2.png)

Per altre informazioni, vedere [Usare la finestra Contenitori](view-and-diagnose-containers.md).

## <a name="docker-compose-support"></a>Supporto di Docker Compose

Quando si vuole comporre una soluzione con più contenitori tramite Docker Compose, aggiungere il supporto dell'orchestrazione dei contenitori ai progetti. Ciò consente di eseguire un gruppo di contenitori (un'intera soluzione o un gruppo di progetti) e di eseguirne il debug contemporaneamente, se sono definiti nello stesso file *docker-compose.yml*.

Per aggiungere il supporto dell'orchestrazione dei contenitori tramite Docker Compose, fare clic con il pulsante destro del mouse sul nodo della soluzione o del progetto in **Esplora soluzioni**, scegliere **Aggiungi > Supporto dell'orchestrazione del contenitore**. Scegliere quindi **Docker Compose** per gestire i contenitori.

Dopo aver aggiunto il supporto dell'orchestrazione dei contenitori al progetto, si noteranno un *Dockerfile* aggiunto al progetto (se non esisteva già) e una cartella **docker-compose** aggiunta alla soluzione in **Esplora soluzioni**, come illustrato di seguito:

![File di Docker in Esplora soluzioni in Visual Studio](media/overview/docker-support-solution-explorer.png)

Se il file *docker-compose.yml* esiste già, Visual Studio aggiunge solo le righe del codice di configurazione necessarie in tale file.

Ripetere il processo con gli altri progetti che si vuole controllare tramite Docker Compose.

Se si lavora con un numero elevato di servizi, è possibile risparmiare tempo e risorse di calcolo selezionando il subset di servizi da avviare nella sessione di debug. Vedere [Avviare un subset di servizi Compose.](launch-profiles.md)

## <a name="service-fabric-support"></a>Supporto di Service Fabric

Con gli strumenti di Service Fabric in Visual Studio è possibile occuparsi dello sviluppo e del debug per Azure Service Fabric, gestire l'esecuzione e il debug in locale ed eseguire la distribuzione in Azure.

::: moniker range="vs-2017"
Visual Studio 2017 versione 15.9 e versioni successive con il carico di lavoro Sviluppo di Azure supportano lo sviluppo di microservizi in contenitori usando i contenitori Windows e l'orchestrazione di Service Fabric.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 supporta lo sviluppo di microservizi in contenitori usando i contenitori Windows e l'orchestrazione di Service Fabric.
::: moniker-end

Per un'esercitazione dettagliata, vedere [Esercitazione: Distribuire un'applicazione .NET in](/azure/service-fabric/service-fabric-host-app-in-a-container)un contenitore Windows in Azure Service Fabric .

Per altre informazioni su Azure Service Fabric, vedere [Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Recapito continuo e integrazione continua (CI/CD)

Visual Studio si integra facilmente con Azure Pipelines per l'integrazione e il recapito continui e automatizzati delle modifiche al codice e alla configurazione del servizio. Per iniziare, vedere [Creare la prima pipeline](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2&preserve-view=true).

Per Service Fabric, vedere [Esercitazione: Distribuire l'app ASP.NET Core in Azure Service Fabric usando Azure DevOps Projects.](/azure/devops-project/azure-devops-project-service-fabric)

Per Kubernetes, vedere [Deploy a Docker container app to Azure Kubernetes Service](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops&preserve-view=true) (Distribuire un'app contenitore Docker nel servizio Azure Kubernetes).

## <a name="next-steps"></a>Passaggi successivi

Per altri dettagli sull'implementazione dei servizi e l'uso degli strumenti di Visual Studio per usare i contenitori, vedere gli articoli seguenti:

[Debug delle applicazioni in un contenitore Docker locale](edit-and-refresh.md)

[Distribuire un contenitore ASP.NET in un registro contenitori tramite Visual Studio](hosting-web-apps-in-docker.md)
