---
title: Distribuire un contenitore Docker ASP.NET Core al servizio app Azure | Microsoft Docs
description: Informazioni su come usare gli strumenti del contenitore di Visual Studio per distribuire un'app Web ASP.NET Core al servizio app Azure
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 03/08/2019
ms.author: ghogen
ms.openlocfilehash: 9952ade8cae70b7e542b9de0b9ca36967f3bd8bb
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826561"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Distribuire un contenitore ASP.NET Core al servizio app Azure con Visual Studio

Questa esercitazione illustra l'uso di Visual Studio per pubblicare l'applicazione Web ASP.NET Core in contenitori in un [servizio di app Azure](/azure/app-service). Il servizio app Azure è un servizio appropriato per un'app Web a singolo contenitore ospitata in Azure.

Se non si ha una sottoscrizione di Azure, creare un [account gratuito](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) prima di iniziare.

## <a name="prerequisites"></a>Prerequisiti

Per completare questa esercitazione:

::: moniker range="vs-2017"
- Installare l'ultima versione di [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con il carico di lavoro "Sviluppo ASP.NET e Web"
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro di *sviluppo ASP.NET e Web* .
::: moniker-end
- Installare [Docker desktop](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Creare un'app Web ASP.NET Core

La procedura seguente illustra la creazione di un'app ASP.NET Core di base che verrà usata in questa esercitazione.

::: moniker range="vs-2017"
1. Nel menu di Visual Studio selezionare **File > Nuovo > Progetto**.
2. Nella sezione **Modelli** della finestra di dialogo **Nuovo progetto** selezionare **Visual C# > Web**.
3. Selezionare **Applicazione Web ASP.NET Core**.
4. Assegnare un nome alla nuova applicazione (o accettare quello predefinito), quindi selezionare **OK**.
5. Selezionare **Applicazione Web**.
6. Spuntare la casella di controllo **Abilita Supporto Docker**.
7. Selezionare il tipo di contenitore **Linux** e fare clic su **OK**. I contenitori di Windows non sono supportati per la distribuzione nel servizio app Azure come contenitore.
::: moniker-end
::: moniker range=">= vs-2019"
1. Nella finestra iniziale di Visual Studio scegliere **Crea un nuovo progetto**.
1. Scegliere **Applicazione Web ASP.NET Core** e quindi scegliere **Avanti**.
1. Assegnare un nome alla nuova applicazione (o accettare quello predefinito), quindi scegliere **Crea**.
1. Scegliere **Applicazione Web**.
1. Scegliere se si vuole il supporto SSL tramite la casella di controllo **Configura per HTTPS**.
1. Spuntare la casella di controllo **Abilita Supporto Docker**.
1. Selezionare il tipo di contenitore e fare clic su **Crea**. I contenitori di Windows non sono supportati per la distribuzione nel servizio app Azure come contenitore.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Distribuire il contenitore in Azure

1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
1. Nella finestra di dialogo pubblica destinazione scegliere **servizio app Linux** o **servizio app**. Si tratta del sistema operativo in cui verrà ospitato il server Web.
1. È possibile pubblicare solo nel servizio app oppure pubblicare sia nel servizio app che in Azure Container Registry (ACR). Per pubblicare il contenitore in un Container Registry di Azure (ACR), scegliere **Crea nuovo servizio app per contenitori**, quindi fare clic su **pubblica**.

   ![Screenshot della finestra di dialogo di pubblicazione](media/deploy-app-service/publish-app-service-linux.PNG)

   Per pubblicare solo in un servizio app Azure senza usare Container Registry di Azure, scegliere **Crea nuovo**e fare clic su **pubblica**.

1. Verificare di aver eseguito l'accesso con l'account associato alla sottoscrizione di Azure e scegliere un nome univoco, una sottoscrizione, un gruppo di risorse, un piano di hosting e un registro contenitori, se applicabile, oppure accettare le impostazioni predefinite.

   ![Screenshot delle impostazioni di pubblicazione](media/deploy-app-service/publish-app-service-linux2.png)

1. Scegliere **Crea**. Il contenitore viene distribuito in Azure nel gruppo di risorse e nel registro contenitori selezionato. Questo processo richiede un po' di tempo. Al termine, la scheda **Publish (pubblica** ) Mostra informazioni sugli elementi pubblicati, incluso l'URL del sito.

   ![Screenshot della scheda pubblica](media/deploy-app-service/publish-succeeded.PNG)

1. Fare clic sul collegamento di sito per verificare che l'app funzioni come previsto in Azure.

   ![Screenshot dell'applicazione Web](media/deploy-app-service/web-application-running.png)

1. Il profilo di pubblicazione viene salvato con tutti i dettagli selezionati, ad esempio il gruppo di risorse e il registro contenitori.

1. Per eseguire di nuovo la distribuzione con lo stesso profilo di pubblicazione, usare il pulsante **pubblica** , il pulsante **pubblica** nella finestra **attività di pubblicazione Web** oppure fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere l'elemento **Publish (pubblica** ) dal menu di scelta rapida.

## <a name="view-container-settings"></a>Visualizzare le impostazioni del contenitore

Nel [portale di Azure](https://portal.azure.com)è possibile aprire il servizio app distribuito.

È possibile visualizzare le impostazioni per il servizio app distribuito aprendo il menu **Impostazioni contenitore* (quando si usa Visual Studio 2019 versione 16,4 o successiva).

![Screenshot del menu delle impostazioni del contenitore nel portale di Azure](media/deploy-app-service/container-settings-menu.png)

Da qui è possibile visualizzare le informazioni sul contenitore, visualizzare o scaricare i log o configurare la distribuzione continua. Vedere [app Azure ci/CD per la distribuzione continua del servizio](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Pulire le risorse

Per rimuovere tutte le risorse di Azure associate a questa esercitazione, eliminare il gruppo di risorse usando il [portale di Azure](https://portal.azure.com). Per trovare il gruppo di risorse associato a un'applicazione Web pubblicata, scegliere **visualizza** > altre **attività di pubblicazione web**di **Windows** > , quindi scegliere l'icona dell'ingranaggio. Verrà visualizzata la scheda **pubblica** che contiene il gruppo di risorse.

Nella portale di Azure scegliere gruppi di **risorse**, selezionare il gruppo di risorse per aprirne la pagina dei dettagli. Verificare che questo sia il gruppo di risorse corretto, quindi scegliere **Rimuovi gruppo di risorse**, digitare il nome e scegliere **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

Scopri di più sul [servizio app Azure Linux](/azure/app-service/containers/app-service-linux-intro).

## <a name="see-also"></a>Vedere anche

[Eseguire la distribuzione in Azure Container Registry](hosting-web-apps-in-docker.md)