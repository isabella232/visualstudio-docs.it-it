---
title: Eseguire la pubblicazione nel servizio app di Azure
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: a8de7175b33a91c310da4b3d6d9e4c05c40c3522
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341690"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Pubblicare un'app Web nel servizio App di Azure con Visual Studio

È possibile usare la **pubblica** dello strumento per la pubblicazione di App ASP.NET, ASP.NET Core, Node. js e .NET Core in servizio App di Azure o il servizio App di Azure Linux (con contenitori). Per le app di Python, seguire i passaggi sullo [Python - pubblicazione in servizio App di Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Eseguire la pubblicazione nel servizio app di Azure

1. In Esplora soluzioni fare clic sul progetto e scegliere **Publish** (o utilizzare il **compilare** > **pubblica** voce di menu).

    ![Il comando Pubblica nel menu di scelta rapida progetto in Esplora soluzioni](../deployment/media/quickstart-publish.png "scegliere pubblica")

1. Se sono stati configurati tutti i profili di pubblicazione, il **Publish** viene visualizzato il riquadro, in cui selezionare case **Crea nuovo profilo**.

1. Nel **selezionare una destinazione di pubblicazione** finestra di dialogo, scegliere **servizio App**.

    ![Scegliere servizio App di Azure](../deployment/media/quickstart-publish-azure.png "scegliere servizio App di Azure")

1. Selezionare **Pubblica**. Il **Crea servizio App** verrà visualizzata la finestra di dialogo. Accedere con è account Azure, se necessario, quindi le impostazioni predefinite del servizio app popolano i campi.

    ![Crea servizio App](../deployment/media/quickstart-publish-settings-app-service.png "Crea servizio App di Azure")

1. Scegliere **Crea**. Visual Studio distribuisce l'app in servizio App di Azure e carica l'app web nel browser. Le proprietà del progetto **pubblica** riquadro viene visualizzato l'URL del sito e altri dettagli.

    ![Riquadro delle proprietà con il riepilogo un profilo di pubblicazione](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Pulire le risorse

Creato nei passaggi precedenti, le risorse di Azure in un gruppo di risorse. Se non si prevede di queste risorse sono necessarie in futuro, è possibile eliminarle eliminando il gruppo di risorse.
Nel menu a sinistra nel portale di Azure, selezionare **gruppi di risorse** e quindi selezionare **myResourceGroup**.
Nella pagina di gruppo di risorse, assicurarsi che le risorse elencate siano quelle da eliminare.
Selezionare **eliminare**, digitare **myResourceGroup** nella casella di testo e quindi selezionare **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

In questa Guida introduttiva è stato descritto come usare Visual Studio per creare un profilo di pubblicazione per la distribuzione in Azure. È anche possibile configurare una pubblicazione mediante l'importazione profilo impostazioni di pubblicazione da servizio App di Azure.

> [!div class="nextstepaction"]
> [Importare impostazioni di pubblicazione e distribuzione in Azure](tutorial-import-publish-settings-azure.md)
