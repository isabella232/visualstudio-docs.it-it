---
title: Visual Studio Strumenti contenitore per Docker con ASP.NET in Windows
author: ghogen
description: Informazioni su come usare gli strumenti di Visual Studio 2017 e Docker per Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.technology: vs-container-tools
ms.topic: include
ms.openlocfilehash: d403572e60d29c3af5197cc3bb647fa47bf8c0aa
ms.sourcegitcommit: 8f8804b885c3a68f20bf0e9fe3729f2764145815
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2021
ms.locfileid: "123122143"
---
Con Visual Studio, è possibile compilare, eseguire il debug ed eseguire facilmente app ASP.NET Core ASP.NET Core in contenitori e pubblicarle in Registro Azure Container, Docker Hub, Servizio app di Azure o nel registro contenitori. In questo articolo verrà pubblicata in Registro Contenitori.

## <a name="prerequisites"></a>Prerequisiti

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* Per pubblicare in Registro Azure Container, una sottoscrizione di Azure. [Iscriversi per ottenere una versione di valutazione gratuita](https://azure.microsoft.com/free/dotnet/).

## <a name="installation-and-setup"></a>Installazione e configurazione

Per l'installazione di Docker, esaminare prima le informazioni in [Docker Desktop per Windows: Cosa sapere prima di installare](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Installare [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Aggiungere un progetto in un contenitore Docker

1. Nel menu di Visual Studio selezionare **File > Nuovo > Progetto**.
1. Nella sezione **Modelli** della finestra di dialogo **Nuovo progetto** selezionare **Visual C# > Web**.
1. Selezionare **ASP.NET Core'applicazione Web** oppure, se si vuole usare il .NET Framework anziché .NET Core, selezionare ASP.NET **Applicazione Web**.
1. Assegnare un nome alla nuova applicazione (o accettare quello predefinito), quindi selezionare **OK**.
1. Selezionare **Applicazione Web**.
1. Spuntare la casella di controllo **Abilita Supporto Docker**.

   ![Casella di controllo Abilita supporto Docker](../../media/container-tools/enable-docker-support.PNG)

   Lo screenshot mostra .NET Core. se si usa .NET Framework, l'aspetto è leggermente diverso.

1. Selezionare il tipo di contenitore appropriato (Windows o Linux) e fare clic su **OK**.

## <a name="dockerfile-overview"></a>Panoramica di Dockerfile

Nel progetto viene creato un *Dockerfile*, il file recipe per la creazione di un'immagine Docker finale. Fare riferimento a [Dockerfile reference](https://docs.docker.com/engine/reference/builder/) (Informazioni di riferimento su Dockerfile) per una descrizione dei comandi contenuti nel file:

```
FROM mcr.microsoft.com/dotnet/aspnet:2.1 AS base
WORKDIR /app
EXPOSE 59518
EXPOSE 44364

FROM mcr.microsoft.com/dotnet/sdk:2.1 AS build
WORKDIR /src
COPY HelloDockerTools/HelloDockerTools.csproj HelloDockerTools/
RUN dotnet restore HelloDockerTools/HelloDockerTools.csproj
COPY . .
WORKDIR /src/HelloDockerTools
RUN dotnet build HelloDockerTools.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish HelloDockerTools.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Il *Dockerfile* precedente è basato sull'immagine [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) e include le istruzioni per modificare l'immagine di base compilando il progetto e aggiungendolo al contenitore. Se si usa il .NET Framework, l'immagine di base sarà diversa.

Se la casella di controllo **Configura per HTTPS** della finestra di dialogo Nuovo progetto è selezionata, il *Dockerfile* espone due porte. Una porta viene usata per il traffico HTTP e l'altra viene usata per il traffico HTTPS. Se la casella di controllo non è selezionata, viene esposta una sola porta (80) per il traffico HTTP.

## <a name="debug"></a>Debug

Selezionare **Docker** nell'elenco a discesa Debug nella barra degli strumenti e avviare il debug dell'app. È possibile che venga visualizzato un messaggio in cui viene richiesto di considerare attendibile un certificato; scegliere di considerare attendibile il certificato per continuare.

La finestra **Output** mostra le azioni eseguite.

Aprire la **console di Gestione pacchetti** dal menu **Strumenti**> Gestione pacchetti NuGet, **Console di Gestione pacchetti**.

L'immagine Docker risultante dell'app, contrassegnata con *dev*, è basata sul tag *2.1-aspnetcore-runtime* dell'immagine di base *microsoft/dotnet*. Eseguire il comando `docker images` nella finestra **Console di Gestione pacchetti**. Vengono visualizzate le immagini nel computer in uso:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> L'immagine **dev** non contiene i file binari e altri contenuti dell'app poiché le configurazioni **Debug** usano il montaggio volumi per offrire l'esperienza interattiva di modifica e debug. Per creare un'immagine di produzione che contiene tutti i contenuti, usare la configurazione **Rilascio**.

Eseguire il comando `docker ps` nella console di Gestione pacchetti. Si noti che l'app viene eseguita usando il contenitore:

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
```

## <a name="publish-docker-images"></a>Pubblicare immagini Docker

Al termine del ciclo di sviluppo e debug dell'app, è possibile creare un'immagine di produzione dell'app.

1. Selezionare **Versione** nell'elenco a discesa della configurazione ed eseguire l'app.
1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
1. Nella finestra di dialogo Destinazione di pubblicazione, selezionare la scheda **Registro contenitori**.
1. Scegliere **Crea nuovo Registro Azure Container** e fare clic su **Pubblica**.
1. Inserire i valori desiderati in **Creare un nuovo Registro Azure Container**.

    | Impostazione      | Valore consigliato  | Descrizione                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefisso DNS** | Nome univoco a livello globale | Nome che identifica in modo univoco il registro contenitori. |
    | **Sottoscrizione** | Scegliere la sottoscrizione | Sottoscrizione di Azure da usare. |
    | **[Gruppo di risorse](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nome del gruppo di risorse in cui creare il registro contenitori. Per creare un nuovo gruppo di risorse scegliere **Nuovo**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Livello di servizio del registro contenitori  |
    | **Percorso del registro** | Un percorso vicino | Scegliere un Percorso in una [regione](https://azure.microsoft.com/regions/) nelle vicinanze o vicino ad altri servizi usati nel registro contenitori. |

    ![Finestra di dialogo Creare un'istanza di Registro Azure Container di Visual Studio][0]

1. Fare clic su **Crea**

## <a name="next-steps"></a>Passaggi successivi

È possibile ora eseguire il pull del contenitore dal registro a qualsiasi host in grado di eseguire immagini Docker, ad esempio [Istanze di Azure Container ](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
