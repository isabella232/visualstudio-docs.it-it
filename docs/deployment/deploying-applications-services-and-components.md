---
title: Presentazione della distribuzione
description: Informazioni sulle opzioni per la distribuzione di app da Visual Studio.
ms.custom: mvc
ms.date: 09/23/2021
ms.topic: conceptual
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: ace4dd25eb82d8e1aaf96b40ada6308d6e90fbf7
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431653"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Presentazione della distribuzione in Visual Studio

Mediante la distribuzione, un'applicazione, un servizio o un componente viene distribuito per l'installazione in altri computer, dispositivi o server, oppure nel cloud. Il metodo appropriato viene scelto in Visual Studio per il tipo di distribuzione necessaria. Molti tipi di app supportano altri strumenti di distribuzione, ad esempio la distribuzione da riga di comando o NuGet, che non sono descritti qui.

Per istruzioni dettagliate sulla distribuzione, vedere le guide introduttive e le esercitazioni. Per una panoramica delle opzioni di distribuzione, vedere [Quali sono le opzioni di pubblicazione più adatte?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-a-local-folder"></a>Distribuire in una cartella locale

La distribuzione in una cartella locale viene in genere usata per il test o per avviare una distribuzione a fasi in cui viene usato un altro strumento per la distribuzione finale.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python** e . **NET Core:** usare lo **strumento Pubblica** per eseguire la distribuzione in una cartella locale. Le opzioni disponibili variano a seconda del tipo di app. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Pubblica**. Se in precedenza non sono stati configurati profili di pubblicazione, è necessario selezionare **Crea nuovo profilo.** Selezionare quindi **Cartella**. Per altre informazioni, vedere [Distribuire in una cartella locale](quickstart-deploy-to-local-folder.md).

    ![Screenshot che mostra la selezione di Pubblica.](../deployment/media/quickstart-publish.png)

- **Windows desktop:** è possibile pubblicare un Windows app applicazione desktop in una cartella usando ClickOnce distribuzione. Gli utenti possono quindi installare l'applicazione con un solo clic. Per altre informazioni, vedere gli articoli seguenti:

  - [Distribuire un'app desktop Windows .NET usando ClickOnce](quickstart-deploy-using-clickonce-folder.md)
  - [Distribuire un'app desktop .NET Framework Windows usando ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md).
  - [Distribuire un'app desktop Windows .NET usando ClickOnce](quickstart-deploy-using-clickonce-folder.md).
  - [Distribuire un'app C++/CLR usando ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) o, per C/C++, vedere Distribuire un'app nativa usando un progetto [di installazione.](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)

## <a name="publish-to-azure"></a>Eseguire la pubblicazione in Azure

- **ASP.NET**, **ASP.NET Core**, **Python** e **Node.js**: pubblicare in Servizio app di Azure o Servizio app di Azure in Linux (usando contenitori) usando uno dei metodi seguenti:

  - Per una distribuzione di app continua o automatica, usare Azure DevOps con [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).
  - Per una distribuzione di app una tantum o manuale, usare lo strumento **Pubblica** in Visual Studio.
  - Per creare flussi GitHub di lavoro di ASP.NET e di funzioni di Azure ospitati in GitHub.com, vedere Distribuire in Azure usando GitHub [azioni.](../deployment/azure-deployment-using-github-actions.md)

  Per la distribuzione che offre una configurazione più personalizzata del server, è anche possibile usare lo strumento **Pubblica** per distribuire le app in una macchina virtuale di Azure.

  Per usare lo strumento **Pubblica,** fare clic con il pulsante destro del mouse sul Esplora soluzioni e **scegliere Pubblica.** Se in precedenza sono stati configurati profili di pubblicazione, è necessario selezionare **Crea nuovo profilo.** Nella finestra **di** dialogo Pubblica selezionare Servizio **app o** Macchine virtuali **di Azure** e quindi seguire i passaggi di configurazione.

  ![Screenshot che mostra la selezione Servizio app di Azure.](../deployment/media/quickstart-publish-azure-new.png "Scegliere Servizio app di Azure")

  A partire Visual Studio 2017 versione 15.7, è possibile distribuire ASP.NET Core app in Servizio app in Linux.

  Per le app Python, vedere anche [Python: pubblicazione nel Servizio app di Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Per una rapida introduzione, vedere [Pubblicare in Azure](quickstart-deploy-to-azure.md) e [Pubblicare in Linux](quickstart-deploy-to-linux.md). Vedere anche [Pubblicare un'app ASP.NET Core in Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Per la distribuzione tramite Git, vedere [Distribuzione continua di ASP.NET Core in Azure con Git](/azure/app-service/deploy-continuous-deployment).

  > [!NOTE]
  > Se non si ha già un account Azure, è possibile [iscriversi qui.](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio)

## <a name="publish-to-the-web-or-deploy-to-a-network-share"></a>Pubblicare sul Web o distribuire in una condivisione di rete

- **ASP.NET**, **ASP.NET Core**, **Node.js** e **Python:** è possibile usare  lo strumento Pubblica per eseguire la distribuzione in un sito Web tramite FTP o Distribuzione Web. Per altre informazioni, vedere [Distribuire in un sito Web.](quickstart-deploy-to-a-web-site.md)

    In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica.** Se in precedenza sono stati configurati profili di pubblicazione, è necessario selezionare **Crea nuovo profilo.** Nello strumento **Pubblica** selezionare l'opzione desiderata e seguire i passaggi di configurazione.

    ![Screenshot che mostra la selezione di IIS.](../deployment/media/quickstart-publish-iis.png)

    Per informazioni sull'importazione di un profilo di pubblicazione in Visual Studio, vedere [Importare impostazioni di pubblicazione e distribuzione in IIS](../deployment/tutorial-import-publish-settings-iis.md).

    È anche possibile distribuire applicazioni ASP.NET e servizi in diversi altri modi. Per altre informazioni, vedere [Deploying ASP.NET web applications and services](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/) (Distribuzione di applicazioni e servizi Web ASP.NET).

- **Windows desktop:** è possibile pubblicare un'applicazione desktop Windows in un server Web o in una condivisione file di rete usando ClickOnce distribuzione. Gli utenti possono quindi installare l'applicazione con un solo clic. Per altre informazioni, vedere gli articoli seguenti:

  - [Distribuire un.NET Framework Windows app desktop con ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
  - [Distribuire un'app desktop Windows .NET usando ClickOnce](quickstart-deploy-using-clickonce-folder.md)
  - [Distribuire un'app C++/CLR usando ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)

## <a name="create-an-installer-package-windows-desktop"></a>Creare un pacchetto del programma di installazione (desktop di Windows)

Se è necessaria un'installazione più complessa di un'applicazione desktop rispetto a quanto ClickOnce possa fornire, è possibile creare un pacchetto del programma di installazione di Windows (file di installazione MSI o EXE) o un programma di avvio automatico personalizzato.

- È possibile creare un pacchetto del programma di installazione basato su MSI usando [wix toolset Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension). Si tratta di un set di strumenti da riga di comando.

- È possibile creare un pacchetto di installazione MSI o EXE usando un progetto di installazione (vdproj). Per usare questa opzione, vedere Estensione progetti Programma di installazione di Visual Studio e [.NET Core 3.1 e .NET 5.0](../deployment/installer-projects-net-core.md) oppure passare direttamente all'estensione [Programma di installazione di Visual Studio Projects.](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)

- È possibile creare un pacchetto di installazione MSI o EXE usando [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) di Flexera Software. InstallShield può essere usato con Visual Studio 2017 e versioni successive. Community L'edizione non è supportata.

  > [!NOTE]
  > InstallShield Limited Edition non è più incluso in Visual Studio e non è supportato in Visual Studio 2017 e versioni successive. Verificare con [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) la disponibilità futura.

- È anche possibile installare i componenti prerequisiti per le applicazioni desktop configurando un programma di installazione generico, noto come programma di avvio automatico. Per altre informazioni, vedere Prerequisiti [per la distribuzione di applicazioni.](../deployment/application-deployment-prerequisites.md)

## <a name="publish-to-microsoft-store"></a>Pubblicare in Microsoft Store

Da Visual Studio è possibile creare pacchetti di app per la distribuzione in Microsoft Store.

- **UWP:** è possibile creare un pacchetto dell'app e distribuirla usando voci di menu. Per altre informazioni, vedere [Creare il pacchetto di un'app UWP con Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Screenshot che mostra la creazione di un pacchetto dell'app.](../deployment/media/feature-tour-create-app-package.png)

- **Windows desktop:** è possibile eseguire la distribuzione in Microsoft Store usando il Desktop Bridge a partire Visual Studio 2017 versione 15.4. A tale scopo, iniziare creando un progetto di creazione del pacchetto dell'applicazione Windows. Per altre informazioni, vedere [Creare il pacchetto di un'app desktop per Microsoft Store (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Screenshot che mostra la selezione Windows creazione di pacchetti dell Project.](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Eseguire la distribuzione in un dispositivo (piattaforma UWP)

Se si distribuisce un'app UWP per il test in un dispositivo, vedere Eseguire [app UWP in un computer remoto in Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="deploy-to-a-test-lab"></a>Eseguire la distribuzione in un lab di test

È possibile consentire operazioni più sofisticate di sviluppo e test distribuendo le applicazioni in ambienti virtuali. Per altre informazioni, vedere [Eseguire test in un ambiente lab](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Distribuzione continua

È possibile usare Azure Pipelines per abilitare la distribuzione continua dell'app. Per altre informazioni, vedere [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true) e [Distribuisci in Azure](/azure/devops/deploy-azure/index?view=vsts&preserve-view=true).

## <a name="deploy-a-sql-database"></a>Distribuire un database SQL

- [Modificare la piattaforma di destinazione e pubblicare un progetto di database (SQL Server Data Tools (SSDT))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)
- [Distribuire un progetto di Analysis Services (SSAS)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)
- [Distribuire progetti e pacchetti di Integration Services (SSIS)](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)
- [Compilare e distribuire in un database locale](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Distribuzione di altri tipi di app

| Tipo di app | Scenario di distribuzione | Collegamento |
| --- | --- | --- |
| **App di Office** | È possibile pubblicare un componente aggiuntivo per Office in Visual Studio. | [Deploy and publish your Office add-in](/office/dev/add-ins/publish/publish) (Distribuire e pubblicare un componente aggiuntivo per Office) |
| **Servizio WCF o OData** | I servizi WCF RIA distribuiti in un server Web possono essere usati da altre applicazioni. | [Sviluppo e distribuzione di WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch non è più supportato a partire da Visual Studio 2017, ma può essere comunque distribuito da Visual Studio 2015 e versioni precedenti. | [Distribuzione di applicazioni LightSwitch](/previous-versions/ff872288(v=vs.140)) |

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stata presentata una veloce panoramica delle opzioni di distribuzione per applicazioni diverse.

> [!div class="nextstepaction"]
> [Quali sono le opzioni di pubblicazione più adatte?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)