---
title: Pubblicare in Azure tramite l'importazione delle impostazioni di pubblicazione
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
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808321"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Pubblicare un'applicazione in servizio App di Azure importando le impostazioni di pubblicazione in Visual Studio

È possibile usare la **pubblica** dello strumento per importare le impostazioni di pubblicazione e quindi distribuire l'app. In questo articolo, si Usa impostazioni di pubblicazione per servizio App di Azure, ma è possibile usare una procedura simile per importare impostazioni di pubblicazione da [IIS](../deployment/tutorial-import-publish-settings-iis.md). In alcuni scenari, uso di una pubblicazione profilo delle impostazioni può essere più veloce rispetto alla configurazione manuale di distribuzione per il servizio per ogni installazione di Visual Studio.

Questi passaggi si applicano alle App ASP.NET, ASP.NET Core e .NET Core in Visual Studio. È anche possibile importare impostazioni di pubblicazione [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) app. I passaggi corrispondono a Visual Studio 2017 versione 15.6.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Generare un file di impostazioni di pubblicazione dal servizio App di Azure
> * Importare il file di impostazioni di pubblicazione in Visual Studio
> * Distribuire l'app in servizio App di Azure

Un file di impostazioni di pubblicazione (*\*publishsettings*) è diverso da quello di un profilo di pubblicazione (*\*pubxml*) creati in Visual Studio. Un file di impostazioni di pubblicazione viene creato dal servizio App di Azure e quindi possono essere importati in Visual Studio.

> [!NOTE]
> Se è sufficiente copiare un profilo di pubblicazione di Visual Studio (*\*pubxml* file) da un'installazione di Visual Studio a un altro, è possibile trovare il profilo di pubblicazione  *\<profilename\>pubxml*, nella  *\\< projectname\>\Properties\PublishProfiles* cartella per i tipi di progetto gestito. Per i siti Web, guarda sotto la *\App_Data* cartella. I profili di pubblicazione sono file XML di MSBuild.

## <a name="prerequisites"></a>Prerequisiti

* È necessario disporre di Visual Studio 2017 installato e il **ASP.NET** e. **NET Framework** carico di lavoro di sviluppo. Per un'app .NET Core, è necessario anche il. **NET Core** carico di lavoro.

    Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

* Creare un servizio App di Azure. Per istruzioni dettagliate, vedere [distribuire un'app web ASP.NET Core in Azure usando Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Creare un nuovo progetto ASP.NET in Visual Studio

1. Nel computer che esegue Visual Studio, scegliere **File** > **nuovo progetto**.

1. Sotto **Visual c#** oppure **Visual Basic**, scegliere **Web**, quindi nel riquadro centrale scegliere **applicazione Web ASP.NET (.NET Framework)**(solo c#) o **applicazione Web ASP.NET Core**, quindi fare clic su **OK**.

    Se i modelli di progetto specificato non è visibile, fare clic sul **aperto Visual Studio Installer** collegamento nel riquadro sinistro della finestra di **nuovo progetto** nella finestra di dialogo. Verrà avviato il Programma di installazione di Visual Studio. Vedere i prerequisiti descritti in questo articolo per identificare i necessari Visual Studio carichi di lavoro, che devono essere installati.

1. Scegliere uno **MVC** (.NET Framework) o **applicazione Web (Model-View-Controller)** (per .NET Core) e verificare che **Nessuna autenticazione** sia selezionata e quindi fare clic su **OK**.

1. Digitare un nome come **MyWebApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

1. Scegli **compilare** > **Compila soluzione** per compilare il progetto.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Creare il file di impostazioni di pubblicazione nel servizio App di Azure

1. Nel portale di Azure, aprire il servizio App di Azure.

1. Fare clic su **Recupera profilo di pubblicazione** e salvare il profilo in locale.

    ![Ottenere il profilo di pubblicazione](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Un file con un *publishsettings* estensione di file è stato generato nel percorso in cui è stato salvato. Il codice seguente illustra un esempio parziale del file (in una formattazione più leggibili).

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
    In genere, il file *. publishsettings precedente contiene due profili di pubblicazione che è possibile usare in Visual Studio, uno per la distribuzione usando distribuzione Web e uno per la distribuzione tramite FTP. Il codice precedente mostra il profilo di distribuzione Web. Entrambi i profili verranno importati in un secondo momento quando si importa il profilo.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato creato un file di impostazioni di pubblicazione, viene importato in Visual Studio e distribuito un'app ASP.NET in servizio App di Azure. È possibile una panoramica delle opzioni di pubblicazione in Visual Studio.

> [!div class="nextstepaction"]
> [Presentazione della distribuzione](../deployment/deploying-applications-services-and-components.md)
