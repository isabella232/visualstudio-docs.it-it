---
title: Pubblicare in IIS importando le impostazioni di pubblicazione
description: Creare e importare un profilo di pubblicazione per distribuire un'applicazione da Visual Studio in IIS
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: ca5aac87838ad52aee0432a6430f74d35281b063ad2ae94c92f1c2baca3476d3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403841"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Pubblicare un'applicazione in IIS importando le impostazioni di pubblicazione in Visual Studio

È possibile usare lo strumento **Pubblica** per importare le impostazioni di pubblicazione e quindi distribuire l'app. In questo articolo vengono usate le impostazioni di pubblicazione per IIS, ma è possibile seguire una procedura simile per importare le impostazioni di pubblicazione per il [servizio app di Azure](../deployment/tutorial-import-publish-settings-azure.md). In alcuni scenari per rendere l'operazione più rapida è possibile usare un profilo delle impostazioni di pubblicazione anziché configurare manualmente la distribuzione in IIS per ogni installazione di Visual Studio.

Questa procedura si applica alle app ASP.NET, ASP.NET Core e .NET Core in Visual Studio.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Configurare IIS per poter creare un file delle impostazioni di pubblicazione
> * Creare un file delle impostazioni di pubblicazione
> * Importare il file delle impostazioni di pubblicazione in Visual Studio
> * Distribuire l'app in IIS

Un file di impostazioni di pubblicazione (*\* .publishsettings*) è diverso da un profilo di pubblicazione (*\* .pubxml*) creato in Visual Studio. Il file delle impostazioni di pubblicazione viene creato da IIS o dal servizio app di Azure oppure può essere creato manualmente e quindi importato in Visual Studio.

> [!NOTE]
> Se è sufficiente copiare un profilo di pubblicazione Visual Studio (file con estensione pubxml) da un'installazione di Visual Studio a un'altra, è possibile trovare il profilo di \* pubblicazione, *\<profilename\> .pubxml*, nella cartella nomeprogetto *\\ di<\> \Properties\PublishProfiles* per i tipi di progetto gestiti. Per i siti Web, cercare nella cartella *\App_Data*. I profili di pubblicazione sono file XML di MSBuild.

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"

* È necessario aver installato Visual Studio 2019 e il carico di lavoro **Sviluppo ASP.NET e Web**.

    Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
::: moniker-end

::: moniker range="vs-2017"

* È necessario aver installato Visual Studio 2017 e il carico di lavoro **Sviluppo ASP.NET e Web**.

    Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
::: moniker-end

* Nel server è necessario eseguire Windows Server 2012, Windows Server 2016 o Windows Server 2019 ed è necessario che il ruolo [Server Web IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) sia installato correttamente (necessario per generare il file delle impostazioni di pubblicazione (*\* .publishsettings*)). Nel server deve essere installato anche ASP.NET 4.5 o ASP.NET Core. Per configurare ASP.NET 4.5, vedere [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (IIS 8.0 con ASP.NET 3.5 e ASP.NET 4.5). Per configurare ASP.NET Core, vedere [Host ASP.NET Core in Windows con IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Per ASP.NET Core, assicurarsi di configurare il pool di applicazioni per l'uso di Nessun **codice gestito,** come descritto nell'articolo.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Creare un nuovo progetto ASP.NET in Visual Studio

1. Creare un nuovo progetto nel computer che esegue Visual Studio.

    Scegliere il modello corretto. In questo esempio scegliere **un ASP.NET App applicazione Web (.NET Framework)** o (solo per **C#)** ASP.NET Core Applicazione Web e quindi selezionare **OK.**

    Se i modelli di progetto specificati non vengono visualizzati, passare al collegamento **Apri** Programma di installazione di Visual Studio nel riquadro sinistro della finestra di **dialogo Project** nuovo progetto. Verrà avviato il Programma di installazione di Visual Studio. Installare il carico **ASP.NET e sviluppo** Web.

    Il modello di progetto selezionato (ASP.NET o ASP.NET Core) deve corrispondere alla versione di ASP.NET installata nel server Web.

1. Scegliere **MVC** (.NET Framework) o Applicazione **Web (Model-View-Controller)** (per .NET Core) e verificare che l'opzione Nessuna autenticazione sia selezionata e quindi selezionare **OK.** 

1. Digitare un nome come **MyWebApp e** selezionare **OK.**

    Visual Studio crea il progetto.

1. Scegliere **Compila**  >  **soluzione (o** premere **CTRL**  +  **MAIUSC**  +  **B)** per compilare il progetto.

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
