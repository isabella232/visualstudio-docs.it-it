---
title: Tour delle funzionalità di distribuzione
description: Informazioni sulle opzioni disponibili per la distribuzione di App da Visual Studio.
ms.custom: mvc
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
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
ms.openlocfilehash: 5824876adc75430085ea0f69dc6f01be722526f5
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231226"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Guida introduttiva: Presentazione della distribuzione in Visual Studio

Distribuendo un'applicazione, servizio o componente, viene distribuito per l'installazione in altri computer, dispositivi o i server o nel cloud. Il metodo appropriato viene scelto in Visual Studio per il tipo di distribuzione necessaria. (Molti tipi di app supportano altri strumenti di distribuzione, ad esempio distribuzione da riga di comando o NuGet che non sono descritti di seguito).

Vedere le guide introduttive ed esercitazioni per istruzioni dettagliate di distribuzione. Per una panoramica delle opzioni di distribuzione, vedere [quali sono le opzioni di pubblicazione sono più adatte?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Distribuire in una cartella locale

Distribuzione in una cartella locale in genere viene utilizzata per il test o per iniziare una distribuzione di gestione temporanea in cui viene utilizzato un altro strumento per la distribuzione finale.

- **ASP.NET**, **ASP.NET Core**, **Node. js**, **Python**, e. **NET Core**: usare lo strumento di pubblicazione per la distribuzione in una cartella locale. Le opzioni disponibili variano a seconda del tipo di app. In Esplora soluzioni fare doppio clic il progetto e scegliere **pubblica**. (Se sono stati configurati tutti i profili di pubblicazione, è necessario fare quindi clic **Crea nuovo profilo**.) Scegliere quindi **cartella**. Per altre informazioni, vedere [Distribuisci in una cartella locale](quickstart-deploy-to-local-folder.md).

    ![Scegliere Pubblica](../deployment/media/quickstart-publish.png)

- **Runtime di Visual C++**: È possibile distribuire il runtime di Visual C++ tramite la distribuzione locale o collegamento statico. Per altre informazioni, vedere [distribuzione di applicazioni Desktop Native (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

## <a name="publish-to-azure"></a>Pubblicare in Azure

- **ASP.NET**, **ASP.NET Core**, **Python**, e **Node. js**: È possibile usare lo strumento di pubblicazione per distribuire rapidamente App servizio App di Azure o a un virtuale di Azure Macchina. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**. (Se sono stati configurati tutti i profili di pubblicazione, è necessario fare quindi clic **Crea nuovo profilo**.) Nella finestra di dialogo di pubblicazione, scegliere **servizio App** oppure **macchine virtuali di Azure**e quindi seguire i passaggi di configurazione.

    ![Scegliere servizio App di Azure](../deployment/media/quickstart-publish-azure.png "scegliere servizio App di Azure")

    In Visual Studio 2017 versione 15.7 e successive, è possibile distribuire App ASP.NET Core **servizio App per Linux**.

    Per le app di Python, vedere anche [Python - pubblicazione in servizio App di Azure](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

    Per una rapida introduzione, vedere [Publish to Azure](quickstart-deploy-to-azure.md) e [Publish to Linux](quickstart-deploy-to-linux.md). Vedere anche [pubblicare un'app ASP.NET Core in Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Per la distribuzione tramite Git, vedere [distribuzione continua di ASP.NET Core in Azure con Git](/aspnet/core/publishing/azure-continuous-deployment).

    Per informazioni su come importare un profilo di pubblicazione dal servizio App di Azure per Visual Studio, vedere [importare impostazioni di pubblicazione e distribuzione in Azure](../deployment/tutorial-import-publish-settings-azure.md).

    > [!NOTE]
    > Se non hai già un account Azure, puoi [iscrizione qui](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Pubblicazione sul Web o la distribuzione alla condivisione di rete

- **ASP.NET**, **ASP.NET Core**, **Node. js**, e **Python**: È possibile usare lo strumento di pubblicazione per la distribuzione a un sito Web tramite FTP o distribuzione Web. Per altre informazioni, vedere [Distribuisci in un sito web](quickstart-deploy-to-a-web-site.md).

    In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**. (Se sono stati configurati tutti i profili di pubblicazione, è necessario fare quindi clic **Crea nuovo profilo**.) Nello strumento di pubblicazione, scegliere l'opzione desiderata e seguire i passaggi di configurazione.

    ![Scegliere IIS, FTP e così via.](../deployment/media/quickstart-publish-iis-ftp.png)

    Per informazioni su come importare un profilo di pubblicazione in Visual Studio, vedere [importare impostazioni di pubblicazione e distribuzione in IIS](../deployment/tutorial-import-publish-settings-iis.md).

    È anche possibile distribuire applicazioni ASP.NET e servizi in diversi altri modi. Per altre informazioni, vedere [ASP.NET la distribuzione di applicazioni e servizi web](http://www.asp.net/aspnet/overview/deployment).

- **Runtime di Visual C++**: È possibile distribuire il runtime di Visual C++ con la distribuzione centrale. Per altre informazioni, vedere [distribuzione di applicazioni Desktop Native (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

- **Desktop di Windows** è possibile pubblicare un'applicazione desktop di Windows in un server web o una condivisione di file di rete mediante la distribuzione ClickOnce. Gli utenti possono quindi installare l'applicazione con un solo clic. Per altre informazioni, vedere [distribuire un'app desktop tramite ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) e [distribuire un'app nativa tramite ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

## <a name="publish-to-microsoft-store"></a>Pubblicazione in Microsoft Store

Da Visual Studio, è possibile creare pacchetti di app per la distribuzione in Microsoft Store.

- **Piattaforma UWP**: È possibile pacchetto dell'app e distribuirla tramite le voci di menu. Per altre informazioni, vedere [il pacchetto di un'app UWP tramite Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Creare un pacchetto dell'app](../deployment/media/feature-tour-create-app-package.jpg)

- **Desktop di Windows**: È possibile distribuire in Microsoft Store usando il Desktop Bridge a partire da Visual Studio 2017 versione 15.4. A tale scopo, iniziare creando un progetto di creazione del pacchetto di applicazione Windows. Per altre informazioni, vedere [pacchetto di un'app desktop per Microsoft Store (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Desktop bridge](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Distribuire un dispositivo (UWP)

Se si distribuisce un'app UWP per il test in un dispositivo, vedere [eseguire App UWP in un computer remoto in Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-client"></a>Creare un pacchetto di installazione (client di Windows)

Se sono necessari più di un'installazione di un'applicazione desktop più complessa [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) può fornire, è possibile creare un pacchetto di installazione, un progetto di installazione o un programma di avvio automatico.

- È possibile creare un programma di installazione WiX basata su MSI utilizzando il [WiX set di strumenti di Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) da Flexera Software può essere usato con Visual Studio 2017 (Community Edition non è supportata). Si noti che InstallShield Limited Edition è più incluso in Visual Studio e non è supportato in Visual Studio 2017; Rivolgersi [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) sulla disponibilità futura.

- Se si desidera creare un progetto di installazione (vdproj), installare il [estensione di progetti di programma di installazione di Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- È possibile installare componenti dei prerequisiti per le applicazioni desktop configurando un programma di installazione generico, che è noto come programma di avvio automatico. Per altre informazioni, vedere [prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Distribuire per l'ambiente di prova

È possibile abilitare più sofisticate di sviluppo e test tramite la distribuzione di applicazioni in ambienti virtuali. Per altre informazioni, vedere [Test in un ambiente lab](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="devops-deployment"></a>Distribuzione di DevOps

In un ambiente di team, è possibile usare Visual Studio Team Services (VSTS) per abilitare la distribuzione continua dell'app. Per altre informazioni, vedere [compilazione e versione](/vsts/build-release/index) e [Deploy to Azure](/vsts/deploy-azure/index).

## <a name="deployment-for-other-app-types"></a>Distribuzione per altri tipi di app

| Tipo di app | Scenario di distribuzione | Collegamento |
| --- | --- | --- |
| **App di Office** | È possibile pubblicare un componente aggiuntivo per Office in Visual Studio. | [Distribuire e pubblicare il componente aggiuntivo di Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Servizio WCF o OData**  | Altre applicazioni possono utilizzare servizi WCF RIA distribuiti in un server web. | [Sviluppo e distribuzione di WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch non è più supportato in Visual Studio 2017, ma può essere comunque distribuito da Visual Studio 2015 e versioni precedenti. | [Distribuzione di applicazioni LightSwitch](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione, si ha richiesto di esaminare rapidamente le opzioni di distribuzione per applicazioni diverse.

> [!div class="nextstepaction"]
> [Quali opzioni di pubblicazione sono adatta alle mie esigenze?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
