---
title: Distribuire l'app Visual Studio in una cartella, IIS, Azure o in un'altra destinazione
titleSuffix: ''
description: Altre informazioni sulle opzioni di pubblicazione per l'app con lo strumento Pubblica.
ms.custom:
- SEO-VS-2020
- contperf-fy21q1
ms.date: 08/21/2020
ms.topic: troubleshooting
f1_keywords:
- vs.publish
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: c8ce30c5dded0c247467d47296429412d1a561eb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073890"
---
# <a name="deploy-your-app-to-a-folder-iis-azure-or-another-destination"></a>Distribuire l'app in una cartella, IIS, Azure o in un'altra destinazione

Mediante la distribuzione, un'applicazione, un servizio o un componente viene distribuito per l'installazione in altri computer, dispositivi, server o nel cloud. Il metodo appropriato viene scelto in Visual Studio per il tipo di distribuzione necessaria.

Ottenere assistenza per l'attività di distribuzione:

- Non si è certi dell'opzione di distribuzione da scegliere? Vedere [Quali sono le opzioni di pubblicazione più giuste?](#what-publishing-options-are-right-for-me)
- Per informazioni sui problemi di distribuzione per Servizio app di Azure o IIS, vedere Risolvere i ASP.NET Core [in Servizio app di Azure e IIS.](/aspnet/core/test/troubleshoot-azure-iis)
- Per informazioni sulla configurazione delle impostazioni di distribuzione .NET, vedere [Configurare le impostazioni di distribuzione .NET.](#configure-net-deployment-settings)
- Per eseguire la distribuzione in una nuova destinazione,  se in precedenza è stato creato un profilo di pubblicazione, selezionare Nuovo nella **finestra Pubblica** per un profilo configurato.

   ![Creare un nuovo profilo di pubblicazione](../deployment/media/create-a-new-publish-profile.png)

   Scegliere quindi un'opzione di distribuzione nella finestra Pubblica. Per informazioni sulle opzioni di pubblicazione, vedere le sezioni seguenti.

## <a name="what-publishing-options-are-right-for-me"></a>Quali sono le opzioni di pubblicazione più adatte?

Dall'interno di Visual Studio è possibile pubblicare le applicazioni direttamente nelle destinazioni seguenti:

::: moniker range=">=vs-2019"
- [Azure](#azure)
- [Registro Contenitori Docker](#docker-container-registry)
- [Cartella](#folder)
- [Server FTP/FTPS](#ftpftps-server)
- [Server Web (IIS)](#web-server-iis)
- [Importa profilo](#import-profile)
::: moniker-end
::: moniker range="vs-2017"
- [Servizio app](#azure-app-service)
- [Servizio app in Linux](#azure-app-service)
- [IIS (scegliere IIS, FTP e così via)](#web-server-iis)
- [FTP/FTPS (scegliere IIS, FTP e così via)](#ftpftps-server)
- [Cartella](#folder)
- [Importa profilo](#import-profile)
::: moniker-end

Le opzioni precedenti vengono visualizzate come illustrato nella figura seguente quando si crea un nuovo profilo di pubblicazione.

::: moniker range=">=vs-2019"
![Scegliere un'opzione di pubblicazione](../deployment/media/quickstart-publish-dialog.png)
::: moniker-end
::: moniker range="vs-2017"
![Scegliere un'opzione di pubblicazione](../deployment/media/quickstart-publish-dialog-vs-2017.png)
::: moniker-end

Per una breve panoramica delle opzioni di distribuzione delle applicazioni più generali, vedere [Presentazione della distribuzione.](../deployment/deploying-applications-services-and-components.md)

## <a name="azure"></a>Azure 

Quando si sceglie Azure, è possibile scegliere tra:

- [Servizio app di Azure](#azure-app-service) in esecuzione Windows, Linux o come immagine Docker
- Un'immagine Docker distribuita in [Registro Azure Container](#azure-container-registry)
- Una [macchina virtuale di Azure](#azure-virtual-machine)

![Scegliere un servizio di Azure](../deployment/media/quickstart-choose-azure-service.png)

### <a name="azure-app-service"></a>Servizio app di Azure

[Servizio app di Azure](/azure/app-service/app-service-web-overview) consente agli sviluppatori di creare rapidamente applicazioni e servizi Web scalabili senza gestire l'infrastruttura. Un servizio app viene eseguito nelle macchine virtuali ospitate nel cloud di Azure, ma tali macchine vengono gestite automaticamente. A ogni app di un servizio app viene assegnato un URL \*.azurewebsites.net univoco. Tutti i piani tariffari diversi da quello gratuito consentono l'assegnazione di nomi di dominio personalizzati al sito.

Per determinare la potenza di calcolo di un servizio app, scegliere un [piano tariffario](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) per il servizio app che lo contiene. È possibile fare in modo che più app Web (e altri tipi di app) condividano lo stesso servizio app senza modificare il piano tariffario. È ad esempio possibile ospitare insieme app Web di sviluppo, gestione temporanea e produzione nello stesso servizio app.

#### <a name="when-to-choose-azure-app-service"></a>Quando scegliere Servizio App di Azure

- Si vuole distribuire un'applicazione Web accessibile via Internet.
- Si vuole adeguare automaticamente l'applicazione Web in base alla richiesta senza doverla ridistribuire.
- Non si vuole gestire l'infrastruttura di server, inclusi gli aggiornamenti software.
- Non sono necessarie personalizzazioni a livello di computer sui server che ospitano l'applicazione Web.

> Per usare Servizio app di Azure nel proprio centro dati o in altri computer locali, usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Per altre informazioni sulla pubblicazione nel servizio app, vedere:
- [Avvio rapido: Pubblicare in Servizio app di Azure](quickstart-deploy-to-azure.md)
- [Avvio rapido: Pubblicare ASP.NET Core in Linux.](quickstart-deploy-to-linux.md)
- [Pubblicare un ASP.NET Core app in Servizio app di Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Risolvere i ASP.NET Core in Servizio app di Azure e IIS.](/aspnet/core/test/troubleshoot-azure-iis)

### <a name="azure-container-registry"></a>Registro Azure Container

[Registro Azure Container](/azure/container-registry/) consente di creare, archiviare e gestire elementi e immagini del contenitore Docker in un registro privato per tutti i tipi di distribuzioni di contenitori.

#### <a name="when-to-choose-azure-container-registry"></a>Quando scegliere Registro Azure Container

- Quando si ha una pipeline di sviluppo e distribuzione di contenitori Docker esistente.
- Quando si vogliono compilare immagini del contenitore Docker in Azure.

Per altre informazioni:

- [Distribuire un contenitore ASP.NET contenitore in un registro contenitori](../containers/hosting-web-apps-in-docker.md)

### <a name="azure-virtual-machine"></a>Macchina virtuale di Azure

[Macchine virtuali (VM) di Azure](https://azure.microsoft.com/documentation/services/virtual-machines/) consente di creare e gestire un numero qualsiasi di risorse di calcolo nel cloud. Assumendosi la responsabilità per tutto il software e tutti gli aggiornamenti nelle macchine virtuali, è possibile personalizzare queste ultime in base alle esigenze dell'applicazione. È possibile accedere alle macchine virtuali direttamente con Desktop remoto e ognuna di esse manterrà l'indirizzo IP assegnato finché lo si ritiene opportuno.

Il ridimensionamento di un'applicazione ospitata in macchine virtuali comporta l'attivazione di altre macchine virtuali in base alla richiesta e quindi la distribuzione del software necessario. Questo livello di controllo aggiuntivo consente di ridimensionare le macchine in modo diverso nelle diverse aree geografiche globali. Se ad esempio l'applicazione viene usata da dipendenti dislocati in varie sedi regionali, è possibile ridimensionare le macchine virtuali in base al numero di dipendenti di quelle sedi, potenzialmente riducendo i costi.

Per altre informazioni, [](/azure/architecture/guide/technology-choices/compute-decision-tree) vedere il confronto dettagliato tra Servizio app di Azure, Macchine virtuali di Azure e altri servizi di Azure che è possibile usare come destinazione di distribuzione usando l'opzione Personalizzata in Visual Studio.

#### <a name="when-to-choose-azure-virtual-machines"></a>Quando scegliere macchine virtuali di Azure

- Si vuole distribuire un'applicazione Web accessibile via Internet, con controllo completo della durata degli indirizzi IP assegnati.
- Sono necessarie personalizzazioni a livello di computer nei server, che includono software aggiuntivo, ad esempio un sistema di database specializzato, configurazioni di rete specifiche, partizioni del disco e così via.
- Si vuole garantire un elevato livello di controllo sul ridimensionamento dell'applicazione Web.
- È necessario l'accesso diretto ai server che ospitano l'applicazione per qualsiasi altro motivo.

> Per usare le macchine virtuali di Azure nel proprio centro dati o in altri computer locali, usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="docker-container-registry"></a>Registro contenitori di Docker

Se l'applicazione usa Docker, è possibile pubblicare l'applicazione in contenitori in un registro contenitori Docker.

### <a name="when-to-choose-docker-container-registry"></a>Quando scegliere Docker Container Registry

- Si vuole distribuire un'applicazione in contenitori

Per altre informazioni, vedere gli argomenti seguenti:

- [Distribuire un contenitore ASP.NET contenitore in un registro contenitori](../containers/hosting-web-apps-in-docker.md)
- [Distribuire in Docker Hub](../containers/deploy-docker-hub.md)

## <a name="folder"></a>Cartella

La distribuzione nel file system significa copiare i file dell'applicazione in una cartella specifica nel proprio computer. La distribuzione in una cartella viene spesso usata a scopo di test o per distribuire l'applicazione per l'uso da parte di un numero limitato di utenti se il computer esegue anche un server. Se la cartella di destinazione è condivisa in rete, la distribuzione nel file system può rendere disponibili i file dell'applicazione Web per altri utenti che possono distribuirli a loro volta a server specifici.
::: moniker range=">=vs-2019"
A partire da Visual Studio 2019 16.8, la destinazione cartella include la possibilità di pubblicare un'applicazione .NET Windows usando ClickOnce.

Se si vuole pubblicare un'applicazione .NET Core 3.1 o versione più recente con Windows con ClickOnce, vedere Distribuire un'applicazione [.NET Windows usando ClickOnce](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end
Qualsiasi computer locale che esegue un server è in grado di rendere l'applicazione disponibile su Internet o Intranet, in base al tipo di configurazione e alle reti a cui è connesso. Se si connette un computer direttamente a Internet, prestare particolare attenzione a proteggerlo da minacce alla sicurezza esterne. Poiché si gestiscono questi computer, si ha il controllo completo delle configurazioni software e hardware.

Se per qualsiasi motivo, ad esempio l'accesso ai computer, non è possibile usare servizi [](https://azure.microsoft.com/overview/azure-stack/) cloud come Servizio app di Azure o Macchine virtuali di Azure, è possibile usare il Azure Stack nel proprio data center. Azure Stack consente di gestire e usare le risorse di elaborazione con Servizio app di Azure e Macchine virtuali di Azure, mantenendo tutti gli elementi in locale.

### <a name="when-to-choose-file-system-deployment"></a>Quando scegliere la distribuzione nel file system

- È necessario distribuire l'applicazione solo in una condivisione di file da cui altri utenti effettueranno a loro volta la distribuzione a server diversi.
::: moniker range=">=vs-2019"
- Si vuole distribuire un'applicazione .NET Windows usando ClickOnce
::: moniker-end
- È necessaria solo una distribuzione locale dei test.
- Si vuole esaminare e potenzialmente modificare in modo indipendente i file dell'applicazione prima di inviarli a un'altra destinazione di distribuzione.

Per altre informazioni, vedere [Avvio rapido - Distribuire in una cartella locale.](quickstart-deploy-to-local-folder.md)
::: moniker range=">=vs-2019"
Per altre informazioni sulla distribuzione di un'applicazione .NET Windows usando ClickOnce, vedere Distribuire un'applicazione [.NET Windows usando ClickOnce](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end

Per altre informazioni sulla scelta delle impostazioni, vedere quanto segue:

- [Distribuzione dipendente dal framework e distribuzione autonoma](/dotnet/core/deploying/)
- [Identificatori di runtime di destinazione (RID portabile e altri)](/dotnet/core/rid-catalog)
- [Configurazioni di debug e versione](../ide/understanding-build-configurations.md)

## <a name="ftpftps-server"></a>Server FTP/FTPS

Un server FTP/FTPS consente di distribuire l'applicazione in un server diverso da Azure. È possibile distribuire l'applicazione a un file system o qualsiasi altro server (Internet o Intranet) a cui si ha accesso, inclusi quelli presenti in altri servizi cloud. È anche possibile usare una distribuzione Web (file o .ZIP) e FTP.

Quando si sceglie un server FTP/FTPS, Visual Studio richiede un nome di  profilo e quindi raccoglie informazioni aggiuntive sulla connessione, tra cui il server di destinazione o il percorso, un nome del sito e le credenziali. È possibile controllare i comportamenti seguenti nella scheda **Impostazioni**:

- La configurazione da distribuire.
- Se rimuovere i file esistenti dalla destinazione.
- Se precompilare durante la pubblicazione.
- Se escludere i file nella cartella App_Data dalla distribuzione.

È possibile creare un numero qualsiasi di profili di distribuzione FTP/FTPS in Visual Studio, rendendo possibile la gestione dei profili con impostazioni diverse.

### <a name="when-to-choose-ftpftps-server-deployment"></a>Quando scegliere la distribuzione del server FTP/FTPS

- Se si usano servizi cloud di un provider diverso da Azure a cui è possibile accedere con URL.
- Si vuole eseguire la distribuzione usando credenziali diverse da quelle usate in Visual Studio o quelle associate direttamente all'account Azure.
- Si vuole eliminare i file dalla destinazione ogni volta che si esegue la distribuzione.

## <a name="web-server-iis"></a>Server Web (IIS)

Un server Web IIS consente di distribuire l'applicazione in un server Web diverso da Azure. Può essere distribuito in un server IIS (Internet o Intranet) a cui si ha accesso, inclusi quelli in altri servizi cloud. Può funzionare con un Distribuzione Web o un Distribuzione Web pacchetto.

Quando si sceglie un server Web IIS, Visual Studio richiede un nome di  profilo e quindi raccoglie informazioni aggiuntive sulla connessione, tra cui il server di destinazione o il percorso, un nome del sito e le credenziali. È possibile controllare i comportamenti seguenti nella scheda **Impostazioni**:

- La configurazione da distribuire.
- Se rimuovere i file esistenti dalla destinazione.
- Se precompilare durante la pubblicazione.
- Se escludere i file nella cartella App_Data dalla distribuzione.

È possibile creare un numero qualsiasi di profili di distribuzione del server Web IIS in Visual Studio, rendendo possibile la gestione dei profili con impostazioni diverse.

### <a name="when-to-choose-web-server-iis-deployment"></a>Quando scegliere la distribuzione del server Web (IIS)

- Si usa IIS per pubblicare un sito o un servizio accessibile tramite URL.
- Si vuole eseguire la distribuzione usando credenziali diverse da quelle usate in Visual Studio o quelle associate direttamente all'account Azure.
- Si vuole eliminare i file dalla destinazione ogni volta che si esegue la distribuzione.

Per altre informazioni, vedere [Avvio rapido - Distribuire in un sito Web.](quickstart-deploy-to-a-web-site.md)

Per informazioni sulla risoluzione dei ASP.NET Core in IIS, vedere Risolvere i ASP.NET Core [in Servizio app di Azure e IIS.](/aspnet/core/test/troubleshoot-azure-iis)

## <a name="import-profile"></a>Importa profilo

È possibile importare un profilo durante la pubblicazione in IIS o Servizio app di Azure. È possibile configurare la distribuzione usando un *file di impostazioni di pubblicazione* (*\* .publishsettings*). Il file delle impostazioni di pubblicazione viene creato da IIS o dal servizio app di Azure oppure può essere creato manualmente e quindi importato in Visual Studio.

L'uso di un file di impostazioni di pubblicazione può semplificare la configurazione della distribuzione e funziona meglio in un ambiente di team anziché configurare manualmente ogni profilo di distribuzione.

### <a name="when-to-choose-import-profile"></a>Quando scegliere il profilo di importazione

- Si esegue la pubblicazione in IIS e si vuole semplificare la configurazione della distribuzione.
- Si esegue la pubblicazione in IIS o Servizio app di Azure e si vuole velocizzare la configurazione della distribuzione per il riutilizzo o per i membri del team che pubblicano nello stesso servizio.

Per altre informazioni, vedere gli argomenti seguenti:

- [Importare impostazioni di pubblicazione ed eseguire la distribuzione in IIS](tutorial-import-publish-settings-iis.md)
- [Importare impostazioni di pubblicazione e distribuzione in Azure](tutorial-import-publish-settings-azure.md)

## <a name="configure-net-deployment-settings"></a>Configurare le impostazioni di distribuzione .NET

Per altre informazioni sulla scelta delle impostazioni, vedere quanto segue:

- [Distribuzione dipendente dal framework e distribuzione autonoma](/dotnet/core/deploying/)
- [Identificatori di runtime di destinazione (RID portabile e altri)](/dotnet/core/rid-catalog)
- [Configurazioni di debug e versione](../ide/understanding-build-configurations.md)

## <a name="next-steps"></a>Passaggi successivi

Esercitazioni:

- [Distribuire un'applicazione .NET Core con lo strumento di pubblicazione](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Pubblicare un ASP.NET app core in Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Distribuzione in Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Distribuire app per la piattaforma UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Pubblicare un'app Node.js in Azure con Distribuzione Web](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Pubblicare un'app Python in Servizio app di Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
