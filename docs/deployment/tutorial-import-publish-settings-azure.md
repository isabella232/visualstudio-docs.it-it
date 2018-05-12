---
title: Pubblicare in Azure tramite l'importazione delle impostazioni di pubblicazione
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: 3e844e2177d01d5b308472eae5661b25798f0838
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/11/2018
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Pubblicare un'applicazione di servizio App di Azure importando le impostazioni di pubblicazione in Visual Studio

È possibile usare il **pubblica** strumento di importare le impostazioni di pubblicazione e quindi distribuire l'app. In questo articolo, si Usa impostazioni di pubblicazione per servizio App di Azure, ma è possibile utilizzare passaggi simili per importare impostazioni da di pubblicazione [IIS](../deployment/tutorial-import-publish-settings-iis.md). In alcuni scenari di utilizzo di una pubblicazione profilo delle impostazioni possa essere più veloce di manualmente la configurazione di distribuzione per il servizio per ogni installazione di Visual Studio.

Questi passaggi si applicano alle App ASP.NET, ASP.NET Core e .NET Core in Visual Studio. È inoltre possibile importare impostazioni di pubblicazione per [Python](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio) app. I passaggi corrispondono a Visual Studio 2017 versione 15,6.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Generare un file di impostazioni di pubblicazione dal servizio App di Azure
> * Importare il file di impostazioni di pubblicazione in Visual Studio
> * Distribuire l'applicazione di servizio App di Azure

Un file di impostazioni di pubblicazione (*\*publishsettings*) è diverso da quello di un profilo di pubblicazione (*\*pubxml*) creati in Visual Studio. Un file di impostazioni di pubblicazione viene creato dal servizio App di Azure e quindi possono essere importato in Visual Studio.

> [!NOTE]
> Se è sufficiente copiare un profilo di pubblicazione di Visual Studio (*\*pubxml* file) da un'installazione di Visual Studio a un altro, è possibile trovare il profilo di pubblicazione  *\<profilename\>pubxml*nella  *\\< NomeProgetto\>\Properties\PublishProfiles* cartella per i tipi di progetto gestito. Per i siti Web, guarda sotto la *\App_Data* cartella. I profili di pubblicazione sono file XML di MSBuild.

## <a name="prerequisites"></a>Prerequisiti

* È necessario disporre di Visual Studio installato e il **ASP.NET** e **.NET Framework** carico di lavoro di sviluppo. Per un'applicazione .NET Core, è necessario anche il **.NET Core** carico di lavoro.

    Se non è ancora stato installato Visual Studio, installarlo gratuitamente [qui](http://www.visualstudio.com).

* Creare un servizio App di Azure. Per istruzioni dettagliate, vedere [distribuire un'app web ASP.NET Core in Azure utilizzando Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). 

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Creare un nuovo progetto ASP.NET in Visual Studio

1. Nel computer che esegue Visual Studio, scegliere **File > Nuovo progetto**.

1. In **Visual c#** o **Visual Basic**, scegliere **Web**, quindi nel riquadro centrale scegliere **applicazione Web ASP.NET (.NET Framework)**(solo c#) o **applicazione Web di ASP.NET Core**, quindi fare clic su **OK**.

    Se i modelli di progetto specificato non viene visualizzato, fare clic sul **aperto Visual Studio Installer** collegamento nel riquadro sinistro della finestra di **nuovo progetto** finestra di dialogo. Verrà avviato il Programma di installazione di Visual Studio. Vedere i prerequisiti descritti in questo articolo per identificare i necessari Visual Studio carichi di lavoro, che deve essere installato.

1. Scegliere il **MVC** (.NET Framework) o **applicazione Web (Model-View-Controller)** (per .NET Core) e verificare che **Nessuna autenticazione** sia selezionata e quindi fare clic su **OK**.

1. Digitare un nome come **MyWebApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

1. Scegliere **compilazione > Compila soluzione** per compilare il progetto.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Creare il file di impostazioni di pubblicazione nel servizio App di Azure

1. Nel portale di Azure, aprire il servizio App di Azure.

1. Fare clic su **profilo di pubblicazione Get** e salvare il profilo locale.

    ![Ottenere il profilo di pubblicazione](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Un file con un *publishsettings* estensione di file è stato generato nel percorso in cui è stato salvato. Il codice seguente viene illustrato un esempio parziale del file (in una formattazione più leggibili).

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
    In genere, il file publishsettings precedente contiene due profili di pubblicazione che è possibile usare in Visual Studio, uno per distribuire usando distribuzione Web e uno per la distribuzione tramite FTP. Il codice precedente mostra il profilo di distribuzione Web. Entrambi i profili verranno importati in un secondo momento quando si importa il profilo.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

1. Nel computer in cui è aperto il progetto ASP.NET in Visual Studio, fare clic sul progetto in Esplora soluzioni e scegliere **pubblica**.

1. Se in precedenza è stato configurato alcun profilo di pubblicazione, il **pubblica** viene visualizzato il riquadro. Fare clic su **Crea nuovo profilo**.

1. Nel **selezionare una destinazione di pubblicazione** finestra di dialogo, fare clic su **Importa profilo**.

    ![Scegliere Pubblica](../deployment/media/tutorial-publish-tool-import-profile.png)

1. Passare al percorso del file delle impostazioni pubblica che è stato creato nella sezione precedente.

1. Nel **Importa i File di impostazioni di pubblicazione** la finestra di dialogo, selezionare il profilo che è stato creato nella sezione precedente, fare clic su **Apri**.

1. Selezionare uno dei due profili importati, quindi scegliere **pubblica**.

    Visual Studio avvia il processo di distribuzione e nella finestra di Output viene visualizzato lo stato di avanzamento e risultati.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è creato un file di impostazioni di pubblicazione, importato in Visual Studio e distribuito un'app ASP.NET al servizio App di Azure.

> [!div class="nextstepaction"]
> [Presentazione della distribuzione](../deployment/deploying-applications-services-and-components.md)
