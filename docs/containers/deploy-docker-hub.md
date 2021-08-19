---
title: Distribuire un ASP.NET Core Docker in Docker Hub | Microsoft Docs
description: Informazioni su come usare Visual Studio Container Tools per distribuire un ASP.NET Core app Web Docker Hub
author: ghogen
manager: jmartens
ms.technology: vs-container-tools
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 2fe4c9a1ac39ed090eae657c02ea8417002a2473
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059333"
---
# <a name="deploy-to-docker-hub"></a>Distribuire in Docker Hub

Docker Hub un comodo servizio di hosting per i repository di immagini. È possibile eseguire facilmente la distribuzione in Docker Hub manualmente da Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Creare un account Docker e Docker Hub repository

[Iscriversi per](https://hub.docker.com/signup) un account Docker, se non se ne ha già uno.

Se non si ha un repository Docker Hub, crearne uno [in Docker Hub](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Pubblicare l'immagine per un singolo progetto in Docker Hub

1. Fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Pubblica...**. Viene visualizzata una schermata che mostra le opzioni di distribuzione.

   ![Screenshot delle opzioni di distribuzione](media/container-tools/vs-2019/docker-container-registry.png)

1. Scegliere **Registro Contenitori Docker** e quindi scegliere **Docker Hub**.

   ![Screenshot della finestra di dialogo Pubblica: scegliere Docker Hub](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Immettere le credenziali di Docker.

   ![Screenshot della finestra Docker Hub dialogo](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Se ci si connette al proprio repository (non fa parte di un'organizzazione), lasciare selezionata la casella di controllo Pubblica in **un repository** personale. Se il repository è di proprietà di un'organizzazione, deselezionare la casella di controllo e immettere il nome dell'organizzazione. Immettere il nome utente e la password Docker per l'account Docker che dispone delle autorizzazioni per accedere al repository a cui ci si connette e quindi selezionare **Salva**.

   Visual Studio tenta di distribuire l'immagine nel Docker Hub.  In caso  di esito positivo, viene visualizzata la schermata Pubblica con l'URL per l'immagine del repository, il tag dell'immagine, il repository e la configurazione della compilazione , ad esempio **Release**.

   ![Screenshot della schermata Pubblica](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. È possibile aggiornare l'immagine in qualsiasi momento facendo clic sul **pulsante** Pubblica in questa pagina.  In caso contrario, è possibile modificare o rimuovere il profilo usando i collegamenti sotto l'URL.

## <a name="next-steps"></a>Passaggi successivi

Pubblicare [in Registro Azure Container](/azure/container-registry/) seguendo la procedura descritta in Distribuire in [Registro Azure Container](hosting-web-apps-in-docker.md).

Configurare l'integrazione continua e il recapito (CI/CD) [con Azure Pipelines](/azure/devops/pipelines/?view=azure-devops&preserve-view=true).

## <a name="see-also"></a>Vedi anche

[Distribuire in Servizio app di Azure](deploy-app-service.md) 
 [Visual Studio Container Tools](./index.yml).