---
title: Visual Studio Strumenti contenitore con ASP.NET Core e React.js
titleSuffix: ''
ms.custom: SEO-VS-2020
author: ghogen
description: Informazioni su come creare un'app spa React contenitori con Visual Studio Container Tools e Docker
ms.author: ghogen
ms.date: 02/21/2021
ms.technology: vs-container-tools
ms.topic: quickstart
ms.openlocfilehash: c009686029355fdb5c9e1d371a4d0a071bec2fc282d5fbc441bd099d52b89dba
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121348406"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Guida introduttiva: Usare Docker con un React app a pagina singola in Visual Studio

Con Visual Studio è possibile compilare, eseguire il debug ed eseguire app ASP.NET Core aggiunte a contenitori, incluse quelle con JavaScript sul lato cliente come le app a pagina singola React.js, e pubblicarle nel Registro Azure Container, in Docker Hub, in Servizio app di Azure o nel proprio registro contenitori. In questo articolo viene eseguita la pubblicazione nel Registro Azure Container (ACR).

## <a name="prerequisites"></a>Prerequisiti

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* Per pubblicare in Registro Azure Container, una sottoscrizione di Azure. [Iscriversi per ottenere una versione di valutazione gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Per Windows contenitori, Windows 10 versione 1809 o successiva, per usare le immagini Docker a cui si fa riferimento in questo articolo.
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* [Strumenti di sviluppo .NET Core 3.1 per](https://dotnet.microsoft.com/download/dotnet-core/3.1) lo sviluppo con .NET Core 3.1.
* Per pubblicare in Registro Azure Container, una sottoscrizione di Azure. [Iscriversi per ottenere una versione di valutazione gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Per Windows contenitori, Windows 10 versione 1809 o successiva, per usare le immagini Docker a cui si fa riferimento in questo articolo.
::: moniker-end

## <a name="installation-and-setup"></a>Installazione e configurazione

Per l'installazione di Docker, esaminare prima di tutto le informazioni in [Docker Desktop per Windows: Cosa](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)sapere prima di installare . Installare [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="create-a-project-and-add-docker-support"></a>Creare un progetto e aggiungere il supporto di Docker

::: moniker range="vs-2017"
1. Creare un nuovo progetto usando il modello **Applicazione Web ASP.NET Core**.
1. Selezionare **React.js**. Non è possibile selezionare **Abilita supporto Docker**, ma non è un problema perché è possibile aggiungere tale supporto dopo aver creato il progetto.

   ![Screenshot del nuovo progetto React.js](media/container-tools-react/vs-2017/new-react-project.png)

1. Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi** > **supporto Docker** per aggiungere un Dockerfile al progetto.

   ![Aggiungere il supporto di Docker](media/container-tools-react/vs-2017/add-docker-support.png)

1. Selezionare il tipo di contenitore e fare clic su **OK.**
::: moniker-end

::: moniker range=">=vs-2019"

1. Creare un nuovo progetto usando il **ASP.NET Core con React.js** modello.

   ![Screenshot della creazione di un nuovo React.js progetto](media/container-tools-react/vs-2019/create-reactjs-project.png)

1. Nella schermata **Informazioni aggiuntive** non è possibile selezionare Abilita supporto **Docker,** ma è possibile aggiungere il supporto in un secondo momento.

   ![Screenshot della creazione di un nuovo progetto React.js - Schermata Informazioni aggiuntive](media/container-tools-react/vs-2019/new-react-project-additional-information.png)

1. Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi** > **supporto Docker** per aggiungere un Dockerfile al progetto.

   ![Aggiungere il supporto di Docker](media/container-tools-react/vs-2017/add-docker-support.png)

1. Selezionare il tipo di contenitore.
::: moniker-end

Il passaggio successivo è diverso a seconda che si utilizzino contenitori Linux o Windows contenitori.

## <a name="modify-the-dockerfile-linux-containers"></a>Modificare il Dockerfile (contenitori Linux)

Nel progetto viene creato un *Dockerfile*, il file recipe per la creazione di un'immagine Docker finale. Per informazioni sui comandi al suo interno, fare riferimento a [Dockerfile](https://docs.docker.com/engine/reference/builder/) reference (Informazioni di riferimento su Dockerfile).

Aprire il *Dockerfile* nel progetto e aggiungere le righe seguenti per installare Node.js 10.x nel contenitore. Assicurarsi di aggiungere queste righe sia nella prima sezione, per aggiungere l'installazione di Node Package Manager *npm.exe* all'immagine di base, nonché nella `build` sezione .

```Dockerfile
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

Il *Dockerfile* dovrebbe ora essere simile al seguente:

```Dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
WORKDIR /src
COPY ["WebApplication-ReactSPA/WebApplication-ReactSPA.csproj", "WebApplication-ReactSPA/"]
RUN dotnet restore "WebApplication-ReactSPA/WebApplication-ReactSPA.csproj"
COPY . .
WORKDIR "/src/WebApplication-ReactSPA"
RUN dotnet build "WebApplication-ReactSPA.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication-ReactSPA.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication-ReactSPA.dll"]
```

Il *Dockerfile* precedente è basato sull'immagine [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) e include istruzioni per modificare l'immagine di base compilando il progetto e aggiungendolo al contenitore.

Se la casella di controllo **Configura per HTTPS** della finestra di dialogo Nuovo progetto è selezionata, il *Dockerfile* espone due porte. Una porta viene usata per il traffico HTTP e l'altra viene usata per il traffico HTTPS. Se la casella di controllo non è selezionata, viene esposta una sola porta (80) per il traffico HTTP.

## <a name="modify-the-dockerfile-windows-containers"></a>Modificare il Dockerfile (Windows contenitori)

Aprire il file di progetto facendo doppio clic sul nodo del progetto e aggiornare il file di progetto (*.csproj) aggiungendo la proprietà seguente come figlio `<PropertyGroup>` dell'elemento :

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Aggiornare il Dockerfile aggiungendo le righe seguenti. Il nodo e npm verranno copiati nel contenitore.

   1. Aggiungere ``# escape=` `` alla prima riga del Dockerfile
   1. Aggiungere le righe seguenti prima di `FROM … base`

      ```Dockerfile
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   2. Aggiungere la riga seguente prima e dopo `FROM … build`

      ```Dockerfile
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   3. Il Dockerfile completo dovrebbe ora essere simile al seguente:

      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      RUN mkdir -p C:\nodejsfolder
      WORKDIR C:\nodejsfolder
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplicationReact1/WebApplicationReact1.csproj", "WebApplicationReact1/"]
      RUN dotnet restore "WebApplicationReact1/WebApplicationReact1.csproj"
      COPY . .
      WORKDIR "/src/WebApplicationReact1"
      RUN dotnet build "WebApplicationReact1.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplicationReact1.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplicationReact1.dll"]
      ```

   4. Aggiornare il file con estensione dockerignore rimuovendo `**/bin` .

## <a name="debug"></a>Debug

Selezionare **Docker** nell'elenco a discesa Debug nella barra degli strumenti e avviare il debug dell'app. È possibile che venga visualizzato un messaggio in cui viene richiesto di considerare attendibile un certificato; scegliere di considerare attendibile il certificato per continuare.  La prima volta che si esegue la compilazione, Docker scarica le immagini di base, quindi potrebbe richiedere più tempo.

L'opzione **Strumenti contenitore** nella finestra **Output** mostra le azioni in corso. Si dovrebbero vedere i passaggi di installazione associati a *npm.exe*.

Il browser visualizza la home page dell'app.

::: moniker range="vs-2017"
   ![Screenshot dell'app in esecuzione](media/container-tools-react/vs-2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Screenshot dell'app in esecuzione](media/container-tools-react/vs-2019/running-app.png)
::: moniker-end

Passare alla pagina *Contatore* e testare il codice sul lato client per il contatore facendo clic sul pulsante **Incrementa**.

Aprire la **console di Gestione pacchetti** dal menu **Strumenti**> Gestione pacchetti NuGet, **Console di Gestione pacchetti**.

L'immagine Docker risultante dell'app, contrassegnata con *dev*, L'immagine è basata sul tag *3.1* dell'immagine di base *dotnet/core/aspnet.* Eseguire il comando `docker images` nella finestra **Console di Gestione pacchetti**. Vengono visualizzate le immagini nel computer in uso:

```console
REPOSITORY                             TAG                 IMAGE ID            CREATED             SIZE
webapplicationreact1                   dev                 09be6ec2405d        2 hours ago         352MB
mcr.microsoft.com/dotnet/core/aspnet   3.1                 e3559b2d50bb        10 days ago         207MB
```

> [!NOTE]
> L'immagine **dev** non contiene i file binari e altri contenuti dell'app poiché le configurazioni **Debug** usano il montaggio volumi per offrire l'esperienza interattiva di modifica e debug. Per creare un'immagine di produzione che contiene tutti i contenuti, usare la configurazione **Rilascio**.

Eseguire il comando `docker ps` nella console di Gestione pacchetti. Si noti che l'app viene eseguita usando il contenitore:

```console
CONTAINER ID        IMAGE                      COMMAND               CREATED             STATUS              PORTS                                           NAMES
56d1b1008c89        webapplicationreact1:dev   "tail -f /dev/null"   2 hours ago         Up 2 hours          0.0.0.0:32771->80/tcp, 0.0.0.0:32770->443/tcp   WebApplication-React1
```

## <a name="publish-docker-images"></a>Pubblicare immagini Docker

Al termine del ciclo di sviluppo e debug dell'app, è possibile creare un'immagine di produzione dell'app.

:::moniker range="vs-2017"

1. Selezionare **Versione** nell'elenco a discesa della configurazione ed eseguire l'app.
1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
1. Nella finestra di dialogo di pubblicazione della destinazione selezionare **Registro Container.**
1. Scegliere **Crea nuovo Registro Azure Container** e fare clic su **Pubblica**.
1. Inserire i valori desiderati in **Creare un nuovo Registro Azure Container**.

    | Impostazione      | Valore consigliato  | Descrizione                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefisso DNS** | Nome univoco a livello globale | Nome che identifica in modo univoco il registro contenitori. |
    | **Sottoscrizione** | Scegliere la sottoscrizione | Sottoscrizione di Azure da usare. |
    | **[Gruppo di risorse](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nome del gruppo di risorse in cui creare il registro contenitori. Per creare un nuovo gruppo di risorse scegliere **Nuovo**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Livello di servizio del registro contenitori  |
    | **Percorso del registro** | Un percorso vicino | Scegliere un Percorso in una [regione](https://azure.microsoft.com/regions/) nelle vicinanze o vicino ad altri servizi usati nel registro contenitori. |

    ![Finestra di dialogo Creare un'istanza di Registro Azure Container di Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

1. Selezionare **Crea**.

   ![Screenshot che indica l'esito positivo della pubblicazione](media/container-tools/publish-succeeded.png)
:::moniker-end

:::moniker range=">=vs-2019"

1. Selezionare **Versione** nell'elenco a discesa della configurazione ed eseguire l'app.
1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
1. Nella finestra di dialogo publish target (Destinazione pubblicazione) selezionare **Docker Container Registry (Registro contenitori Docker).**

   ![Scegliere Registro Contenitori Docker](media/container-tools-react/vs-2019/publish-dialog1.png)

1. Scegliere quindi **Registro Azure Container**.

   ![Scegliere Registro Azure Container](media/container-tools-react/vs-2019/publish-dialog-acr.png)

1. Scegliere **Crea una nuova Registro Azure Container**.
1. Immettere i valori desiderati nella schermata **Create new Registro Azure Container (Crea Registro Azure Container** pagina).

    | Impostazione      | Valore consigliato  | Descrizione                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefisso DNS** | Nome univoco a livello globale | Nome che identifica in modo univoco il registro contenitori. |
    | **Sottoscrizione** | Scegliere la sottoscrizione | Sottoscrizione di Azure da usare. |
    | **[Gruppo di risorse](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nome del gruppo di risorse in cui creare il registro contenitori. Per creare un nuovo gruppo di risorse scegliere **Nuovo**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Livello di servizio del registro contenitori  |
    | **Percorso del registro** | Un percorso vicino | Scegliere un Percorso in una [regione](https://azure.microsoft.com/regions/) nelle vicinanze o vicino ad altri servizi usati nel registro contenitori. |

    ![Finestra di dialogo Creare un'istanza di Registro Azure Container di Visual Studio](media/container-tools-react/vs-2019/azure-container-registry-details.png)

1. Selezionare **Crea** e quindi **Fine.**

   ![Selezionare o creare un nuovo ACR](media/container-tools-react/vs-2019/publish-dialog2.png)

   Al termine del processo di pubblicazione, è possibile esaminare le impostazioni di pubblicazione e modificarle, se necessario, oppure pubblicare nuovamente l'immagine usando il **pulsante Pubblica.**

   ![Screenshot che indica l'esito positivo della pubblicazione](media/container-tools-react/vs-2019/publish-finished.png)

   Per iniziare di nuovo a usare la finestra  **di** dialogo Pubblica, eliminare il profilo di pubblicazione usando il collegamento Elimina in questa pagina e quindi scegliere **di nuovo Pubblica.**
:::moniker-end

## <a name="next-steps"></a>Passaggi successivi

È possibile ora eseguire il pull del contenitore dal registro a qualsiasi host in grado di eseguire immagini Docker, ad esempio [Istanze di Azure Container ](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Risorse aggiuntive

* [Sviluppare con i contenitori in Visual Studio](./index.yml)
* [Risolvere i problemi di sviluppo di Visual Studio con Docker](troubleshooting-docker-errors.md)
* [Repository GitHub degli strumenti contenitore di Visual Studio](https://github.com/Microsoft/DockerTools)

