---
title: Eseguire la pubblicazione nel servizio app di Azure
description: È possibile usare lo strumento Pubblica per la pubblicazione di app ASP.NET Core in Servizio app di Azure.
ms.date: 01/17/2019
helpviewer_keywords:
- deployment, website
ms.assetid: 8524a4c5-97a9-41ac-a2a0-034efb9bfc57
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.custom: video
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: 29118ac1526aaa7a8c3790de8b519e8ec131a7f682e46e187f303d25535e0653
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121313666"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Pubblicare un'app Web in Servizio app di Azure usando Visual Studio per Mac

È possibile usare lo strumento Pubblica per la pubblicazione di app ASP.NET Core in Servizio app di Azure.

## <a name="prerequisites"></a>Prerequisiti

- [Visual Studio 2017 per Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) installato con ASP.NET Core abilitato.
- Una sottoscrizione di Azure. Se non si ha già una sottoscrizione, [iscriversi gratuitamente](https://azure.microsoft.com/free/dotnet/) per ottenere un credito di $200 per 30 giorni e 12 mesi di accesso ai servizi gratuiti più diffusi.
- Un progetto ASP.NET Core. Se non si ha già un progetto, è possibile [crearne uno](./create-new-projects.md?view=vsmac-2017&preserve-view=true).

## <a name="publish-to-azure-app-service"></a>Eseguire la pubblicazione nel servizio app di Azure

 1. Nel riquadro della soluzione fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

    ![Menu di scelta rapida per la pubblicazione](media/publish-context-menu.png)

 2. Se in precedenza il progetto è stato pubblicato in Servizio app di Azure, il profilo di pubblicazione sarà visualizzato nel menu. Selezionare il profilo di pubblicazione per avviare il processo di pubblicazione.

 3. Per pubblicare il progetto in un servizio app per la prima volta, selezionare **Pubblica in Azure**

    ![Menu di scelta rapida per la pubblicazione in un servizio app](media/publish-to-azure-context-menu.png)

 4. Viene visualizzata la finestra di dialogo **Pubblica in Servizi app di Azure** e vengono visualizzati tutti i servizi app esistenti. Per eseguire la pubblicazione in un servizio app esistente, selezionarlo dall'elenco e fare clic su **Pubblica**.

    ![Finestra di dialogo Pubblica in Servizi app di Azure](media/publish-to-app-service-dialog.png)

 5. Per creare un nuovo servizio app, fare clic sul pulsante **Nuovo**.

    ![Finestra di dialogo Pubblica in Servizi app di Azure](media/publish-to-app-service-dialog-new-selected.png)

 6. Viene visualizzata la finestra di dialogo **Nuovo servizio app**. In questa finestra di dialogo è possibile configurare le impostazioni per il nuovo servizio app.

    ![Finestra di dialogo Nuovo servizio app](media/publish-new-app-service.png)

    Alcune opzioni incluse nella finestra sono personalizzabili. Per impostazione predefinita, il nome del servizio app deriva dal nome del progetto. Se il nome non è disponibile, viene visualizzato un simbolo di avviso a destra del campo di input. Il nome del servizio app verrà usato nell'URL del sito Web quindi deve trattarsi di un nome idoneo a tale scopo.

    È possibile modificare la sottoscrizione cui il servizio app sarà associato usando l'elenco a discesa **Sottoscrizione**.

    È possibile selezionare un **Gruppo di risorse** esistente usando l'elenco a discesa oppure è possibile crearne uno nuovo con il pulsante **+**.

    Per il piano di servizio app, selezionarne uno esistente o crearne uno nuovo selezionando il pulsante di opzione **Person.**

    Per creare il nuovo servizio app e pubblicarvi il progetto, fare clic su **Crea**.

    Dopo aver fatto clic su **Crea**, la finestra di dialogo **Nuovo servizio app** viene chiusa e viene visualizzato il messaggio seguente che indica che la creazione del servizio app è stata avviata.

      ![Messaggio di creazione del servizio app](media/publish-create-app-service-message.png)

    Fare clic su **OK** per ignorare il messaggio e continuare a lavorare sul progetto. È possibile controllare lo stato del processo di pubblicazione con la barra di stato nella parte superiore dell'IDE. Una volta completata la pubblicazione dell'app Web, il sito viene aperto con il browser predefinito.

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]