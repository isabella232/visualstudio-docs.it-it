---
title: Introduzione a Docker
description: Informazioni su come aggiungere Docker ai progetti in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.topic: how-to
ms.openlocfilehash: 4ddb15c8bc5bf90663c5431d2379af61b43e73a6
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043094"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Introduzione a Docker in Visual Studio per Mac

Con Visual Studio per Mac è possibile creare, eseguire ed effettuare il debug di app ASP.NET Core in contenitori e pubblicarle in Azure.

## <a name="prerequisites"></a>Prerequisiti

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio per Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Installazione e configurazione

Per l'installazione di Docker, rivedere e seguire le informazioni riportate in [Install Docker Desktop for Mac](https://docs.docker.com/docker-for-mac/install/) (Installare Docker Desktop per Mac).

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>Creazione di un'applicazione Web ASP.NET Core e aggiunta del supporto Docker

1. Creare una nuova soluzione selezionando **File > Nuova soluzione**.
1. In **.NET Core > app** scegliere il modello Applicazione **Web:** ![ Crea una nuova ASP.NET applicazione](media/docker-quickstart-1.png)
1. Selezionare il framework di destinazione. In questo esempio si userà .NET Core 2.2: ![ Impostare il framework di destinazione](media/docker-quickstart-2.png)
1. Immettere i dettagli del progetto, tra cui il nome (in questo esempio, _DockerDemo_). Il progetto creato contiene tutte le informazioni di base necessarie per compilare ed eseguire un sito Web ASP.NET Core.
1. Nella finestra della soluzione fare clic con il pulsante destro del mouse sul progetto DockerDemo e scegliere > Aggiungi supporto **Docker:** ![ Aggiungi supporto Docker](media/docker-quickstart-3.png)

Visual Studio per Mac aggiungerà automaticamente alla soluzione un nuovo progetto denominato **docker-compose** e un **Dockerfile** al progetto esistente.

![File di supporto Docker generati](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Panoramica dei Dockerfile

Un Dockerfile è il file recipe per la creazione di un'immagine Docker finale. Per informazioni sui comandi al suo interno, fare riferimento a [Dockerfile](https://docs.docker.com/engine/reference/builder/) reference (Informazioni di riferimento su Dockerfile).

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore "DockerDemo/DockerDemo.csproj"
COPY . .
WORKDIR "/src/DockerDemo"
RUN dotnet build "DockerDemo.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "DockerDemo.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

Il *Dockerfile* precedente è basato sull'immagine [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) e include le istruzioni per modificare l'immagine di base compilando il progetto e aggiungendolo al contenitore.

> [!NOTE]
> Il Dockerfile predefinito creato da Visual Studio per Mac espone la porta 80 per il traffico HTTP. Per consentire il traffico HTTPS, aggiungere `Expose 443` al Dockerfile.

## <a name="debugging"></a>Debug

Selezionare il progetto `docker-compose` come progetto di avvio e avviare il debug (**Esegui > Avvia debug**). Il progetto ASP.NET verrà compilato, distribuito e avviato in un contenitore.

> [!TIP]
> Quando si esegue per la prima volta Docker Desktop dopo averlo installato, è possibile che venga visualizzato l'errore seguente durante il tentativo di eseguire il debug: `Cannot start service dockerdemo: Mounts denied`
>
> Aggiunge `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` alla scheda Condivisione file in Docker Desktop:
>
> ![Aggiunta della cartella NuGetFallbackFolder alla condivisione di file](media/docker-quickstart-5.png)

Al termine del processo di compilazione, l'applicazione verrà avviata in Safari:

![Progetto Docker predefinito in esecuzione in Safari](media/docker-quickstart-6.png)

Il contenitore rimarrà in ascolto su una porta, ad esempio `http://localhost:32768`, e questa porta può variare.

Per visualizzare l'elenco dei contenitori in esecuzione, usare il comando `docker ps` nel terminale.

Osservare il valore di inoltro della porta nello screenshot seguente (sotto **PORTS**). Questo valore indica che il contenitore è in ascolto sulla porta specificata in precedenza e che inoltra le richieste al server Web interno sulla porta 80 (come definito nel Dockerfile). L'applicazione, quindi, è in ascolto sulla porta 80:

![Elenco di contenitori Docker](media/docker-quickstart-7.png)
