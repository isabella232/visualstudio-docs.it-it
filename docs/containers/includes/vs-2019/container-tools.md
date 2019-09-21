---
title: Visual Studio Tools per Docker con ASP.NET Core
author: ghogen
description: Informazioni su come usare gli strumenti di Visual Studio 2019 e Docker per Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 124f60a4a632115625524b4e30ab28f795d41660
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2019
ms.locfileid: "70312252"
---
Con Visual Studio è possibile creare, eseguire il debug ed eseguire facilmente app ASP.NET Core in contenitori e pubblicarle in Azure Container Registry (ACR), nell'hub Docker, nel servizio app Azure o nel registro contenitori. In questo articolo viene eseguita la pubblicazione nel Registro Azure Container (ACR).

## <a name="prerequisites"></a>Prerequisiti

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* [Strumenti di sviluppo per .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) per lo sviluppo con .NET Core 2.2
* Per pubblicare in Registro Azure Container, una sottoscrizione di Azure. [Iscriversi per ottenere una versione di valutazione gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Installazione e configurazione

Per l'installazione di Docker, rivedere prima le informazioni riportate in [Docker Desktop for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) (Docker Desktop per Windows: Informazioni da conoscere prima dell'installazione). Installare [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Aggiungere un progetto in un contenitore Docker

1. Creare un nuovo progetto usando il modello **Applicazione Web ASP.NET Core**.
1. Selezionare **applicazione Web**e verificare che sia selezionata la casella di controllo **Abilita supporto Docker** .

   ![Casella di controllo Abilita supporto Docker](../../media/container-tools/vs-2019/create-new-web-application.PNG)

1. Selezionare il tipo di contenitore appropriato (Windows o Linux) e fare clic su **Crea**.

## <a name="dockerfile-overview"></a>Panoramica di Dockerfile

Nel progetto viene creato un *Dockerfile*, il file recipe per la creazione di un'immagine Docker finale. Fare riferimento a [Dockerfile reference](https://docs.docker.com/engine/reference/builder/) (Informazioni di riferimento su Dockerfile) per una descrizione dei comandi contenuti nel file:

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Il *Dockerfile* precedente è basato sull'immagine [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) e include le istruzioni per modificare l'immagine di base compilando il progetto e aggiungendolo al contenitore.

Se la casella di controllo **Configura per HTTPS** della finestra di dialogo Nuovo progetto è selezionata, il *Dockerfile* espone due porte. Una porta viene usata per il traffico HTTP e l'altra viene usata per il traffico HTTPS. Se la casella di controllo non è selezionata, viene esposta una sola porta (80) per il traffico HTTP.

## <a name="debug"></a>Debug

Selezionare **Docker** nell'elenco a discesa Debug nella barra degli strumenti e avviare il debug dell'app. È possibile che venga visualizzato un messaggio in cui viene richiesto di considerare attendibile un certificato; scegliere di considerare attendibile il certificato per continuare.

L'opzione **Strumenti contenitore** nella finestra **Output** mostra le azioni in corso.

Aprire la **console di Gestione pacchetti** dal menu **Strumenti**> Gestione pacchetti NuGet, **Console di Gestione pacchetti**.

L'immagine Docker risultante dell'app, contrassegnata con *dev*, è basata sul tag *2.2-aspnetcore-runtime* dell'immagine di base *microsoft/dotnet*. Eseguire il comando `docker images` nella finestra **Console di Gestione pacchetti**. Vengono visualizzate le immagini nel computer in uso:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> L'immagine **dev** non contiene i file binari e altri contenuti dell'app poiché le configurazioni **Debug** usano il montaggio volumi per offrire l'esperienza interattiva di modifica e debug. Per creare un'immagine di produzione che contiene tutti i contenuti, usare la configurazione **Rilascio**.

Eseguire il comando `docker ps` nella console di Gestione pacchetti. Si noti che l'app viene eseguita usando il contenitore:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        hellodockertools:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
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

1. Fare clic su **Crea**

   ![Screenshot che indica l'esito positivo della pubblicazione](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Fasi successive

È possibile ora eseguire il pull del contenitore dal registro a qualsiasi host in grado di eseguire immagini Docker, ad esempio [Istanze di Azure Container ](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png