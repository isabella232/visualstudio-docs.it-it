---
title: Eseguire la pubblicazione nel servizio app di Azure
description: Informazioni sui metodi per pubblicare ASP.NET, ASP.NET Core, Node.js e .NET Core in Servizio app di Azure o Servizio app di Azure Linux.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- azure
ms.openlocfilehash: 53c14db342e48ceccc7651220ac86c8bcacedcf3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146277"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Eseguire la pubblicazione di un'app Web in Servizio app di Azure con Visual Studio

Per le app ASP.NET, ASP.NET Core, Node.js e .NET Core, pubblicare nel servizio app di Azure o nel servizio app di Azure per Linux (tramite i contenitori) usando uno dei metodi seguenti.

* Per una distribuzione di app continua o automatica, usare Azure DevOps con [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).

* Per la distribuzione una sola volta (o  manuale) delle app, usare lo strumento Pubblica in Visual Studio per distribuire app ASP.NET, ASP.NET Core, Node.js e .NET Core in Servizio app di Azure o nel servizio [app per Linux](../deployment/quickstart-deploy-to-linux.md) (usando contenitori). Per le app Python seguire i passaggi in [Python - Eseguire la pubblicazione nel servizio app di Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

Questo articolo descrive come usare lo strumento **Pubblica** per una distribuzione singola.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service-on-windows"></a>Pubblicare in Servizio app di Azure in Windows

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Pubblica** oppure usare la **voce di** menu  >  **Compila** pubblicazione.

    ![Comando Pubblica nel menu di scelta rapida del progetto in Esplora soluzioni](../deployment/media/quickstart-publish.png "Scegliere Pubblica")

1. Se in precedenza sono stati configurati profili di pubblicazione, viene **visualizzata la finestra** Pubblica. Selezionare **Nuovo**.

1. Nella finestra **Pubblica** selezionare **Azure**.

    ![Scegliere la destinazione di pubblicazione](../deployment/media/quickstart-publish-azure-new.png)

1. Selezionare **Servizio app di Azure (Windows) e** **Avanti.**

    ![Scegliere Servizio app di Azure in Linux](../deployment/media/quickstart-publish-windows-select-azure-service.png)

1. Accedere con l'account Azure, se necessario. Selezionare **Crea una nuova Servizio app di Azure...**

    ![Collegamento per creare una nuova istanza di Servizio app di Azure](../deployment/media/quickstart-publish-windows-create-new-link.png)

1. Nella finestra **di dialogo Servizio app di Azure (Windows)** vengono popolati i campi  Nome **app,** Gruppo di risorse e Piano di servizio app. È possibile mantenere questi nomi o modificarli. Al termine, selezionare **Crea**.

    ![Screenshot della finestra di dialogo Servizio app di Azure (Windows) con i campi Nome, Sottoscrizione, Gruppo di risorse e Piano di hosting popolati.](../deployment/media/quickstart-publish-windows-create-new-dialog.png)

1. Nella finestra **di dialogo** Pubblica l'istanza appena creata è stata selezionata automaticamente. Al termine, selezionare **Fine.**

    ![Screenshot della finestra Pubblica accessibile da Visual Studio Esplora soluzioni. Azure è selezionato come destinazione di pubblicazione.](../deployment/media/quickstart-publish-windows-select-instance.png)

1. Selezionare **Pubblica**. Visual Studio distribuisce l'app al Servizio app di Azure e l'app Web viene caricata nel browser. Nel riquadro **Pubblica** delle proprietà del progetto viene visualizzato l'URL del sito con altri dettagli.

    ![Riquadro Pubblica delle proprietà con il riepilogo di un profilo](../deployment/media/quickstart-publish-windows-summary-page.png)

## <a name="clean-up-resources"></a>Pulire le risorse

Nei passaggi precedenti sono state create risorse di Azure in un gruppo di risorse. Se non si prevede di aver bisogno di queste risorse in futuro, è possibile eliminarle eliminando il gruppo di risorse.
Dal menu a sinistra nel portale di Azure scegliere **Gruppi di risorse** e quindi selezionare **myResourceGroup**.
Nella pagina del gruppo di risorse assicurarsi che le risorse elencate siano quelle da eliminare.
Selezionare **Elimina**, digitare **myResourceGroup** nella casella di testo e quindi selezionare **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato descritto come usare Visual Studio per creare un profilo di pubblicazione per la distribuzione in Azure. È anche possibile configurare un profilo di pubblicazione importando le impostazioni di pubblicazione da Servizio app di Azure.

> [!div class="nextstepaction"]
> [Importare impostazioni di pubblicazione e distribuzione in Azure](tutorial-import-publish-settings-azure.md)
