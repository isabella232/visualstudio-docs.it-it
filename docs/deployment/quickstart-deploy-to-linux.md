---
title: Eseguire la pubblicazione nel Servizio app in Linux
description: Informazioni sui metodi per pubblicare ASP.NET Core app in Servizio app di Azure Linux usando contenitori, incluse opzioni continue e una sola volta.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- azure
ms.openlocfilehash: 62ff5d26fe426055be88d8a3c28edbd06118f599
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080403"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Eseguire la pubblicazione di un'app ASP.NET Core nel Servizio app in Linux con Visual Studio

A partire da Visual Studio 2017 versione 15.7 è possibile pubblicare le app ASP.NET Core nel servizio app di Azure per Linux (tramite i contenitori) usando uno dei metodi seguenti.

* Per una distribuzione di app continua o automatica, usare Azure DevOps con [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).

* Per una distribuzione delle app singola (o manuale), usare lo strumento **Pubblica** in Visual Studio per pubblicare le app ASP.NET Core nel servizio app per Linux (tramite i contenitori).

Questo articolo descrive come usare lo strumento **Pubblica** per una distribuzione singola.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-azure-app-service-on-linux"></a>Pubblicare in Servizio app di Azure in Linux

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica** o usare la voce di menu **Compila** > **Pubblica**.

    ![Comando Pubblica nel menu di scelta rapida del progetto in Esplora soluzioni](../deployment/media/quickstart-publish.png "Scegliere Pubblica")

1. Se in precedenza sono stati configurati profili di pubblicazione, viene **visualizzata la finestra** Pubblica. Selezionare **Nuovo**.

1. Nella finestra **Pubblica** selezionare **Azure.**

    ![Scegliere la destinazione di pubblicazione](../deployment/media/quickstart-publish-azure-new.png)

1. Selezionare **Servizio app di Azure (Linux) e** **Avanti.**

    ![Scegliere Servizio app di Azure in Linux](../deployment/media/quickstart-publish-linux-select-azure-service.png)

1. Se necessario, accedere con l'account Azure. Selezionare **Crea una nuova Servizio app di Azure...**

    ![Collegamento per creare una nuova istanza di Servizio app di Azure](../deployment/media/quickstart-publish-linux-create-new-link.png)

1. Nella finestra **di dialogo Servizio app di Azure (Linux)** vengono popolati i campi **Nome app,** Gruppo di risorse e Piano **di** servizio app. È possibile mantenere questi nomi o modificarli. Quando si è pronti, selezionare **Crea.**

    ![Screenshot della finestra di dialogo Servizio app di Azure (Linux) con i campi Nome, Sottoscrizione, Gruppo di risorse e Piano di hosting popolati.](../deployment/media/quickstart-publish-linux-create-new-dialog.png)

1. Nella finestra **di dialogo** Pubblica l'istanza appena creata è stata selezionata automaticamente. Quando si è pronti, fare clic **su Fine.**

    ![Screenshot della finestra di dialogo Pubblica con il servizio MyASpCoreWebAppOnAzure appena creato selezionato come servizio app per la pubblicazione.](../deployment/media/quickstart-publish-linux-select-instance.png)

1. Selezionare **Pubblica**. Visual Studio distribuisce l'app al Servizio app di Azure e l'app Web viene caricata nel browser. Nel riquadro **Pubblica** delle proprietà del progetto viene visualizzato l'URL del sito con altri dettagli.

    ![Riquadro Pubblica delle proprietà con il riepilogo di un profilo](../deployment/media/quickstart-publish-linux-summary-page.png)

## <a name="clean-up-resources"></a>Pulire le risorse

Nei passaggi precedenti sono state create risorse di Azure in un gruppo di risorse. Se non si prevede di aver bisogno di queste risorse in futuro, è possibile eliminarle eliminando il gruppo di risorse.
Dal menu a sinistra nel portale di Azure scegliere **Gruppi di risorse** e quindi selezionare **myResourceGroup**.
Nella pagina del gruppo di risorse assicurarsi che le risorse elencate siano quelle da eliminare.
Selezionare **Elimina**, digitare **myResourceGroup** nella casella di testo e quindi selezionare **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato descritto come usare Visual Studio per creare un profilo di pubblicazione per la distribuzione nel Servizio app in Linux. Sono disponibili altre informazioni per la pubblicazione in Linux tramite Azure.

> [!div class="nextstepaction"]
> [Servizio app di Linux](/azure/app-service/containers/app-service-linux-intro)