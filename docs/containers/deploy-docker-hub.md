---
title: Distribuzione di un contenitore Docker di base di ASP.NET in Docker Hub. Documenti Microsoft
description: Informazioni su come usare Visual Studio Container Tools per distribuire un'app Web ASP.NET Core in Docker Hub
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: b033825bbe8facbeae3dcdee6a5b563461921522
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188755"
---
# <a name="deploy-to-docker-hub"></a>Distribuire in Docker Hub

Docker Hub fornisce un comodo servizio di hosting per i repository di immagini. È possibile distribuire facilmente a Docker Hub manualmente da Visual Studio.You can easily deploy to Docker Hub manually from Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Creare un account Docker e un repository Docker HubCreate a Docker account and Docker Hub repository

[Registrati](https://hub.docker.com/signup) per ottenere un account Docker, se non ne hai già uno.

Se non si dispone di un repository Docker Hub, crearne uno in [Docker Hub](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Pubblicare l'immagine per un singolo progetto in Docker Hub

1. Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Pubblica...**. Viene visualizzata una schermata che mostra le opzioni di distribuzione.

   ![](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. In **Selezionare una destinazione di pubblicazione**scegliere Registro di sistema **contenitori**, quindi **Docker Hub**. Viene visualizzata la finestra di dialogo **Hub Docker** THe.

   ![](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Se ci si connette al proprio repository (non fa parte di un'organizzazione), lasciare selezionata la casella di controllo Pubblica in **un repository personale.** Se il repository è di proprietà di un'organizzazione, deselezionare la casella di controllo e immettere il nome dell'organizzazione. Immettere il nome utente e la password Docker per l'account Docker che dispone delle autorizzazioni per accedere al repository a cui ci si connette e quindi selezionare **Salva**.  

   Visual Studio tenta di distribuire l'immagine nell'hub Docker.  In caso di esito positivo, viene visualizzata la schermata **Pubblica** con l'URL dell'immagine del repository, il tag dell'immagine, il repository e la configurazione di compilazione, ad esempio **Release**.

   ![](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. È possibile aggiornare l'immagine in qualsiasi momento facendo clic sul pulsante **Pubblica** in questa pagina.  In alternativa, è possibile modificare o rimuovere il profilo utilizzando i collegamenti sotto l'URL.

## <a name="next-steps"></a>Passaggi successivi

Pubblicare nel Registro di [sistema del contenitore](/azure/container-registry/) di Azure seguendo la procedura descritta in Deploy to Azure Container [Registry](hosting-web-apps-in-docker.md).

Configurare l'integrazione e la distribuzione continue (CI/CD) con le pipeline di [Azure.](/azure/devops/pipelines/?view=azure-devops)

## <a name="see-also"></a>Vedere anche

[Eseguire la distribuzione in Azure App Service](deploy-app-service.md)
[Visual Studio Container Tools](/visualstudio/containers/).