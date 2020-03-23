---
title: Distribuzione di un contenitore Docker di base di ASP.NET nel servizio app di Azure. Documenti Microsoft
description: Informazioni su come usare Visual Studio Container Tools per distribuire un'app Web di base di Visual Studio nel servizio app di AzureLearn how to use Visual Studio Container Tools to deploy an ASP.NET Core web app to Azure App Service
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 6c1d56f788294826853ad441313597255308bb39
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027296"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Distribuire un contenitore di ASP.NET Core nel servizio app di Azure usando Visual StudioDeploy an ASP.NET Core container to Azure App Service using Visual Studio

Questa esercitazione illustra come usare Visual Studio per pubblicare l'applicazione Web ASP.NET Core in un servizio app di [Azure.](/azure/app-service) Azure App Service is an appropriate service for a single-container web app hosted in Azure.

Se non si ha una sottoscrizione di Azure, creare un [account gratuito](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) prima di iniziare.

## <a name="prerequisites"></a>Prerequisites

Per completare questa esercitazione:

::: moniker range="vs-2017"
- Installare l'ultima versione di [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con il carico di lavoro "Sviluppo ASP.NET e Web"
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro *Sviluppo ASP.NET e Web*.
::: moniker-end
- Installare [Docker Desktop](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Creare un'app Web ASP.NET Core

La procedura seguente illustra la creazione di un'app ASP.NET Core di base che verrà usata in questa esercitazione.

::: moniker range="vs-2017"
1. Nel menu di Visual Studio selezionare **File > Nuovo > Progetto**.
2. Nella sezione **Modelli** della finestra di dialogo **Nuovo progetto** selezionare **Visual C# > Web**.
3. Selezionare **Applicazione Web ASP.NET Core**.
4. Assegnare un nome alla nuova applicazione (o accettare quello predefinito), quindi selezionare **OK**.
5. Selezionare **Applicazione Web**.
6. Spuntare la casella di controllo **Abilita Supporto Docker**.
7. Selezionare il tipo di contenitore **Linux** e fare clic su **OK**. I contenitori di Windows non sono supportati per la distribuzione nel servizio app di Azure come contenitore.
::: moniker-end
::: moniker range=">= vs-2019"
1. Nella finestra iniziale di Visual Studio scegliere **Crea un nuovo progetto**.
1. Scegliere **Applicazione Web ASP.NET Core** e quindi scegliere **Avanti**.
1. Assegnare un nome alla nuova applicazione (o accettare quello predefinito), quindi scegliere **Crea**.
1. Scegliere **Applicazione Web**.
1. Scegliere se si vuole il supporto SSL tramite la casella di controllo **Configura per HTTPS**.
1. Spuntare la casella di controllo **Abilita Supporto Docker**.
1. Selezionare il tipo di contenitore e fare clic su **Crea**. I contenitori di Windows non sono supportati per la distribuzione nel servizio app di Azure come contenitore.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Distribuire il contenitore in AzureDeploy the container to Azure

1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
1. Nella finestra di dialogo Destinazione pubblicazione scegliere **Servizio app Linux** o Servizio **app**. Questo è il sistema operativo che ospiterà il server web.
1. È possibile eseguire la pubblicazione solo nel servizio app oppure nel servizio app e nel Registro di sistema del contenitore di Azure. Per pubblicare il contenitore in un Registro di sistema contenitori di Azure, scegliere **Crea nuovo servizio app per i contenitori**e fare clic su **Pubblica**.

   ![Schermata della finestra di dialogo Pubblica](media/deploy-app-service/publish-app-service-linux.PNG)

   Per pubblicare solo in un servizio app di Azure senza usare il Registro di sistema del contenitore di Azure, scegliere **Crea nuovo**e fare clic su **Pubblica**.

1. Verificare di aver eseguito l'accesso con l'account associato alla sottoscrizione di Azure e scegliere un nome univoco, una sottoscrizione, un gruppo di risorse, un piano di hosting e un registro dei contenitori (se applicabile) oppure accettare le impostazioni predefinite.

   ![Screenshot delle impostazioni di pubblicazione](media/deploy-app-service/publish-app-service-linux2.png)

1. Scegliere **Crea**. Il contenitore viene distribuito in Azure nel gruppo di risorse e nel Registro di sistema del contenitore selezionati. Questo processo richiede un po' di tempo. Al termine, la scheda **Pubblica** mostra informazioni su ciò che è stato pubblicato, incluso l'URL del sito.

   ![Schermata della scheda Pubblica](media/deploy-app-service/publish-succeeded.PNG)

1. Fare clic sul collegamento di sito per verificare che l'app funzioni come previsto in Azure.Click on the site link to verify your app works as expected in Azure.

   ![Schermata dell'applicazione Web](media/deploy-app-service/web-application-running.png)

1. Il profilo di pubblicazione viene salvato con tutti i dettagli selezionati, ad esempio il gruppo di risorse e il registro contenitori.

1. Per eseguire nuovamente la distribuzione con lo stesso profilo di pubblicazione, utilizzare il pulsante **Pubblica,** il pulsante **Pubblica** nella finestra **Attività di pubblicazione Web** oppure fare clic con il pulsante destro del mouse sul progetto in Esplora **soluzioni** e **scegliere** pubblica elemento dal menu di scelta rapida.

## <a name="view-container-settings"></a>Visualizzare le impostazioni del contenitore

Nel [portale](https://portal.azure.com)di Azure è possibile aprire il servizio app distribuito.

È possibile visualizzare le impostazioni per il servizio app distribuito aprendo il menu*delle impostazioni del contenitore* (quando si usa Visual Studio 2019 versione 16.4 o successiva).

![Screenshot del menu Impostazioni contenitore nel portale di Azure](media/deploy-app-service/container-settings-menu.png)

Da qui è possibile visualizzare le informazioni sul contenitore, visualizzare o scaricare i log o configurare la distribuzione continua. Vedere [CI/CD di distribuzione continua](/azure/app-service/containers/app-service-linux-ci-cd)del servizio app di Azure .

## <a name="clean-up-resources"></a>Pulire le risorse

Per rimuovere tutte le risorse di Azure associate a questa esercitazione, eliminare il gruppo di risorse tramite il portale di Azure.To remove all Azure resources associated with this tutorial, delete the resource group using the [Azure portal](https://portal.azure.com). Per trovare il gruppo di risorse associato a un'applicazione Web pubblicata, scegliere **Visualizza** > altre attività di**Pubblicazione Web****Windows** > , quindi scegliere l'icona a forma di ingranaggio. Viene visualizzata la scheda **Pubblica** contenente il gruppo di risorse.

Nel portale di Azure scegliere **Gruppi di**risorse, selezionare il gruppo di risorse per aprire la relativa pagina dei dettagli. Verificare che si tratti del gruppo di risorse corretto, quindi scegliere **Rimuovi gruppo di risorse,** digitare il nome e scegliere **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni su [Azure App Service Linux](/azure/app-service/containers/app-service-linux-intro).

## <a name="see-also"></a>Vedere anche

[Eseguire la distribuzione nel Registro Azure Container](hosting-web-apps-in-docker.md)