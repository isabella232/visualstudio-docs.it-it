---
title: Pubblicazione in IIS tramite l'importazione delle impostazioni di pubblicazione
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
ms.openlocfilehash: e6df935578955d3c72b6f4fa61efdf614229bca0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808465"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Pubblicare un'applicazione in IIS tramite l'importazione delle impostazioni di pubblicazione in Visual Studio

È possibile usare la **pubblica** dello strumento per importare le impostazioni di pubblicazione e quindi distribuire l'app. In questo articolo, si Usa impostazioni di pubblicazione per IIS, ma è possibile usare una procedura simile per importare impostazioni di pubblicazione per [servizio App di Azure](../deployment/tutorial-import-publish-settings-azure.md). In alcuni scenari, uso di una pubblicazione profilo delle impostazioni può essere più veloce rispetto alla configurazione manuale di distribuzione in IIS per ogni installazione di Visual Studio.

Questi passaggi si applicano alle App ASP.NET, ASP.NET Core e .NET Core in Visual Studio. I passaggi corrispondono a Visual Studio 2017 versione 15.6.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Configurare IIS in modo che è possibile generare un file di impostazioni di pubblicazione
> * Creare un file di impostazioni di pubblicazione
> * Importare il file di impostazioni di pubblicazione in Visual Studio
> * Distribuire l'app in IIS

Un file di impostazioni di pubblicazione (*\*publishsettings*) è diverso da quello di un profilo di pubblicazione (*\*pubxml*) creati in Visual Studio. Un file di impostazioni di pubblicazione viene creato da IIS o servizio App di Azure o può essere creato manualmente e quindi possono essere importati in Visual Studio.

> [!NOTE]
> Se è sufficiente copiare un profilo di pubblicazione di Visual Studio (\*file con estensione pubxml) da un'installazione di Visual Studio a un altro, è possibile trovare il profilo di pubblicazione  *\<profilename\>pubxml*, nel  *\\< NomeProgetto\>\Properties\PublishProfiles* cartella per i tipi di progetto gestito. Per i siti Web, guarda sotto la *\App_Data* cartella. I profili di pubblicazione sono file XML di MSBuild.

## <a name="prerequisites"></a>Prerequisiti

* È necessario disporre di Visual Studio 2017 installato e il **ASP.NET** e **.NET Framework** carico di lavoro di sviluppo. Per un'app .NET Core, è necessario anche il **.NET Core** carico di lavoro.

    Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

* Per generare il file di impostazioni di pubblicazione da IIS, è necessario disporre di un computer che esegue Windows Server 2012 o Windows Server 2016 e deve avere il ruolo Server Web IIS configurato correttamente. ASP.NET 4.5 o ASP.NET Core deve essere installato. Per ASP.NET Core, vedere [pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Per ASP.NET 4.5, vedere [IIS 8.0 Using ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Creare un nuovo progetto ASP.NET in Visual Studio

1. Nel computer che esegue Visual Studio, scegliere **File** > **nuovo progetto**.

1. Sotto **Visual c#** oppure **Visual Basic**, scegliere **Web**, quindi nel riquadro centrale scegliere **applicazione Web ASP.NET (.NET Framework)**(solo c#) o **applicazione Web ASP.NET Core**, quindi fare clic su **OK**.

    Se i modelli di progetto specificato non è visibile, fare clic sul **aperto Visual Studio Installer** collegamento nel riquadro sinistro della finestra di **nuovo progetto** nella finestra di dialogo. Verrà avviato il Programma di installazione di Visual Studio. Vedere i prerequisiti descritti in questo articolo per identificare i necessari Visual Studio carichi di lavoro, che devono essere installati.

1. Scegliere uno **MVC** (.NET Framework) o **applicazione Web (Model-View-Controller)** (per .NET Core) e verificare che **Nessuna autenticazione** sia selezionata e quindi fare clic su **OK**.

1. Digitare un nome come **MyWebApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

1. Scegli **compilare** > **Compila soluzione** per compilare il progetto.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Installare e configurare distribuzione Web in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Creare il file di impostazioni di pubblicazione in IIS in Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Dopo che l'app distribuisce correttamente, viene avviata automaticamente. Se non viene avviato da Visual Studio, avviare l'app in IIS. Per ASP.NET Core, è necessario assicurarsi che il pool di applicazioni di campo per il **DefaultAppPool** è impostata su **nessun codice gestito**.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato creato un file di impostazioni di pubblicazione, viene importato in Visual Studio e distribuita un'app ASP.NET in IIS. È possibile una panoramica delle altre opzioni di pubblicazione in Visual Studio.

> [!div class="nextstepaction"]
> [Presentazione della distribuzione](../deployment/deploying-applications-services-and-components.md)
