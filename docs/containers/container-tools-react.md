---
title: Strumenti contenitore di Visual Studio con ASP.NET Core
author: ghogen
description: Informazioni su come usare gli strumenti contenitore di Visual Studio e Docker per Windows
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: bcc30ec13096b37d7540c187d11c846d6c575093
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2019
ms.locfileid: "70179941"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Guida introduttiva: Usare Docker con un'app a singola pagina React in Visual Studio

Con Visual Studio è possibile compilare, eseguire il debug ed eseguire app ASP.NET Core aggiunte a contenitori, incluse quelle con JavaScript sul lato cliente come le app a pagina singola React.js, e pubblicarle nel Registro Azure Container, in Docker Hub, in Servizio app di Azure o nel proprio registro contenitori. In questo articolo viene eseguita la pubblicazione nel Registro Azure Container (ACR).

## <a name="prerequisites"></a>Prerequisiti

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* Per pubblicare in Registro Azure Container, una sottoscrizione di Azure. [Iscriversi per ottenere una versione di valutazione gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* [Strumenti di sviluppo per .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) per lo sviluppo con .NET Core 2.2
* Per pubblicare in Registro Azure Container, una sottoscrizione di Azure. [Iscriversi per ottenere una versione di valutazione gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).
::: moniker-end

## <a name="installation-and-setup"></a>Installazione e configurazione

Per l'installazione di Docker, rivedere prima le informazioni riportate in [Docker Desktop for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) (Docker Desktop per Windows: Informazioni da conoscere prima dell'installazione). Installare [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="create-a-project-and-add-docker-support"></a>Creare un progetto e aggiungere il supporto di Docker

::: moniker range="vs-2017"
1. Creare un nuovo progetto usando il modello **Applicazione Web ASP.NET Core**.
1. Selezionare **React.js**. Non è possibile selezionare **Abilita supporto Docker**, ma non è un problema perché è possibile aggiungere tale supporto dopo aver creato il progetto.

   ![Screenshot del nuovo progetto React.js](media/container-tools-react/vs2017/new-react-project.png)

1. Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi** > **Supporto Docker** per aggiungere un Dockerfile al progetto.

   ![Aggiungere il supporto di Docker](media/container-tools-react/vs2017/add-docker-support.png)

1. Selezionare il tipo di contenitore Linux e quindi fare clic su **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Creare un nuovo progetto usando il modello **Applicazione Web ASP.NET Core**.
1. Selezionare **React.js** e fare clic su **Crea**. Non è possibile selezionare **Abilita supporto Docker**, ma non è un problema perché è possibile aggiungere tale supporto in seguito.

   ![Screenshot del nuovo progetto React.js](media/container-tools-react/vs2019/new-react-project.png)

1. Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi** > **Supporto Docker** per aggiungere un Dockerfile al progetto.

   ![Aggiungere il supporto di Docker](media/container-tools-react/vs2017/add-docker-support.png)

1. Selezionare Linux come tipo di contenitore.
::: moniker-end

## <a name="dockerfile-overview"></a>Panoramica di Dockerfile

Nel progetto viene creato un *Dockerfile*, il file recipe per la creazione di un'immagine Docker finale. Vedere le [informazioni di riferimento su Dockerfile](https://docs.docker.com/engine/reference/builder/) per conoscere i comandi inclusi.

Aprire il *Dockerfile* nel progetto e aggiungere le righe seguenti per installare Node.js 10.x nel contenitore. Assicurarsi di aggiungere le righe nella prima sezione, per aggiungere l'installazione dello strumento di gestione pacchetti Node *npm.exe* all'immagine di base che viene usata nei passaggi successivi.

```
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

Il *Dockerfile* dovrebbe ora essere simile al seguente:

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80 
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["WebApplication37/WebApplication37.csproj", "WebApplication37/"]
RUN dotnet restore "WebApplication37/WebApplication37.csproj"
COPY . .
WORKDIR "/src/WebApplication37"
RUN dotnet build "WebApplication37.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication37.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication37.dll"]
```

Il *Dockerfile* precedente è basato sull'immagine [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) e include le istruzioni per modificare l'immagine di base compilando il progetto e aggiungendolo al contenitore.

Se la casella di controllo **Configura per HTTPS** della finestra di dialogo Nuovo progetto è selezionata, il *Dockerfile* espone due porte. Una porta viene usata per il traffico HTTP e l'altra viene usata per il traffico HTTPS. Se la casella di controllo non è selezionata, viene esposta una sola porta (80) per il traffico HTTP.

## <a name="debug"></a>Debug

Selezionare **Docker** nell'elenco a discesa Debug nella barra degli strumenti e avviare il debug dell'app. È possibile che venga visualizzato un messaggio in cui viene richiesto di considerare attendibile un certificato; scegliere di considerare attendibile il certificato per continuare.

L'opzione **Strumenti contenitore** nella finestra **Output** mostra le azioni in corso. Si dovrebbero vedere i passaggi di installazione associati a *npm.exe*.

Il browser visualizza la home page dell'app.

::: moniker range="vs-2017"
   ![Screenshot dell'app in esecuzione](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Screenshot dell'app in esecuzione](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

Passare alla pagina *Contatore* e testare il codice sul lato client per il contatore facendo clic sul pulsante **Incrementa**.

Aprire la **console di Gestione pacchetti** dal menu **Strumenti**> Gestione pacchetti NuGet, **Console di Gestione pacchetti**.

L'immagine Docker risultante dell'app, contrassegnata con *dev*, è basata sul tag *2.2-aspnetcore-runtime* dell'immagine di base *microsoft/dotnet*. Eseguire il comando `docker images` nella finestra **Console di Gestione pacchetti**. Vengono visualizzate le immagini nel computer in uso:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> L'immagine **dev** non contiene i file binari e altri contenuti dell'app poiché le configurazioni **Debug** usano il montaggio volumi per offrire l'esperienza interattiva di modifica e debug. Per creare un'immagine di produzione che contiene tutti i contenuti, usare la configurazione **Rilascio**.

Eseguire il comando `docker ps` nella console di Gestione pacchetti. Si noti che l'app viene eseguita usando il contenitore:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

## <a name="publish-docker-images"></a>Pubblicare immagini Docker

Al termine del ciclo di sviluppo e debug dell'app, è possibile creare un'immagine di produzione dell'app.

1. Selezionare **Versione** nell'elenco a discesa della configurazione ed eseguire l'app.
1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
1. Nella finestra di dialogo Destinazione di pubblicazione, selezionare la scheda **Registro contenitori**.
1. Scegliere **Crea nuovo Registro Azure Container** e fare clic su **Pubblica**.
1. Inserire i valori desiderati in **Creare un nuovo Registro Azure Container**.

    | Impostazione      | Valore consigliato  | DESCRIZIONE                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefisso DNS** | Nome globalmente univoco | Nome che identifica in modo univoco il registro contenitori. |
    | **Sottoscrizione** | Scegliere la sottoscrizione | Sottoscrizione di Azure da usare. |
    | **[Gruppo di risorse](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nome del gruppo di risorse in cui creare il registro contenitori. Per creare un nuovo gruppo di risorse scegliere **Nuovo**.|
    | **[SKU](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Standard | Livello di servizio del registro contenitori  |
    | **Percorso del registro** | Un percorso vicino | Scegliere un Percorso in una [regione](https://azure.microsoft.com/regions/) nelle vicinanze o vicino ad altri servizi usati nel registro contenitori. |

    ![Finestra di dialogo Creare un'istanza di Registro Azure Container di Visual Studio][0]

1. Scegliere **Crea**.

   ![Screenshot che indica l'esito positivo della pubblicazione](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Passaggi successivi

È possibile ora eseguire il pull del contenitore dal registro a qualsiasi host in grado di eseguire immagini Docker, ad esempio [Istanze di Azure Container ](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Risorse aggiuntive

* [Sviluppare con i contenitori in Visual Studio](/visualstudio/containers)
* [Risolvere i problemi di sviluppo di Visual Studio con Docker](troubleshooting-docker-errors.md)
* [Repository GitHub degli strumenti contenitore di Visual Studio](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end