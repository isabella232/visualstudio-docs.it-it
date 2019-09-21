---
title: Distribuire un contenitore Docker ASP.NET Core nell'hub Docker | Microsoft Docs
description: Informazioni su come usare gli strumenti del contenitore di Visual Studio per distribuire un'app Web di ASP.NET Core nell'hub Docker
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: 267e0c1ed1ac3911aad2161f186bf4a482f069b6
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "70312238"
---
# <a name="deploy-to-docker-hub"></a>Distribuire in Docker Hub

Docker Hub fornisce un servizio di hosting pratico per i repository di immagini. È possibile eseguire facilmente la distribuzione nell'hub Docker manualmente da Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Creare un account Docker e un repository Docker Hub

[Iscriversi](https://hub.docker.com/signup) per ottenere un account Docker, se non ne è già presente uno.

Se non si dispone di un repository Docker Hub, crearne uno nell' [Hub Docker](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Pubblicare l'immagine per un singolo progetto nell'hub Docker

1. Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **pubblica...** . Verrà visualizzata una schermata che mostra le opzioni di distribuzione.

   ![](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. In **selezionare una destinazione di pubblicazione**scegliere **container Registry**, quindi scegliere **Hub Docker**. Verrà visualizzata la finestra di dialogo **Hub Docker** .

   ![](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Se ci si connette al proprio repository (non appartenente a un'organizzazione), lasciare selezionata la casella di controllo per la **pubblicazione in un repository personale** . Se il repository è di proprietà di un'organizzazione, deselezionare la casella di controllo e immettere il nome dell'organizzazione. Immettere il nome utente e la password di Docker per l'account Docker con le autorizzazioni per accedere al repository a cui ci si connette e quindi selezionare **Save (Salva**).  

   Visual Studio tenta di distribuire l'immagine nell'hub docker.  In caso di esito positivo, viene visualizzata la schermata di **pubblicazione** con l'URL dell'immagine del repository, il tag dell'immagine, il repository e la configurazione della build * * (ad esempio, **Release**).

   ![](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. È possibile aggiornare l'immagine in qualsiasi momento facendo clic sul pulsante **pubblica** in questa pagina.  In alternativa, è possibile modificare o rimuovere il profilo usando i collegamenti sotto l'URL.

## <a name="next-steps"></a>Passaggi successivi

Eseguire la pubblicazione in [azure container Registry](/azure/container-registry/) attenendosi alla procedura illustrata in [distribuire in Azure container Registry](vs-azure-tools-docker-hosting-web-apps-in-docker.md).

Configurare l'integrazione e il recapito continui con [Azure Pipelines](/azure/devops/pipelines/?view=azure-devops).

## <a name="see-also"></a>Vedere anche

[Eseguire la distribuzione nel servizio](deploy-app-service.md)
app Azure[strumenti contenitore di Visual Studio](/visualstudio/containers/).