---
title: Pubblicare in Azure importando le impostazioni di pubblicazione
description: Creare e importare un profilo di pubblicazione per distribuire un'applicazione da Visual Studio in Servizio app di Azure
ms.date: 08/27/2021
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 7d2807480741ff40df82156eea563843bec07712
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709882"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Pubblicare un'applicazione nel servizio app di Azure importando le impostazioni di pubblicazione in Visual Studio

È possibile usare lo strumento **Pubblica** per importare le impostazioni di pubblicazione e quindi distribuire l'app. In questo articolo vengono usate le impostazioni di pubblicazione per il servizio app di Azure, ma è possibile seguire una procedura simile per importare le impostazioni di pubblicazione da [IIS](../deployment/tutorial-import-publish-settings-iis.md). In alcuni scenari per rendere l'operazione più rapida è possibile usare un profilo delle impostazioni di pubblicazione anziché configurare manualmente la distribuzione nel servizio per ogni installazione di Visual Studio.

Questa procedura si applica alle app ASP.NET, ASP.NET Core e .NET Core in Visual Studio. È anche possibile importare le impostazioni di pubblicazione per le app [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Generare un file delle impostazioni di pubblicazione dal servizio app di Azure
> * Importare il file delle impostazioni di pubblicazione in Visual Studio
> * Distribuire l'app nel servizio app di Azure

Un file di impostazioni di pubblicazione (*\* .publishsettings*) è diverso da un profilo di pubblicazione (*\* .pubxml*) creato in Visual Studio. Il file delle impostazioni di pubblicazione viene creato dal servizio app di Azure e quindi importato in Visual Studio.

> [!NOTE]
> Se è sufficiente copiare un profilo di pubblicazione Visual Studio (file con estensione *\* pubxml)* da un'installazione di Visual Studio a un'altra, è possibile trovare il profilo di pubblicazione, *\<profilename\> .pubxml,* nella cartella nomeprogetto *\\ di<\> \Properties\PublishProfiles* per i tipi di progetto gestiti. Per i siti Web, cercare nella cartella *\App_Data*. I profili di pubblicazione sono file XML di MSBuild.

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"

* È necessario aver installato Visual Studio 2019 e il carico di lavoro **Sviluppo ASP.NET e Web**.

    Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
::: moniker-end

::: moniker range="vs-2017"

* È necessario aver installato Visual Studio 2017 e il carico di lavoro **Sviluppo ASP.NET e Web**.

    Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
::: moniker-end

* Creare un servizio app di Azure. Per istruzioni dettagliate, vedere [Distribuire un'app Web ASP.NET Core in Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Creare un nuovo progetto ASP.NET in Visual Studio

1. Creare un nuovo progetto nel computer che esegue Visual Studio.

    Scegliere il modello corretto. In questo esempio scegliere **ASP.NET'applicazione Web (.NET Framework)** o (solo per C#) ASP.NET Core **Web Application (Applicazione Web)** e quindi **selezionare OK.**

    Se i modelli di progetto specificati non vengono visualizzati, passare al collegamento **Apri** Programma di installazione di Visual Studio nel riquadro sinistro della finestra di **dialogo Project** nuovo progetto. Verrà avviato il Programma di installazione di Visual Studio. Installare il carico **ASP.NET e sviluppo** Web.

    Il modello di progetto selezionato (ASP.NET o ASP.NET Core) deve corrispondere alla versione di ASP.NET installata nel server Web.

1. Scegliere **MVC** (.NET Framework) o Applicazione **Web (Model-View-Controller)** (per .NET Core) e verificare che l'opzione Nessuna autenticazione sia selezionata e quindi selezionare **OK.** 

1. Digitare un nome come **MyWebApp e** selezionare **OK.**

    Visual Studio crea il progetto.

1. Scegliere **Compila**  >  **compila soluzione** per compilare il progetto.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Creare il file delle impostazioni di pubblicazione nel servizio app di Azure

1. Nel portale di Azure aprire il servizio app di Azure.

1. Passare a **Get publish profile (Ottieni profilo di** pubblicazione) e salvare il profilo in locale.

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
        destinationAppUrl="http://deployaspdotnetcore2021.azurewebsites.net"
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
