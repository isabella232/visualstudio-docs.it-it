---
title: Presentazione delle funzionalità di distribuzione
description: Informazioni sulle opzioni per la distribuzione di app da Visual Studio.
ms.custom: mvc
ms.date: 06/22/2018
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0db2a9dcd19b2100239a99ec8fc08850432aa80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860036"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Guida introduttiva: Presentazione della distribuzione in Visual Studio

Mediante la distribuzione, un'applicazione, un servizio o un componente viene distribuito per l'installazione in altri computer, dispositivi o server, oppure nel cloud. Il metodo appropriato viene scelto in Visual Studio per il tipo di distribuzione necessaria. Molti tipi di app supportano altri strumenti di distribuzione, ad esempio la distribuzione da riga di comando o NuGet, che non vengono descritti in questa sede.

Per istruzioni dettagliate per la distribuzione, vedere le guide introduttive e le esercitazioni. Per una panoramica delle opzioni di distribuzione, vedere [Quali sono le opzioni di pubblicazione più adatte?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Distribuire in una cartella locale

La distribuzione in una cartella locale viene di solito usata a scopo di test o per iniziare una pre-distribuzione quando viene usato un altro strumento per la distribuzione finale.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python** e **.NET Core**: usare lo strumento Pubblicazione per la distribuzione in una cartella locale. Le opzioni disponibili variano a seconda del tipo di app. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**. Se in precedenza sono stati configurati profili di pubblicazione, è quindi necessario fare clic su **Crea nuovo profilo**. Quindi scegliere **Cartella**. Per altre informazioni, vedere [Distribuire in una cartella locale](quickstart-deploy-to-local-folder.md).

    ![Scegliere Pubblica](../deployment/media/quickstart-publish.png)

- **Runtime di Visual C++**: è possibile distribuire il runtime di Visual C++ tramite distribuzione locale o collegamento statico. Per altre informazioni, vedere [Distribuzione di applicazioni desktop native (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp).

## <a name="publish-to-azure"></a>Pubblicare in Azure

- **ASP.NET**, **ASP.NET Core**, **Python** e **Node.js**: è possibile usare lo strumento Pubblicazione per distribuire rapidamente app nel Servizio app di Azure o in una macchina virtuale di Azure. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**. Se in precedenza sono stati configurati profili di pubblicazione, è quindi necessario fare clic su **Crea nuovo profilo**. Nella finestra di dialogo Pubblica scegliere **Servizio app** oppure **Macchine virtuali di Azure** e quindi seguire la procedura di configurazione.

    ![Scegliere Servizio app di Azure](../deployment/media/quickstart-publish-azure.png "Scegliere Servizio app di Azure")

    In Visual Studio 2017 versione 15.7 e successive, è possibile distribuire app ASP.NET Core nel **Servizio app per Linux**.

    Per le app Python, vedere anche [Python: pubblicazione nel Servizio app di Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

    Per una rapida introduzione, vedere [Pubblicare in Azure](quickstart-deploy-to-azure.md) e [Pubblicare in Linux](quickstart-deploy-to-linux.md). Vedere anche [Pubblicare un'app ASP.NET Core in Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Per la distribuzione tramite Git, vedere [Distribuzione continua di ASP.NET Core in Azure con Git](/aspnet/core/publishing/azure-continuous-deployment).

    Per informazioni sull'importazione di un profilo di pubblicazione dal Servizio app di Azure in Visual Studio, vedere [Importare impostazioni di pubblicazione e distribuzione in Azure](../deployment/tutorial-import-publish-settings-azure.md).

    > [!NOTE]
    > Se non si ha ancora un account di Azure, è possibile [iscriversi qui](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Pubblicare nel Web o distribuire in una condivisione di rete

- **ASP.NET**, **ASP.NET Core**, **Node.js** e **Python**: è possibile usare lo strumento Pubblicazione per distribuire un sito Web con FTP o Distribuzione Web. Per altre informazioni, vedere [Distribuire in un sito Web](quickstart-deploy-to-a-web-site.md).

    In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**. Se in precedenza sono stati configurati profili di pubblicazione, è quindi necessario fare clic su **Crea nuovo profilo**. Nello strumento Pubblicazione scegliere l'opzione da usare e seguire la procedura di configurazione.

    ![Scegliere IIS, FTP e così via.](../deployment/media/quickstart-publish-iis-ftp.png)

    Per informazioni sull'importazione di un profilo di pubblicazione in Visual Studio, vedere [Importare impostazioni di pubblicazione e distribuzione in IIS](../deployment/tutorial-import-publish-settings-iis.md).

    È anche possibile distribuire applicazioni ASP.NET e servizi in diversi altri modi. Per altre informazioni, vedere [Deploying ASP.NET web applications and services](http://www.asp.net/aspnet/overview/deployment) (Distribuzione di applicazioni e servizi Web ASP.NET).

- **Runtime di Visual C++**: è possibile distribuire il runtime di Visual C++ tramite distribuzione centralizzata. Per altre informazioni, vedere [Distribuzione di applicazioni desktop native (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp).

- **Desktop di Windows**: è possibile pubblicare un'applicazione desktop di Windows in un server Web o in una condivisione file di rete tramite la distribuzione ClickOnce. Gli utenti possono quindi installare l'applicazione con un solo clic. Per altre informazioni, vedere [Distribuire un'app desktop tramite ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) e [Distribuire un'app nativa tramite ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

## <a name="publish-to-microsoft-store"></a>Pubblicare in Microsoft Store

Da Visual Studio è possibile creare pacchetti di app per la distribuzione in Microsoft Store.

- **Piattaforma UWP**: è possibile creare il pacchetto dell'app e distribuirlo tramite voci di menu. Per altre informazioni, vedere [Creare il pacchetto di un'app UWP con Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Creare un pacchetto dell'app](../deployment/media/feature-tour-create-app-package.jpg)

- **Desktop di Windows**: a partire da Visual Studio 2017 versione 15.4, è possibile eseguire la distribuzione in Microsoft Store tramite Desktop Bridge. A tale scopo, iniziare creando un progetto di creazione del pacchetto dell'applicazione Windows. Per altre informazioni, vedere [Creare il pacchetto di un'app desktop per Microsoft Store (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Desktop Bridge](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Eseguire la distribuzione in un dispositivo (piattaforma UWP)

Se si intende distribuire a scopo di test un'app per la piattaforma UWP in un dispositivo, vedere [Eseguire app per la piattaforma UWP in un computer remoto in Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-client"></a>Creare un pacchetto di installazione (client Windows)

Se è necessaria un'installazione di un'applicazione desktop più complessa di quella offerta da [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md), è possibile creare un pacchetto di installazione, un progetto di installazione o un programma di avvio automatico personalizzato.

- È possibile creare un programma di installazione WiX basato su MSI usando [WiX Toolset Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- È possibile usare [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) di Flexera Software con Visual Studio 2017 (Community Edition non supportata). Si noti che InstallShield Limited Edition non è più incluso in Visual Studio e non è supportato in Visual Studio 2017. Rivolgersi a [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) per informazioni sulla disponibilità futura.

- Se si vuole creare un progetto di installazione (vdproj), installare l'[estensione Visual Studio 2017 Installer Projects](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- È possibile installare i componenti prerequisiti per le applicazioni desktop configurando un programma di installazione generico, noto come programma di avvio automatico. Per altre informazioni, vedere [Prerequisiti per la distribuzione delle applicazioni](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Distribuire a un lab di test

È possibile consentire operazioni più sofisticate di sviluppo e test distribuendo le applicazioni in ambienti virtuali. Per altre informazioni, vedere [Eseguire test in un ambiente lab](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="devops-deployment"></a>Distribuzione DevOps

In un ambiente di team, è possibile usare Azure Pipelines per abilitare la distribuzione continua dell'app. Per altre informazioni, vedere [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) e [Distribuisci in Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deployment-for-other-app-types"></a>Distribuzione di altri tipi di app

| Tipo di app | Scenario di distribuzione | Collegamento |
| --- | --- | --- |
| **App di Office** | È possibile pubblicare un componente aggiuntivo per Office in Visual Studio. | [Deploy and publish your Office add-in](https://dev.office.com/docs/add-ins/publish/publish) (Distribuire e pubblicare un componente aggiuntivo per Office) |
| **Servizio WCF o OData** | I servizi WCF RIA distribuiti in un server Web possono essere usati da altre applicazioni. | [Sviluppo e distribuzione di WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch non è più supportato in Visual Studio 2017, ma può essere comunque distribuito da Visual Studio 2015 e versioni precedenti. | [Deploying LightSwitch Applications](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) (Distribuzione di applicazioni LightSwitch) |

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stata presentata una veloce panoramica delle opzioni di distribuzione per applicazioni diverse.

> [!div class="nextstepaction"]
> [Quali sono le opzioni di pubblicazione più adatte?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
