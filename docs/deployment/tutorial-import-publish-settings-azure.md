---
title: Pubblicare in Azure importando le impostazioni di pubblicazione
ms.description: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
ms.date: 05/07/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b4b0e4ea963f20199267f32a8c87440c8cc350b
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808321"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Pubblicare un'applicazione nel servizio app di Azure importando le impostazioni di pubblicazione in Visual Studio

È possibile usare lo strumento **Pubblica** per importare le impostazioni di pubblicazione e quindi distribuire l'app. In questo articolo vengono usate le impostazioni di pubblicazione per il servizio app di Azure, ma è possibile seguire una procedura simile per importare le impostazioni di pubblicazione da [IIS](../deployment/tutorial-import-publish-settings-iis.md). In alcuni scenari per rendere l'operazione più rapida è possibile usare un profilo delle impostazioni di pubblicazione anziché configurare manualmente la distribuzione nel servizio per ogni installazione di Visual Studio.

Questa procedura si applica alle app ASP.NET, ASP.NET Core e .NET Core in Visual Studio. È anche possibile importare le impostazioni di pubblicazione per le app [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md). La procedura fa riferimento a Visual Studio 2017 versione 15.6.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Generare un file delle impostazioni di pubblicazione dal servizio app di Azure
> * Importare il file delle impostazioni di pubblicazione in Visual Studio
> * Distribuire l'app nel servizio app di Azure

Il file delle impostazioni di pubblicazione (*\*.publishsettings*) non corrisponde al profilo di pubblicazione (*\*.pubxml*) creato in Visual Studio. Il file delle impostazioni di pubblicazione viene creato dal servizio app di Azure e quindi importato in Visual Studio.

> [!NOTE]
> Per copiare un profilo di pubblicazione di Visual Studio (file *\*.pubxml*) da un'installazione di Visual Studio a un'altra, il profilo di pubblicazione, *\<nomeprofilo\>.pubxml*, è disponibile nella cartella *\\<nomeprogetto\>\Properties\PublishProfiles* per i tipi di progetto gestiti. Per i siti Web, cercare nella cartella *\App_Data*. I profili di pubblicazione sono file XML di MSBuild.

## <a name="prerequisites"></a>Prerequisiti

* È necessario aver installato Visual Studio 2017 e avere il carico di lavoro di sviluppo **ASP.NET** e **.NET Framework**. Per un'app .NET Core, è necessario anche il carico di lavoro **.NET Core**.

    Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

* Creare un servizio app di Azure. Per istruzioni dettagliate, vedere [Distribuire un'app Web ASP.NET Core in Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Creare un nuovo progetto ASP.NET in Visual Studio

1. Nel computer che esegue Visual Studio scegliere **File** > **Nuovo progetto**.

1. In **Visual C#** o **Visual Basic** scegliere **Web**, quindi nel riquadro centrale scegliere **Applicazione Web ASP.NET (.NET Framework)** oppure (solo C#) **Applicazione Web ASP.NET Core** e infine fare clic su **OK**.

    Se non vengono visualizzati i modelli di progetto specificati, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Vedere i prerequisiti descritti in questo articolo per identificare i carichi di lavoro di Visual Studio che è necessario installare.

1. Scegliere **MVC** (.NET Framework) o **Applicazione Web (MVC)** (per .NET Core) e verificare che l'opzione **Nessuna autenticazione** sia selezionata, quindi fare clic su **OK**.

1. Digitare un nome come **MyWebApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

1. Scegliere **Compila** > **Compila soluzione** per compilare il progetto.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Creare il file delle impostazioni di pubblicazione nel servizio app di Azure

1. Nel portale di Azure aprire il servizio app di Azure.

1. Fare clic su **Recupera profilo di pubblicazione** e salvare il profilo in locale.

    ![Recuperare il profilo di pubblicazione](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Un file con estensione *.publishsettings* è stato generato nel percorso in cui è stato salvato. Il codice seguente illustra un esempio parziale del file (in una formattazione più leggibile).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```
    Il file *.publishsettings precedente contiene in genere due profili di pubblicazione che è possibile usare in Visual Studio, uno per la distribuzione tramite Distribuzione Web e uno per la distribuzione tramite FTP. Il codice precedente mostra il profilo di Distribuzione Web. Entrambi i profili verranno importati in un secondo momento quando si importa il profilo.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato creato un file delle impostazioni di pubblicazione, il file è stato importato in Visual Studio ed è stata distribuita un'app ASP.NET nel servizio app di Azure. È disponibile una panoramica delle opzioni di pubblicazione in Visual Studio.

> [!div class="nextstepaction"]
> [Presentazione della distribuzione](../deployment/deploying-applications-services-and-components.md)
