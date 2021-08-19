---
title: Distribuire un ASP.NET Core contenitore in Servizio app di Azure
description: Informazioni su come usare Visual Studio Container Tools per distribuire un'app Web ASP.NET Core in un contenitore Docker in Servizio app di Azure
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-container-tools
ms.devlang: dotnet
ms.topic: how-to
ms.date: 02/21/2021
ms.author: ghogen
ms.openlocfilehash: 6dd3a1bf0dd7b40f101f95e74c18dee071b4cfc6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122162032"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Distribuire un ASP.NET Core contenitore in Servizio app di Azure usando Visual Studio

Questa esercitazione illustra l'uso di Visual Studio pubblicare l'applicazione Web ASP.NET Core contenitore in un [Servizio app di Azure](/azure/app-service). Servizio app di Azure è un servizio appropriato per un'app Web a contenitore singolo ospitata in Azure.

Se non si ha una sottoscrizione di Azure, creare un [account gratuito](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) prima di iniziare.

## <a name="prerequisites"></a>Prerequisiti

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
5. Selezionare **Applicazione Web.**
6. Spuntare la casella di controllo **Abilita Supporto Docker**.
7. Selezionare il tipo **di contenitore Linux** e fare clic su **OK.** Windows contenitori non sono supportati per la distribuzione Servizio app di Azure come contenitore.
::: moniker-end
::: moniker range=">= vs-2019"
1. Nella finestra iniziale di Visual Studio scegliere **Crea un nuovo progetto**.
1. Scegliere **ASP.NET Core'app Web** e scegliere **Avanti.**
1. Assegnare un nome alla nuova applicazione (o prendere il valore predefinito) e scegliere **Avanti.**
1. Scegliere la versione di .NET di destinazione. Se non si è certi, scegliere la versione LTS (Long-Term Support).
1. Scegliere se si vuole il supporto SSL tramite la casella di controllo **Configura per HTTPS**.
1. Spuntare la casella di controllo **Abilita Supporto Docker**.
1. Selezionare il tipo di contenitore e fare clic su **Crea.**
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Distribuire il contenitore in Azure

::: moniker range="vs-2017"

1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
1. Nella finestra di dialogo di destinazione di pubblicazione scegliere **Servizio app Linux** o Servizio **app.** Si tratta del sistema operativo che ospiterà il server Web.
1. È possibile pubblicare solo nel servizio app oppure nel servizio app e nel Registro Azure Container (ACR). Per pubblicare il contenitore in un Registro Azure Container( ACR), scegliere **Create new App Service for containers**(Crea nuovo servizio app per contenitori) e fare clic su **Publish (Pubblica).**

   ![Screenshot della finestra di dialogo di pubblicazione](media/deploy-app-service/publish-app-service-linux-1.png)

   Per pubblicare solo in un Servizio app di Azure senza usare Registro Azure Container, scegliere Crea **nuovo** e fare clic su **Pubblica.**

1. Verificare di aver eseguito l'accesso con l'account associato alla sottoscrizione di Azure e scegliere un nome univoco, una sottoscrizione, un gruppo di risorse, un piano di hosting e un registro contenitori (se applicabile) oppure accettare le impostazioni predefinite.

   ![Screenshot delle impostazioni di pubblicazione](media/deploy-app-service/publish-app-service-linux-2.png)

1. Scegliere **Crea**. Il contenitore viene distribuito in Azure nel gruppo di risorse e nel registro contenitori selezionati. Questo processo richiede un po' di tempo. Al termine, nella scheda **Pubblica** vengono visualizzate informazioni sugli elementi pubblicati, incluso l'URL del sito.

   ![Screenshot della scheda Pubblica](media/deploy-app-service/publish-succeeded.PNG)

1. Fare clic sul collegamento del sito per verificare che l'app funzioni come previsto in Azure.

   ![Screenshot dell'applicazione Web](media/deploy-app-service/web-application-running.png)

1. Il profilo di pubblicazione viene salvato con tutti i dettagli selezionati, ad esempio il gruppo di risorse e il registro contenitori.

1. Per eseguire nuovamente la distribuzione con  lo stesso  profilo di  pubblicazione, usare il pulsante Pubblica, il pulsante Pubblica  nella finestra Attività di pubblicazione Web oppure fare clic con il pulsante destro del mouse sul progetto **in Esplora soluzioni** e scegliere l'elemento Pubblica nel menu di scelta rapida.
:::moniker-end
:::moniker range=">=vs-2019"
1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
1. Nella finestra **di dialogo** Pubblica scegliere la destinazione **di Azure.**

   ![Screenshot della pubblicazione guidata](media/deploy-app-service/publish-choices.png)

1. Nella scheda **Destinazione specifica** scegliere la destinazione di distribuzione appropriata, ad esempio Servizio app **(Windows)** o **Servizio app (Linux),** a seconda del tipo di contenitore.

   ![Screenshot della scheda Destinazione specifica della pubblicazione guidata](media/deploy-app-service/publish-app-service-windows.png)

1. Se non è stato eseguito l'accesso all'account Azure giusto con la sottoscrizione che si vuole usare, accedere usando il pulsante in alto a sinistra nella **finestra Pubblica.**

1. È possibile usare un servizio app esistente o crearne uno nuovo facendo clic sul collegamento **Create new Servizio app di Azure (Crea nuovo** servizio). Trovare il servizio app esistente nella visualizzazione albero espandendo  il gruppo di risorse oppure modificare l'impostazione Visualizza in **Tipo** di risorsa per ordinare in base al tipo.

   ![Screenshot che mostra la scelta di un servizio app](media/deploy-app-service/publish-app-service-windows2.png)

1. Se si crea un nuovo gruppo di risorse, verranno generati un gruppo di risorse e un servizio app in Azure. Se si desidera, è possibile modificare i nomi, purché siano univoci.

   ![Screenshot che mostra la creazione di un servizio app](media/deploy-app-service/publish-app-service-windows3.png)

1. È possibile accettare il piano di hosting predefinito o modificare il piano di hosting ora o in un secondo momento nel portale di Azure. Il valore predefinito `S1` è (piccolo) in una delle aree supportate. Per creare un piano di hosting, scegliere **Nuovo accanto all'elenco** a discesa **Piano di** hosting. Viene **visualizzata la finestra Piano** di hosting.

   ![Screenshot che mostra le opzioni del piano di hosting](media/deploy-app-service/hosting-plan.png)

   È possibile visualizzare i dettagli su queste opzioni nella [Servizio app di Azure panoramica del piano.](/azure/app-service/overview-hosting-plans)

1. Dopo aver selezionato o creato queste risorse, scegliere **Fine.** Il contenitore viene distribuito in Azure nel gruppo di risorse e nel servizio app selezionato. Questo processo richiede un po' di tempo. Al termine, nella scheda **Pubblica** vengono visualizzate informazioni sugli elementi pubblicati, incluso l'URL del sito.

   ![Screenshot della scheda Pubblica](media/deploy-app-service/publish-succeeded-windows.png)

1. Fare clic sul collegamento del sito per verificare che l'app funzioni come previsto in Azure.

   ![Screenshot dell'applicazione Web](media/deploy-app-service/web-application-running2.png)

1. Il profilo di pubblicazione viene salvato con tutti i dettagli selezionati, ad esempio il gruppo di risorse e il servizio app.

1. Per eseguire nuovamente la distribuzione con  lo stesso  profilo di  pubblicazione, usare il pulsante Pubblica, il pulsante Pubblica  nella finestra Attività di pubblicazione Web oppure fare clic con il pulsante destro del mouse sul progetto **in Esplora soluzioni** e scegliere l'elemento Pubblica nel menu di scelta rapida.
:::moniker-end

## <a name="view-container-settings"></a>Visualizzare le impostazioni del contenitore

Nel [portale di Azure](https://portal.azure.com)è possibile aprire il servizio app distribuito.

È possibile visualizzare le impostazioni per il servizio app distribuito aprendo il **menu** Impostazioni contenitore (quando si usa Visual Studio 2019 versione 16.4 o successiva).

![Screenshot del menu Impostazioni contenitore nel portale di Azure](media/deploy-app-service/container-settings-menu.png)

Da qui è possibile visualizzare le informazioni sul contenitore, visualizzare o scaricare i log o configurare la distribuzione continua. Vedere [Servizio app di Azure Ci/CD per la distribuzione continua.](/azure/app-service/containers/app-service-linux-ci-cd)

## <a name="clean-up-resources"></a>Eseguire la pulizia delle risorse

Per rimuovere tutte le risorse di Azure associate a questa esercitazione, eliminare il gruppo di risorse usando il [portale di Azure](https://portal.azure.com). Per trovare il gruppo di risorse associato a un'applicazione Web pubblicata, scegliere Visualizza altro Windows'attività pubblicazione Web e quindi  >    >  scegliere l'icona a forma di ingranaggio. Verrà **visualizzata** la scheda Pubblica, che contiene il gruppo di risorse.

Nel riquadro portale di Azure scegliere **Gruppi di risorse** e selezionare il gruppo di risorse per aprire la relativa pagina dei dettagli. Verificare che si tratta del gruppo di risorse corretto, quindi scegliere **Rimuovi gruppo di risorse,** digitare il nome e scegliere **Elimina.**

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni su [Servizio app di Azure](/azure/app-service/overview).

## <a name="see-also"></a>Vedi anche

[Eseguire la distribuzione in Registro Azure Container](hosting-web-apps-in-docker.md)