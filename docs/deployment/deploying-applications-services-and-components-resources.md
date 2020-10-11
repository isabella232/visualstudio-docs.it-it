---
title: Distribuire l'app di Visual Studio in una cartella, IIS, Azure o un'altra destinazione
titleSuffix: ''
description: Altre informazioni sulle opzioni di pubblicazione per l'app tramite la pubblicazione guidata
ms.custom: contperfq1
ms.date: 08/21/2020
ms.topic: troubleshooting
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bc551a6e9bf4e05db61ddeb2480e218ebb3c925
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928528"
---
# <a name="deploy-your-app-to-a-folder-iis-azure-or-another-destination"></a>Distribuire l'app in una cartella, IIS, Azure o un'altra destinazione

Mediante la distribuzione, un'applicazione, un servizio o un componente viene distribuito per l'installazione in altri computer, dispositivi, server o nel cloud. Il metodo appropriato viene scelto in Visual Studio per il tipo di distribuzione necessaria.

Ottenere la guida per l'attività di distribuzione:

- Non si è certi dell'opzione di distribuzione da scegliere? Scopri [quali sono le opzioni di pubblicazione più adatte?](#what-publishing-options-are-right-for-me)
- Per informazioni sui problemi di distribuzione per app Azure Service o IIS, vedere la pagina [relativa alla risoluzione dei problemi ASP.NET Core su app Azure Service e IIS](/aspnet/core/test/troubleshoot-azure-iis).
- Per informazioni sulla configurazione delle impostazioni di distribuzione .NET, vedere [configurare le impostazioni di distribuzione .NET](#configure-net-deployment-settings).
- Per eseguire la distribuzione in una nuova destinazione, se in precedenza è stato creato un profilo di pubblicazione, selezionare **nuovo** dalla finestra **pubblica** per un profilo configurato.

   ![Crea un nuovo profilo di pubblicazione](../deployment/media/create-a-new-publish-profile.png)

   Quindi, scegliere un'opzione di distribuzione nella finestra pubblica. Per informazioni sulle opzioni di pubblicazione, vedere le sezioni seguenti.

## <a name="what-publishing-options-are-right-for-me"></a>Quali sono le opzioni di pubblicazione più adatte?

Dall'interno di Visual Studio è possibile pubblicare le applicazioni direttamente nelle destinazioni seguenti:

::: moniker range=">=vs-2019"
- [Azure](#azure)
- [Container Registry Docker](#docker-container-registry)
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

Per una rapida panoramica delle opzioni di distribuzione delle applicazioni più generali, vedere la pagina relativa [alla distribuzione](../deployment/deploying-applications-services-and-components.md).

## <a name="azure"></a>Azure 

Quando si sceglie Azure, è possibile scegliere tra:

- [Servizio app Azure](#azure-app-service) in esecuzione in Windows, Linux o come immagine Docker
- Un'immagine Docker distribuita in [Azure container Registry](#azure-container-registry)
- Una [macchina virtuale di Azure](#azure-virtual-machine)

![Scegliere un servizio di Azure](../deployment/media/quickstart-choose-azure-service.png)

### <a name="azure-app-service"></a>Servizio app di Azure

[App Azure servizio](/azure/app-service/app-service-web-overview) consente agli sviluppatori di creare rapidamente servizi e applicazioni Web scalabili senza gestire l'infrastruttura. Un servizio app viene eseguito nelle macchine virtuali ospitate nel cloud di Azure, ma tali macchine vengono gestite automaticamente. A ogni app di un servizio app viene assegnato un URL \*.azurewebsites.net univoco. Tutti i piani tariffari diversi da quello gratuito consentono l'assegnazione di nomi di dominio personalizzati al sito.

Per determinare la potenza di calcolo di un servizio app, scegliere un [piano tariffario](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) per il servizio app che lo contiene. È possibile fare in modo che più app Web (e altri tipi di app) condividano lo stesso servizio app senza modificare il piano tariffario. È ad esempio possibile ospitare insieme app Web di sviluppo, gestione temporanea e produzione nello stesso servizio app.

#### <a name="when-to-choose-azure-app-service"></a>Quando scegliere Servizio App di Azure

- Si vuole distribuire un'applicazione Web accessibile via Internet.
- Si vuole adeguare automaticamente l'applicazione Web in base alla richiesta senza doverla ridistribuire.
- Non si vuole gestire l'infrastruttura di server, inclusi gli aggiornamenti software.
- Non sono necessarie personalizzazioni a livello di computer sui server che ospitano l'applicazione Web.

> Per usare Servizio app di Azure nel proprio centro dati o in altri computer locali, usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Per ulteriori informazioni sulla pubblicazione nel servizio app, vedere:
- [Guida introduttiva-pubblicare nel servizio app Azure](quickstart-deploy-to-azure.md)
- [Guida introduttiva: pubblicare ASP.NET Core in Linux](quickstart-deploy-to-linux.md).
- [Pubblicare un'app ASP.NET Core in app Azure servizio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Risolvere i problemi relativi a ASP.NET Core in app Azure servizio e IIS](/aspnet/core/test/troubleshoot-azure-iis).

### <a name="azure-container-registry"></a>Registro Azure Container

[Azure container Registry](/azure/container-registry/) consente di creare, archiviare e gestire le immagini del contenitore Docker e gli artefatti in un registro privato per tutti i tipi di distribuzioni di contenitori.

#### <a name="when-to-choose-azure-container-registry"></a>Quando scegliere Container Registry di Azure

- Quando si dispone di una pipeline di sviluppo e distribuzione di un contenitore Docker esistente.
- Quando si vuole compilare immagini del contenitore Docker in Azure.

Per altre informazioni:

- [Distribuire un contenitore ASP.NET in un registro contenitori](../containers/hosting-web-apps-in-docker.md)

### <a name="azure-virtual-machine"></a>Macchina virtuale di Azure

Le [macchine virtuali (VM) di Azure](https://azure.microsoft.com/documentation/services/virtual-machines/) consentono di creare e gestire qualsiasi numero di risorse di elaborazione nel cloud. Assumendosi la responsabilità per tutto il software e tutti gli aggiornamenti nelle macchine virtuali, è possibile personalizzare queste ultime in base alle esigenze dell'applicazione. È possibile accedere alle macchine virtuali direttamente con Desktop remoto e ognuna di esse manterrà l'indirizzo IP assegnato finché lo si ritiene opportuno.

Il ridimensionamento di un'applicazione ospitata in macchine virtuali comporta l'attivazione di altre macchine virtuali in base alla richiesta e quindi la distribuzione del software necessario. Questo livello di controllo aggiuntivo consente di ridimensionare le macchine in modo diverso nelle diverse aree geografiche globali. Se ad esempio l'applicazione viene usata da dipendenti dislocati in varie sedi regionali, è possibile ridimensionare le macchine virtuali in base al numero di dipendenti di quelle sedi, potenzialmente riducendo i costi.

Per altre informazioni, vedere il [confronto dettagliato](/azure/architecture/guide/technology-choices/compute-decision-tree) tra Servizio app di Azure, Macchine virtuali di Azure e altri servizi di Azure che è possibile usare come destinazione della distribuzione usando l'opzione Personalizzata in Visual Studio.

#### <a name="when-to-choose-azure-virtual-machines"></a>Quando scegliere macchine virtuali di Azure

- Si vuole distribuire un'applicazione Web accessibile via Internet, con controllo completo della durata degli indirizzi IP assegnati.
- Sono necessarie personalizzazioni a livello di computer sui server, che includono software aggiuntivo come ad esempio un sistema di database specializzato, configurazioni di rete specifiche, partizioni del disco e così via.
- Si vuole garantire un elevato livello di controllo sul ridimensionamento dell'applicazione Web.
- È necessario l'accesso diretto ai server che ospitano l'applicazione per qualsiasi altro motivo.

> Per usare le macchine virtuali di Azure nel proprio centro dati o in altri computer locali, usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="docker-container-registry"></a>Registro contenitori di Docker

Se l'applicazione usa Docker, è possibile pubblicare l'applicazione in contenitori in un registro contenitori docker.

### <a name="when-to-choose-docker-container-registry"></a>Quando scegliere Docker Container Registry

- Si vuole distribuire un'applicazione in contenitori

Per altre informazioni, vedere gli argomenti seguenti:

- [Distribuire un contenitore ASP.NET in un registro contenitori](../containers/hosting-web-apps-in-docker.md)
- [Distribuire in Docker Hub](../containers/deploy-docker-hub.md)

## <a name="folder"></a>Cartella

Effettuare la distribuzione nel file system significa semplicemente copiare i file dell'applicazione in una cartella specifica del proprio computer. Questo sistema viene spesso usato a scopo di test o per distribuire l'applicazione per l'uso da parte di un numero limitato di persone, se il computer esegue anche un server. Se la cartella di destinazione è condivisa in rete, la distribuzione nel file system può rendere disponibili i file dell'applicazione Web per altri utenti che possono distribuirli a loro volta a server specifici.

Qualsiasi computer locale che esegue un server è in grado di rendere l'applicazione disponibile su Internet o Intranet, in base al tipo di configurazione e alle reti a cui è connesso. Se si connette un computer direttamente a Internet, prestare particolare attenzione a proteggerlo dalle minacce alla sicurezza esterna. Poiché si gestiscono questi computer, si ha il controllo completo delle configurazioni software e hardware.

Si noti che se per qualsiasi motivo (ad esempio, l'accesso al computer) non si è in grado di usare servizi cloud come Servizio app di Azure o Macchine virtuali di Azure, è possibile usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) nel proprio centro dati. Azure Stack consente di gestire e usare le risorse di elaborazione con Servizio app di Azure e Macchine virtuali di Azure, mantenendo tutti gli elementi in locale.

### <a name="when-to-choose-file-system-deployment"></a>Quando scegliere la distribuzione nel file system

- È necessario distribuire l'applicazione solo in una condivisione di file da cui altri utenti effettueranno a loro volta la distribuzione a server diversi.
- È necessaria solo una distribuzione locale dei test.
- Si vuole esaminare e potenzialmente modificare in modo indipendente i file dell'applicazione prima di inviarli a un'altra destinazione di distribuzione.

Per ulteriori informazioni, vedere [Guida introduttiva: eseguire la distribuzione in una cartella locale](quickstart-deploy-to-local-folder.md).

Per ulteriori informazioni sulla scelta delle impostazioni, vedere gli argomenti seguenti:

- [Distribuzione autonoma e dipendente dal Framework](/dotnet/core/deploying/)
- [Identificatori di runtime di destinazione (RID portatile, et al)](/dotnet/core/rid-catalog)
- [Configurazioni di debug e di rilascio](../ide/understanding-build-configurations.md)

## <a name="ftpftps-server"></a>Server FTP/FTPS

Un server FTP/FTPS consente di distribuire l'applicazione in un server diverso da Azure. È possibile distribuire l'applicazione a un file system o qualsiasi altro server (Internet o Intranet) a cui si ha accesso, inclusi quelli presenti in altri servizi cloud. È anche possibile usare una distribuzione Web (file o .ZIP) e FTP.

Quando si sceglie un server FTP/FTPS, Visual Studio richiede un nome di profilo, quindi raccoglie informazioni aggiuntive sulla **connessione** , tra cui il server o il percorso di destinazione, il nome di un sito e le credenziali. È possibile controllare i comportamenti seguenti nella scheda **Impostazioni**:

- La configurazione da distribuire.
- Se rimuovere i file esistenti dalla destinazione.
- Se precompilare durante la pubblicazione.
- Se escludere i file nella cartella App_Data dalla distribuzione.

È possibile creare qualsiasi numero di profili di distribuzione FTP/FTPS in Visual Studio, rendendo possibile la gestione dei profili con impostazioni diverse.

### <a name="when-to-choose-ftpftps-server-deployment"></a>Quando scegliere la distribuzione del server FTP/FTPS

- Se si usano servizi cloud di un provider diverso da Azure a cui è possibile accedere con URL.
- Si vuole eseguire la distribuzione usando credenziali diverse da quelle usate in Visual Studio o quelle associate direttamente all'account Azure.
- Si vuole eliminare i file dalla destinazione ogni volta che si esegue la distribuzione.

## <a name="web-server-iis"></a>Server Web (IIS)

Un server Web IIS consente di distribuire l'applicazione in un server Web diverso da Azure. Può essere distribuito in un server IIS (Internet o Intranet) a cui si ha accesso, inclusi quelli in altri servizi cloud. Può funzionare con Distribuzione Web o un pacchetto di Distribuzione Web.

Quando si sceglie un server Web IIS, Visual Studio richiede un nome di profilo, quindi raccoglie informazioni aggiuntive sulla **connessione** , tra cui il server o il percorso di destinazione, un nome di sito e le credenziali. È possibile controllare i comportamenti seguenti nella scheda **Impostazioni**:

- La configurazione da distribuire.
- Se rimuovere i file esistenti dalla destinazione.
- Se precompilare durante la pubblicazione.
- Se escludere i file nella cartella App_Data dalla distribuzione.

È possibile creare qualsiasi numero di profili di distribuzione del server Web IIS in Visual Studio, rendendo possibile la gestione dei profili con impostazioni diverse.

### <a name="when-to-choose-web-server-iis-deployment"></a>Quando scegliere la distribuzione del server Web (IIS)

- Si sta usando IIS per pubblicare un sito o un servizio a cui è possibile accedere tramite URL.
- Si vuole eseguire la distribuzione usando credenziali diverse da quelle usate in Visual Studio o quelle associate direttamente all'account Azure.
- Si vuole eliminare i file dalla destinazione ogni volta che si esegue la distribuzione.

Per ulteriori informazioni, vedere [Guida introduttiva: eseguire la distribuzione in un sito Web](quickstart-deploy-to-a-web-site.md).

Per informazioni sulla risoluzione dei problemi relativi a ASP.NET Core in IIS, vedere [risolvere i problemi di ASP.NET Core in app Azure Service e IIS](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="import-profile"></a>Importa profilo

È possibile importare un profilo durante la pubblicazione in IIS o app Azure servizio. È possibile configurare la distribuzione usando un *file di impostazioni di pubblicazione* (con* \* estensione publishsettings*). Il file delle impostazioni di pubblicazione viene creato da IIS o dal servizio app di Azure oppure può essere creato manualmente e quindi importato in Visual Studio.

L'uso di un file di impostazioni di pubblicazione può semplificare la configurazione della distribuzione e funziona meglio in un ambiente team rispetto alla configurazione manuale di ogni profilo di distribuzione.

### <a name="when-to-choose-import-profile"></a>Quando scegliere Importa profilo

- Si sta eseguendo la pubblicazione in IIS e si vuole semplificare la configurazione della distribuzione.
- Si sta eseguendo la pubblicazione in IIS o app Azure servizio e si desidera velocizzare la configurazione della distribuzione per riutilizzare o per la pubblicazione dei membri del team nello stesso servizio.

Per altre informazioni, vedere gli argomenti seguenti:

- [Importare impostazioni di pubblicazione ed eseguire la distribuzione in IIS](tutorial-import-publish-settings-iis.md)
- [Importare impostazioni di pubblicazione e distribuzione in Azure](tutorial-import-publish-settings-azure.md)

## <a name="configure-net-deployment-settings"></a>Configurare le impostazioni di distribuzione .NET

Per ulteriori informazioni sulla scelta delle impostazioni, vedere gli argomenti seguenti:

- [Distribuzione autonoma e dipendente dal Framework](/dotnet/core/deploying/)
- [Identificatori di runtime di destinazione (RID portatile, et al)](/dotnet/core/rid-catalog)
- [Configurazioni di debug e di rilascio](../ide/understanding-build-configurations.md)

## <a name="next-steps"></a>Passaggi successivi

Esercitazioni:

- [Distribuire un'applicazione .NET Core con lo strumento di pubblicazione](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Pubblicare un'app ASP.NET Core in Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Distribuzione in Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Distribuire app per la piattaforma UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Pubblicare un'app Node.js in Azure con Distribuzione Web](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Pubblicare un'app Python in Servizio app di Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)