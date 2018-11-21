---
title: Eseguire la pubblicazione nel Servizio app in Linux
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
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341748"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Eseguire la pubblicazione di un'app ASP.NET Core nel Servizio app in Linux con Visual Studio

È possibile usare lo strumento **Pubblica** per la pubblicazione di app ASP.NET Core nel Servizio app di Azure in Linux.

La distribuzione nel Servizio app in Linux mediante lo strumento **Pubblica** richiede Visual Studio 2017 versione 15.7.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Eseguire la pubblicazione nel Servizio app in Linux

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica** o usare la voce di menu **Compila** > **Pubblica**.

    ![Il comando Pubblica nel menu di scelta rapida del progetto in Esplora soluzioni](../deployment/media/quickstart-publish.png "scegliere Pubblica")

1. Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. In questo caso, selezionare **Crea nuovo profilo**.

1. Nella finestra di dialogo **Selezionare una destinazione di pubblicazione** fare clic su **Servizio app per Linux**.

    ![Scegliere Servizio app di Azure](../deployment/media/quickstart-publish-linux.png "Scegliere Servizio app di Azure")

1. Selezionare **Pubblica**. Viene visualizzata la finestra di dialogo **Crea servizio app**. Accedere con l'account Azure, se necessario. Le impostazioni predefinite del Servizio app popolano i campi.

    ![Crea Servizio app](../deployment/media/quickstart-publish-settings-app-service-linux.png "Crea Servizio app di Azure")

1. Scegliere **Crea**. Visual Studio distribuisce l'app al Servizio app di Azure e l'app Web viene caricata nel browser. Nel riquadro **Pubblica** delle proprietà del progetto viene visualizzato l'URL del sito con altri dettagli.

    ![Riquadro Pubblica delle proprietà con il riepilogo di un profilo](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Pulire le risorse

Nei passaggi precedenti, sono state create delle risorse di Azure in un gruppo di risorse. Se non si prevede di usare queste in futuro, è possibile eliminarle eliminando il gruppo di risorse.
Nel menu a sinistra nel portale di Azure selezionare **Gruppi di risorse** e quindi selezionare **myResourceGroup**.
Nella pagina del gruppo di risorse assicurarsi che le risorse elencate siano quelle da eliminare.
Selezionare **Elimina**, digitare **myResourceGroup** nella casella di testo e quindi selezionare **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato descritto come usare Visual Studio per creare un profilo di pubblicazione per la distribuzione nel Servizio app in Linux. Sono disponibili altre informazioni per la pubblicazione in Linux tramite Azure.

> [!div class="nextstepaction"]
> [Servizio app di Linux](/azure/app-service/containers/app-service-linux-intro)
