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
ms.openlocfilehash: 907fecd348dba46f6d3375d2d994b04ec1cf1eb5
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2018
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

Un file di impostazioni di pubblicazione (*\*publishsettings*) è diverso da quello di un profilo di pubblicazione (*\*pubxml*) creati in Visual Studio. Un file di impostazioni di pubblicazione viene creato da IIS o di servizio App di Azure, o può essere creato manualmente e quindi possono essere importato in Visual Studio.

> [!NOTE]
> Se è sufficiente copiare un profilo di pubblicazione di Visual Studio (\*file con estensione pubxml) da un'installazione di Visual Studio a un altro, è possibile trovare il profilo di pubblicazione  *\<profilename\>pubxml*, Nel  *\\< NomeProgetto\>\Properties\PublishProfiles* cartella per i tipi di progetto gestito. Per i siti Web, guarda sotto la *\App_Data* cartella. I profili di pubblicazione sono file XML di MSBuild.

## <a name="prerequisites"></a>Prerequisiti

* È necessario disporre di Visual Studio 2017 installato e il **ASP.NET** e **.NET Framework** carico di lavoro di sviluppo. Per un'applicazione .NET Core, è necessario anche il **.NET Core** carico di lavoro.

    Se non è ancora stato installato Visual Studio, installarlo gratuitamente [qui](http://www.visualstudio.com).

* Per generare il file di impostazioni di pubblicazione da IIS, è necessario disporre di un computer che esegue Windows Server 2012 o Windows Server 2016 ed è necessario disporre del ruolo Server Web IIS configurato correttamente. ASP.NET 4.5 o ASP.NET di base deve essere installato. Per ASP.NET Core, vedere [pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Per ASP.NET 4.5, vedere [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

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

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Dopo che l'app viene distribuito correttamente, verrà avviato automaticamente. Se non avviato da Visual Studio, avviare l'app in IIS. Per ASP.NET Core, è necessario assicurarsi che il pool di applicazioni di campo per il **DefaultAppPool** è impostata su **nessun codice gestito**.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è creato un file di impostazioni di pubblicazione, importato in Visual Studio e distribuito un'app ASP.NET in IIS.

> [!div class="nextstepaction"]
> [Presentazione della distribuzione](../deployment/deploying-applications-services-and-components.md)
