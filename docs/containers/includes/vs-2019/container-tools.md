---
title: Visual Studio Tools per Docker con ASP.NET
author: ghogen
description: Informazioni su come usare gli Visual Studio 2019 e Docker per Windows
ms.author: ghogen
ms.date: 02/22/2021
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 35beb1bb67dbfe4d0d1707c499b605f6ff698956
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2021
ms.locfileid: "112908032"
---
Con Visual Studio è possibile compilare, eseguire il debug ed eseguire facilmente app .NET, ASP.NET e ASP.NET Core in contenitori e pubblicarle in Registro Azure Container (ACR), Docker Hub, Servizio app di Azure o nel proprio registro contenitori. In questo articolo verrà pubblicata un'app ASP.NET Core in ACR.

## <a name="prerequisites"></a>Prerequisiti

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* [Strumenti di sviluppo .NET Core](https://dotnet.microsoft.com/download/dotnet-core/) per lo sviluppo con .NET Core
* Per pubblicare in Registro Azure Container, una sottoscrizione di Azure. [Iscriversi per ottenere una versione di valutazione gratuita](https://azure.microsoft.com/free/dotnet/).

## <a name="installation-and-setup"></a>Installazione e configurazione

Per l'installazione di Docker, esaminare prima di tutto le informazioni in [Docker Desktop per Windows: Cosa](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)sapere prima di installare . Installare [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Aggiungere un progetto in un contenitore Docker

1. Creare un nuovo progetto usando il modello app **Web ASP.NET Core** oppure, se si vuole usare il .NET Framework anziché .NET Core, scegliere Applicazione Web ASP.NET **(.NET Framework).**
1. Nella schermata **Informazioni aggiuntive assicurarsi** che la casella di controllo Abilita supporto **Docker** sia selezionata.

   ![Casella di controllo Abilita supporto Docker](../../media/container-tools/vs-2019/webapp-additional-information-31-docker.png)

   Lo screenshot mostra .NET Core. Se si usa un .NET Framework, l'aspetto è leggermente diverso.

1. Selezionare il tipo di contenitore appropriato (Windows o Linux) e fare clic su **Crea**.

## <a name="dockerfile-overview"></a>Panoramica di Dockerfile

Nel progetto viene creato un *Dockerfile*, il file recipe per la creazione di un'immagine Docker finale. Fare riferimento a [Dockerfile reference](https://docs.docker.com/engine/reference/builder/) (Informazioni di riferimento su Dockerfile) per una descrizione dei comandi contenuti nel file:

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["WebApplication1/WebApplication1.csproj", "WebApplication1/"]
RUN dotnet restore "WebApplication1/WebApplication1.csproj"
COPY . .
WORKDIR "/src/WebApplication1"
RUN dotnet build "WebApplication1.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication1.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication1.dll"]
```

Il *Dockerfile* precedente è basato sull'immagine [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) e include le istruzioni per modificare l'immagine di base compilando il progetto e aggiungendolo al contenitore. Se si usa il .NET Framework, l'immagine di base sarà diversa.

Se la casella di controllo **Configura per HTTPS** della finestra di dialogo Nuovo progetto è selezionata, il *Dockerfile* espone due porte. Una porta viene usata per il traffico HTTP e l'altra viene usata per il traffico HTTPS. Se la casella di controllo non è selezionata, viene esposta una sola porta (80) per il traffico HTTP.

## <a name="debug"></a>Debug

Selezionare **Docker** nell'elenco a discesa Debug nella barra degli strumenti e avviare il debug dell'app. È possibile che venga visualizzato un messaggio in cui viene richiesto di considerare attendibile un certificato; scegliere di considerare attendibile il certificato per continuare.

L'opzione **Strumenti contenitore** nella finestra **Output** mostra le azioni in corso. La prima volta, il download dell'immagine di base potrebbe richiedere del tempo, ma è molto più veloce nelle esecuzioni successive.

>[!NOTE]
> Se è necessario modificare le porte per il debug, è possibile farlo nellaunchSettings.js *nel* file . Vedere Impostazioni [di avvio del contenitore.](../../container-launch-settings.md)

## <a name="containers-window"></a>Finestra Contenitori

Se è stata Visual Studio 2019 versione 16.4 o successiva, è possibile usare la finestra Contenitori per visualizzare i contenitori in esecuzione nel computer, nonché le immagini disponibili. 

Aprire la **finestra Contenitori** usando la casella di ricerca nell'IDE (premere **CTRL** Q per usarla), digitare e scegliere la finestra +  `container` Contenitori  dall'elenco.

È possibile montare **la finestra** Contenitori in una posizione pratica, ad esempio sotto l'editor, spostarla e seguire le guide di posizionamento della finestra.

Nella finestra trovare il contenitore ed eseguire ogni scheda per visualizzare le variabili di ambiente, i mapping delle porte, i log e il file system.

![Screenshot della finestra Contenitori](../../media/overview/vs-2019/container-tools-window.png)

Per altre informazioni, vedere [Visualizzare e diagnosticare contenitori e immagini in Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Pubblicare immagini Docker

Al termine del ciclo di sviluppo e debug dell'app, è possibile creare un'immagine di produzione dell'app.

1. Selezionare **Versione** nell'elenco a discesa della configurazione ed eseguire l'app.
1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
1. Nella finestra **di dialogo** Publish (Pubblica) selezionare la **scheda Docker Container Registry (Registro contenitori Docker).**

   ![Screenshot della finestra di dialogo Publish (Pubblica) - Scegliere Docker Container Registry (Registro Contenitori Docker)](../../media/container-tools/vs-2019/docker-container-registry.png)

1. Scegliere **Crea nuovo Registro Azure Container**.

   ![Screenshot della finestra di dialogo Pubblica: scegliere Crea un nuovo Registro Azure Container](../../media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

1. Inserire i valori desiderati in **Creare un nuovo Registro Azure Container**.

    | Impostazione      | Valore consigliato  | Descrizione                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefisso DNS** | Nome univoco a livello globale | Nome che identifica in modo univoco il registro contenitori. |
    | **Sottoscrizione** | Scegliere la sottoscrizione | Sottoscrizione di Azure da usare. |
    | **[Gruppo di risorse](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nome del gruppo di risorse in cui creare il registro contenitori. Per creare un nuovo gruppo di risorse scegliere **Nuovo**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Livello di servizio del registro contenitori  |
    | **Percorso del registro** | Un percorso vicino | Scegliere un Percorso in una [regione](https://azure.microsoft.com/regions/) nelle vicinanze o vicino ad altri servizi usati nel registro contenitori. |

    ![Finestra di dialogo Creare un'istanza di Registro Azure Container di Visual Studio][0]

1. Fare clic su **Crea**. La **finestra di** dialogo Pubblica mostra ora il registro creato.

   ![Screenshot della finestra di dialogo Pubblica che Registro Azure Container creata](../../media/container-tools/vs-2019/created-azure-container-registry.png)

1. Scegliere **Fine** per completare il processo di pubblicazione dell'immagine del contenitore nel registro appena creato in Azure.

   ![Screenshot che indica l'esito positivo della pubblicazione](../../media/container-tools/vs-2019/publish-succeeded.png)

## <a name="next-steps"></a>Passaggi successivi

È possibile ora eseguire il pull del contenitore dal registro a qualsiasi host in grado di eseguire immagini Docker, ad esempio [Istanze di Azure Container ](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
