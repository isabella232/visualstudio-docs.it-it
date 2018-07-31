---
title: Pubblicare nel servizio App in Linux
ms.custom: ''
ms.date: 07/23/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: aa4afce6ef50284f1f966054e805b55c86f4daaf
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341748"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Pubblicare un'app ASP.NET Core in servizio App in Linux tramite Visual Studio

È possibile usare la **pubblica** dello strumento per la pubblicazione delle App ASP.NET Core in servizio App di Azure in Linux.

Distribuzione nel servizio App in Linux mediante il **pubblica** lo strumento richiede Visual Studio 2017 versione 15.7.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Pubblicare nel servizio App in Linux

1. In Esplora soluzioni fare clic sul progetto e scegliere **Publish** (o utilizzare il **compilare** > **pubblica** voce di menu).

    ![Il comando Pubblica nel menu di scelta rapida progetto in Esplora soluzioni](../deployment/media/quickstart-publish.png "scegliere pubblica")

1. Se sono stati configurati tutti i profili di pubblicazione, il **Publish** viene visualizzato il riquadro, in cui selezionare case **Crea nuovo profilo**.

1. Nel **selezionare una destinazione di pubblicazione** finestra di dialogo, scegliere **servizio App Linux**.

    ![Scegliere servizio App di Azure](../deployment/media/quickstart-publish-linux.png "scegliere servizio App di Azure")

1. Selezionare **Pubblica**. Il **Crea servizio App** verrà visualizzata la finestra di dialogo. Accedere con è account Azure, se necessario, quindi le impostazioni predefinite del servizio app popolano i campi.

    ![Crea servizio App](../deployment/media/quickstart-publish-settings-app-service-linux.png "Crea servizio App di Azure")

1. Scegliere **Crea**. Visual Studio distribuisce l'app in servizio App di Azure e carica l'app web nel browser. Le proprietà del progetto **pubblica** riquadro viene visualizzato l'URL del sito e altri dettagli.

    ![Riquadro delle proprietà con il riepilogo un profilo di pubblicazione](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Pulire le risorse

Creato nei passaggi precedenti, le risorse di Azure in un gruppo di risorse. Se non si prevede di queste risorse sono necessarie in futuro, è possibile eliminarle eliminando il gruppo di risorse.
Nel menu a sinistra nel portale di Azure, selezionare **gruppi di risorse** e quindi selezionare **myResourceGroup**.
Nella pagina di gruppo di risorse, assicurarsi che le risorse elencate siano quelle da eliminare.
Selezionare **eliminare**, digitare **myResourceGroup** nella casella di testo e quindi selezionare **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

In questa Guida introduttiva è stato descritto come usare Visual Studio per creare un profilo di pubblicazione per la distribuzione in servizio App in Linux. È possibile altre informazioni sulla pubblicazione in Linux tramite Azure.

> [!div class="nextstepaction"]
> [Servizio app di Linux](/azure/app-service/containers/app-service-linux-intro)
