---
title: La pubblicazione in IIS tramite l'importazione delle impostazioni di pubblicazione
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to IIS
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
ms.openlocfilehash: 1db8ca68453cff105f2bbefcd384b8afa9efea9d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Pubblicare un'applicazione in IIS tramite l'importazione delle impostazioni di pubblicazione in Visual Studio

È possibile usare il **pubblica** strumento di importare le impostazioni di pubblicazione e quindi distribuire l'app. In questo articolo, si Usa impostazioni di pubblicazione per IIS, ma è possibile utilizzare passaggi simili per importare impostazioni di pubblicazione per [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). In alcuni scenari di utilizzo di una pubblicazione profilo delle impostazioni possa essere più veloce di configurare manualmente la distribuzione in IIS per ogni installazione di Visual Studio.

Questi passaggi si applicano alle App ASP.NET, ASP.NET Core e .NET Core in Visual Studio. I passaggi corrispondono a Visual Studio 2017 versione 15,6.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Configurare IIS in modo che è possibile generare un file di impostazioni di pubblicazione
> * Creare un file di impostazioni di pubblicazione
> * Importare il file di impostazioni di pubblicazione in Visual Studio
> * Distribuire l'app in IIS

Un file di impostazioni di pubblicazione (\*publishsettings) è diverso da quello di un profilo di pubblicazione (\*pubxml) creato in Visual Studio. Un file di impostazioni di pubblicazione viene creato da IIS o di servizio App di Azure, o può essere creato manualmente e quindi possono essere importato in Visual Studio.

> [!NOTE]
> Se è sufficiente copiare un profilo di pubblicazione di Visual Studio (\*file con estensione pubxml) da un'installazione di Visual Studio a un altro, è possibile trovare il profilo di pubblicazione  *\<profilename\>pubxml*, Nel  *\\< NomeProgetto\>\Properties\PublishProfiles* cartella per i tipi di progetto gestito. Per i siti Web, guarda sotto la *\App_Data* cartella. I profili di pubblicazione sono file XML di MSBuild.

## <a name="prerequisites"></a>Prerequisiti

* È necessario disporre di Visual Studio installato e il **ASP.NET** e **.NET Framework** carico di lavoro di sviluppo. Per un'applicazione .NET Core, è necessario anche il **.NET Core** carico di lavoro.

    Se non è ancora stato installato Visual Studio, installarlo gratuitamente [qui](http://www.visualstudio.com).

    I passaggi descritti in questo articolo sono basati su Visual Studio 2017

* Per generare il file di impostazioni di pubblicazione da IIS, è necessario disporre di un altro computer che esegue Windows Server 2012 con il ruolo Server Web di IIS 8.0 configurato correttamente ed entrambi ASP.NET 4.5 o installato ASP.NET Core. Per ASP.NET Core, vedere [pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Per ASP.NET 4.5, vedere [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Creare un nuovo progetto ASP.NET in Visual Studio

1. Nel computer che esegue Visual Studio, scegliere **File > Nuovo progetto**.

1. In **Visual c#** o **Visual Basic**, scegliere **Web**, quindi nel riquadro centrale scegliere **applicazione Web ASP.NET (.NET Framework)**(solo c#) o **applicazione Web di ASP.NET Core**, quindi fare clic su **OK**.

    Se i modelli di progetto specificato non viene visualizzato, fare clic sul **aperto Visual Studio Installer** collegamento nel riquadro sinistro della finestra di **nuovo progetto** finestra di dialogo. Verrà avviato il Programma di installazione di Visual Studio. Vedere i prerequisiti descritti in questo articolo per identificare i necessari Visual Studio carichi di lavoro, che deve essere installato.

1. Scegliere il **MVC** (.NET Framework) o **applicazione Web (Model-View-Controller)** (per .NET Core) e verificare che **Nessuna autenticazione** sia selezionata e quindi fare clic su **OK**.

1. Digitare un nome come **MyWebApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

1. Scegliere **compilazione > Compila soluzione** per compilare il progetto.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Installare e configurare distribuzione Web in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Creare il file di impostazioni di pubblicazione in IIS in Windows Server

1. In IIS, fare doppio clic sui **sito Web predefinito**, scegliere **Distribuisci** > **configurare distribuire pubblicazione sul Web**.

    ![Configurazione di distribuzione Web](../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. Nel **configurare la distribuzione di pubblicazione sul Web** dialogo casella, esaminare le impostazioni.

1. Fare clic su **installazione**.

    Nel **risultati** pannello, l'output indica che i diritti di accesso è state concesse all'utente specificato e che un file con un *con estensione publishsettings* estensione di file è stato generato nel percorso indicato di finestra di dialogo.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    A seconda della configurazione di Windows Server e IIS, verranno visualizzati valori diversi. Di seguito sono riportati alcuni dettagli sui valori visualizzati:

    * Il *MSDeploy. axd* file cui fa riferimento il `publishUrl` attributo è un file generato in modo dinamico di un gestore HTTP per distribuzione Web. (Per i test `http://myhostname:8172` in genere funzionerà nonché.)
    * Il `publishUrl` porta è in genere impostata su porta 8172, ovvero l'impostazione predefinita per la distribuzione Web.
    * Il `destinationAppUrl` porta è in genere impostata sulla porta 80, ovvero il valore predefinito per IIS.
    * Se non si riesce a connettersi all'host remoto in Visual Studio usando il nome host (nei passaggi successivi), verificare l'indirizzo IP al posto del nome host.

    > [!NOTE]
    > Se esegue la pubblicazione in IIS in esecuzione in una macchina virtuale di Azure, è necessario aprire le porte IIS e distribuzione Web nel gruppo di sicurezza di rete. Per informazioni dettagliate, vedere [installare ed eseguire IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

1. Copiare questo file nel computer in cui si esegue Visual Studio.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

1. Nel computer in cui è aperto il progetto ASP.NET in Visual Studio, fare clic sul progetto in Esplora soluzioni e scegliere **pubblica**.

1. Se in precedenza è stato configurato alcun profilo di pubblicazione, il **pubblica** viene visualizzato il riquadro. Fare clic su **Crea nuovo profilo**.

1. Nel **selezionare una destinazione di pubblicazione** finestra di dialogo, fare clic su **Importa profilo**.

    ![Scegliere Pubblica](../deployment/media/tutorial-publish-tool-import-profile.png)

1. Passare al percorso del file delle impostazioni pubblica che è stato creato nella sezione precedente.

1. Nel **Importa i File di impostazioni di pubblicazione** la finestra di dialogo, passare a e selezionare il profilo che è stato creato nella sezione precedente, fare clic su **Apri**.

    Visual Studio avvia il processo di distribuzione e nella finestra di Output viene visualizzato lo stato di avanzamento e risultati.

    Se si verificano una distribuzione di eventuali errori, fare clic su **impostazioni** per modificare le impostazioni. Modificare le impostazioni e fare clic su **Validate** per testare le nuove impostazioni.

    ![Modificare le impostazioni nello strumento di pubblicazione](../deployment/media/tutorial-configure-publish-settings-in-tool.png)

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è creato un file di impostazioni di pubblicazione, importato in Visual Studio e distribuito un'app ASP.NET in IIS.

> [!div class="nextstepaction"]
> [Presentazione della distribuzione](../deployment/deploying-applications-services-and-components.md)
