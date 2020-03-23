---
title: Visual Studio Tools per Docker con ASP.NET
author: ghogen
description: Informazioni su come usare gli strumenti e la finestra mobile di Visual Studio 2019 per Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 3869cf025b4ed0e744a7fea929aac38acb7dd816
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922978"
---
Con Visual Studio è possibile compilare, eseguire facilmente il debug e l'esecuzione di .NET, ASP.NET e ASP.NET core e pubblicarle nel Registro di sistema contenitore di Azure (ACR), nell'hub Docker, nel servizio app di Azure o nel registro dei contenitori. In questo articolo, pubblicheremo un'app ASP.NET Core in ACR.

## <a name="prerequisites"></a>Prerequisites

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro **Sviluppo Web**, **Strumenti di Azure** e/o **Sviluppo multipiattaforma .NET Core** installato
* [Strumenti di sviluppo .NET Core](https://dotnet.microsoft.com/download/dotnet-core/) per lo sviluppo con .NET Core
* Per pubblicare in Registro Azure Container, una sottoscrizione di Azure. [Iscriviti per una prova gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Installazione e configurazione

Per l'installazione di Docker, leggere prima le informazioni in [Docker Desktop per Windows: Cosa sapere prima](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)di installare . Installare [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Aggiungere un progetto in un contenitore Docker

1. Creare un nuovo progetto utilizzando il modello **applicazione Web ASP.NET Core** oppure, se si desidera utilizzare .NET Framework anziché .NET Core, scegliere ASP.NET applicazione Web **(.NET Framework)**.
1. Selezionare **Applicazione Web**e assicurarsi che la casella di controllo **Abilita supporto Docker** sia selezionata.

   ![Casella di controllo Abilita supporto Docker](../../media/container-tools/vs-2019/create-new-web-application.PNG)

   La schermata mostra .NET Core; Se si utilizza .NET Framework, l'aspetto è leggermente diverso.

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

Il *Dockerfile* precedente è basato sull'immagine [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) e include le istruzioni per modificare l'immagine di base compilando il progetto e aggiungendolo al contenitore. Se si utilizza .NET Framework, l'immagine di base sarà diversa.

Se la casella di controllo **Configura per HTTPS** della finestra di dialogo Nuovo progetto è selezionata, il *Dockerfile* espone due porte. Una porta viene usata per il traffico HTTP e l'altra viene usata per il traffico HTTPS. Se la casella di controllo non è selezionata, viene esposta una sola porta (80) per il traffico HTTP.

## <a name="debug"></a>Debug

Selezionare **Docker** nell'elenco a discesa Debug nella barra degli strumenti e avviare il debug dell'app. È possibile che venga visualizzato un messaggio in cui viene richiesto di considerare attendibile un certificato; scegliere di considerare attendibile il certificato per continuare.

L'opzione **Strumenti contenitore** nella finestra **Output** mostra le azioni in corso. La prima volta, potrebbe richiedere un po 'di tempo per scaricare l'immagine di base, ma è molto più veloce nelle esecuzioni successive.

## <a name="containers-window"></a>Finestra Contenitori

Se si dispone di Visual Studio 2019 versione 16.4 o successiva, è possibile utilizzare la finestra **Contenitori** per visualizzare i contenitori in esecuzione nel computer, nonché le immagini disponibili.

Aprire la finestra **Contenitori** utilizzando la casella di ricerca nell'IDE `container`(premere **CTRL**+**Q** per utilizzarla), digitare e scegliere la finestra **Contenitori** dall'elenco.

È possibile montare la finestra **Contenitori** in una posizione comoda, ad esempio sotto l'editor, spostandola e seguendo le guide di posizionamento della finestra.

Nella finestra individuare il contenitore e scorrere ogni scheda per visualizzare le variabili di ambiente, i mapping delle porte, i log e il file system.

![Schermata della finestra Contenitori](../../media/overview/vs-2019/container-tools-window.png)

Per ulteriori informazioni, vedere [Visualizzare e diagnosticare contenitori e immagini in Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Pubblicare immagini Docker

Al termine del ciclo di sviluppo e debug dell'app, è possibile creare un'immagine di produzione dell'app.

1. Selezionare **Versione** nell'elenco a discesa della configurazione ed eseguire l'app.
1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
1. Nella finestra di dialogo Destinazione di pubblicazione, selezionare la scheda **Registro contenitori**.
1. Scegliere **Crea nuovo Registro Azure Container** e fare clic su **Pubblica**.
1. Inserire i valori desiderati in **Creare un nuovo Registro Azure Container**.

    | Impostazione      | Valore consigliato  | Descrizione                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefisso DNS** | Nome globalmente univoco | Nome che identifica in modo univoco il registro contenitori. |
    | **Sottoscrizione** | Scegliere la sottoscrizione | Sottoscrizione di Azure da usare. |
    | **[Gruppo di risorse](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nome del gruppo di risorse in cui creare il registro contenitori. Per creare un nuovo gruppo di risorse scegliere **Nuovo**.|
    | **[Sku](/azure/container-registry/container-registry-skus)** | Standard | Livello di servizio del registro contenitori  |
    | **Percorso del registro** | Un percorso vicino | Scegliere un Percorso in una [regione](https://azure.microsoft.com/regions/) nelle vicinanze o vicino ad altri servizi usati nel registro contenitori. |

    ![Finestra di dialogo Creare un'istanza di Registro Azure Container di Visual Studio][0]

1. Fare clic su **Crea**

   ![Screenshot che indica l'esito positivo della pubblicazione](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Passaggi successivi

È possibile ora eseguire il pull del contenitore dal registro a qualsiasi host in grado di eseguire immagini Docker, ad esempio [Istanze di Azure Container ](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
