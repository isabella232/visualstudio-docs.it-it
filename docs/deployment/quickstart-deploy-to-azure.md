---
title: Eseguire la pubblicazione nel servizio app di Azure
ms.date: 06/22/2018
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: 4e7cf13658c33caf6b58d6a4e661a8431f377845
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853593"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Eseguire la pubblicazione di un'app Web in Servizio app di Azure con Visual Studio

È possibile usare lo strumento **Pubblica** per la pubblicazione di app ASP.NET, ASP.NET Core, Node.js e .NET Core nel Servizio app di Azure o nel Servizio app di Azure per Linux (con contenitori). Per le app Python seguire i passaggi in [Python - Eseguire la pubblicazione nel servizio app di Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Eseguire la pubblicazione nel servizio app di Azure

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica** o usare la voce di menu **Compila** > **Pubblica**.

    ![Il comando Pubblica nel menu di scelta rapida del progetto in Esplora soluzioni](../deployment/media/quickstart-publish.png "scegliere Pubblica")

1. Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. In questo caso, selezionare **Crea nuovo profilo**.

1. Nella finestra di dialogo **Selezionare una destinazione di pubblicazione** fare clic su **Servizio app**.

    ![Scegliere Servizio app di Azure](../deployment/media/quickstart-publish-azure.png "Scegliere Servizio app di Azure")

1. Selezionare **Pubblica**. Viene visualizzata la finestra di dialogo **Crea servizio app**. Accedere con l'account Azure, se necessario. Le impostazioni predefinite del Servizio app popolano i campi.

    ![Crea Servizio app](../deployment/media/quickstart-publish-settings-app-service.png "Crea Servizio app di Azure")

1. Scegliere **Crea**. Visual Studio distribuisce l'app al Servizio app di Azure e l'app Web viene caricata nel browser. Nel riquadro **Pubblica** delle proprietà del progetto viene visualizzato l'URL del sito con altri dettagli.

    ![Riquadro Pubblica delle proprietà con il riepilogo di un profilo](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Pulire le risorse

Nei passaggi precedenti, sono state create delle risorse di Azure in un gruppo di risorse. Se non si prevede di usare queste in futuro, è possibile eliminarle eliminando il gruppo di risorse.
Nel menu a sinistra nel portale di Azure selezionare **Gruppi di risorse** e quindi selezionare **myResourceGroup**.
Nella pagina del gruppo di risorse assicurarsi che le risorse elencate siano quelle da eliminare.
Selezionare **Elimina**, digitare **myResourceGroup** nella casella di testo e quindi selezionare **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato descritto come usare Visual Studio per creare un profilo di pubblicazione per la distribuzione in Azure. È anche possibile configurare un profilo di pubblicazione importando le impostazioni di pubblicazione da Servizio app di Azure.

> [!div class="nextstepaction"]
> [Importare impostazioni di pubblicazione e distribuzione in Azure](tutorial-import-publish-settings-azure.md)
