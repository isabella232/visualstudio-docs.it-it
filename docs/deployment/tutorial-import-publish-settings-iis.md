---
title: Pubblicare in IIS importando le impostazioni di pubblicazione
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
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808465"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Pubblicare un'applicazione in IIS importando le impostazioni di pubblicazione in Visual Studio

È possibile usare lo strumento **Pubblica** per importare le impostazioni di pubblicazione e quindi distribuire l'app. In questo articolo vengono usate le impostazioni di pubblicazione per IIS, ma è possibile seguire una procedura simile per importare le impostazioni di pubblicazione per il [servizio app di Azure](../deployment/tutorial-import-publish-settings-azure.md). In alcuni scenari per rendere l'operazione più rapida è possibile usare un profilo delle impostazioni di pubblicazione anziché configurare manualmente la distribuzione in IIS per ogni installazione di Visual Studio.

Questa procedura si applica alle app ASP.NET, ASP.NET Core e .NET Core in Visual Studio. La procedura fa riferimento a Visual Studio 2017 versione 15.6.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Configurare IIS per poter creare un file delle impostazioni di pubblicazione
> * Creare un file delle impostazioni di pubblicazione
> * Importare il file delle impostazioni di pubblicazione in Visual Studio
> * Distribuire l'app in IIS

Il file delle impostazioni di pubblicazione (*\*.publishsettings*) non corrisponde al profilo di pubblicazione (*\*.pubxml*) creato in Visual Studio. Il file delle impostazioni di pubblicazione viene creato da IIS o dal servizio app di Azure oppure può essere creato manualmente e quindi importato in Visual Studio.

> [!NOTE]
> Per copiare un profilo di pubblicazione di Visual Studio (file \*.pubxml) da un'installazione di Visual Studio a un'altra, il profilo di pubblicazione, *\<nomeprofilo\>.pubxml*, è disponibile nella cartella *\\<nomeprogetto\>\Properties\PublishProfiles* per i tipi di progetto gestiti. Per i siti Web, cercare nella cartella *\App_Data*. I profili di pubblicazione sono file XML di MSBuild.

## <a name="prerequisites"></a>Prerequisiti

* È necessario aver installato Visual Studio 2017 e avere il carico di lavoro di sviluppo **ASP.NET** e **.NET Framework**. Per un'app .NET Core, è necessario anche il carico di lavoro **.NET Core**.

    Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

* Per generare il file delle impostazioni di pubblicazione da IIS, è necessario avere un computer che esegue Windows Server 2012 o Windows Server 2016 e aver configurato correttamente il ruolo Server Web di IIS. È necessario aver installato anche ASP.NET 4.5 o ASP.NET Core. Per ASP.NET Core, vedere [Pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Per ASP.NET 4.5, vedere [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (IIS 8.0 con ASP.NET 3.5 e ASP.NET 4.5).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Creare un nuovo progetto ASP.NET in Visual Studio

1. Nel computer che esegue Visual Studio scegliere **File** > **Nuovo progetto**.

1. In **Visual C#** o **Visual Basic** scegliere **Web**, quindi nel riquadro centrale scegliere **Applicazione Web ASP.NET (.NET Framework)** oppure (solo C#) **Applicazione Web ASP.NET Core** e infine fare clic su **OK**.

    Se non vengono visualizzati i modelli di progetto specificati, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Vedere i prerequisiti descritti in questo articolo per identificare i carichi di lavoro di Visual Studio che è necessario installare.

1. Scegliere **MVC** (.NET Framework) o **Applicazione Web (MVC)** (per .NET Core) e verificare che l'opzione **Nessuna autenticazione** sia selezionata, quindi fare clic su **OK**.

1. Digitare un nome come **MyWebApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

1. Scegliere **Compila** > **Compila soluzione** per compilare il progetto.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Installare e configurare Distribuzione Web in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Creare il file delle impostazioni di pubblicazione in IIS in Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Quando la distribuzione è completata, l'app viene avviata automaticamente. Se l'app non viene avviata da Visual Studio, avviare l'app in IIS. Per ASP.NET Core, è necessario assicurarsi che il campo Pool di applicazioni per **DefaultAppPool** sia impostato su **Nessun codice gestito**.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato creato un file delle impostazioni di pubblicazione, il file è stato importato in Visual Studio ed è stata distribuita un'app ASP.NET in IIS. È disponibile una panoramica delle altre opzioni di pubblicazione in Visual Studio.

> [!div class="nextstepaction"]
> [Presentazione della distribuzione](../deployment/deploying-applications-services-and-components.md)
