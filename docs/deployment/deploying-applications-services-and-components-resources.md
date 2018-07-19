---
title: Panoramica della distribuzione - Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7346de998052ba68dfadf74a09fe0d4339be1614
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757162"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Panoramica della distribuzione in Visual Studio

Mediante la distribuzione, un'applicazione, un servizio o un componente viene distribuito per l'installazione in altri computer, dispositivi, server o nel cloud. Il metodo appropriato viene scelto in Visual Studio per il tipo di distribuzione necessaria.

Per molti tipi comuni di app, è possibile distribuire l'applicazione direttamente da Esplora soluzioni in Visual Studio. Per una rapida panoramica di questa funzionalità, vedere [primi passi in fase di distribuzione](../deployment/deploying-applications-services-and-components.md).

![Scegliere un'opzione di pubblicazione](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Quali sono le opzioni di pubblicazione più adatte?

All'interno di Visual Studio, le applicazioni possono essere pubblicate direttamente nelle destinazioni seguenti:

- [Servizio app di Azure](#azure-app-service)
- [Macchine virtuali di Azure](#azure-virtual-machines)
- [File system](#file-system)
- [Destinazioni personalizzate (IIS, FTP e così via) ](#custom-targets), inclusi tutti i server Web arbitrari.

Nella scheda **Pubblica** è possibile selezionare un profilo di pubblicazione esistente, importare un profilo esistente o crearne uno nuovo usando le opzioni descritte di seguito. Per una panoramica delle opzioni di pubblicazione nell'IDE per diversi tipi di app, vedere [Presentazione della distribuzione](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Servizio app di Azure

[Servizio app di Azure](/azure/app-service/app-service-web-overview) consente agli sviluppatori di creare rapidamente un'ampia gamma di servizi e applicazioni Web scalabili senza gestire l'infrastruttura.

Determinare quanta potenza di calcolo di un servizio APp, scelta di un [piano tariffario](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) del servizio App che lo contiene. È possibile avere più Web App (e altri tipi di app) condividano lo stesso servizio App senza modificare il piano tariffario. Ad esempio, è possibile ospitare le app Web di sviluppo, staging e produzione insieme nello stesso servizio App.

Un servizio app viene eseguito nelle macchine virtuali ospitate nel cloud di Azure, ma tali macchine vengono gestite automaticamente. Ogni app in un servizio App verrà assegnato un valore univoco \*. URL azurewebsites.net; tutti i piani tariffari diversi da quello gratuito consentono l'assegnazione di nomi di dominio personalizzati al sito.

### <a name="when-to-choose-azure-app-service"></a>Quando scegliere Servizio App di Azure

- Si vuole distribuire un'applicazione Web accessibile via Internet.
- Si vuole adeguare automaticamente l'applicazione Web in base alla richiesta senza doverla ridistribuire.
- Non si vuole gestire l'infrastruttura di server, inclusi gli aggiornamenti software.
- Non sono necessarie personalizzazioni a livello di computer sui server che ospitano l'applicazione Web.

> Per usare Servizio app di Azure nel proprio centro dati o in altri computer locali, usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Per altre informazioni sulla pubblicazione in servizio App, vedere [Guida introduttiva: pubblicare in Azure App Service](quickstart-deploy-to-azure.md).

## <a name="azure-virtual-machines"></a>Macchine virtuali di Azure

Le [macchine virtuali (VM) di Azure](https://azure.microsoft.com/documentation/services/virtual-machines/) consentono di creare e gestire qualsiasi numero di risorse di elaborazione nel cloud. Assumendo la responsabilità di tutti i software e gli aggiornamenti nelle macchine virtuali, è possibile personalizzarli nel modo desiderato come richiesto dall'applicazione. È possibile accedere alle macchine virtuali direttamente con Desktop remoto e ognuna di esse manterrà l'indirizzo IP assegnato finché lo si ritiene opportuno.

Scalabilità di un'applicazione ospitata in macchine virtuali implica la rotazione dei backup di macchine virtuali aggiuntive in base alla richiesta e quindi distribuire il software necessario. Questo livello di controllo aggiuntivo consente di ridimensionare le macchine in modo diverso nelle diverse aree geografiche globali. Se ad esempio l'applicazione viene usata da dipendenti dislocati in varie sedi regionali, è possibile ridimensionare le macchine virtuali in base al numero di dipendenti di quelle sedi, potenzialmente riducendo i costi.

Per altre informazioni, vedere il [confronto dettagliato](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) tra Servizio app di Azure, Macchine virtuali di Azure e altri servizi di Azure che è possibile usare come destinazione della distribuzione usando l'opzione Personalizzata in Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Quando scegliere Macchine virtuali di Azure

- Si vuole distribuire un'applicazione Web accessibile via Internet, con controllo completo della durata degli indirizzi IP assegnati.
- Sono necessarie personalizzazioni a livello di computer sui server, che includono software aggiuntivo come ad esempio un sistema di database specializzato, configurazioni di rete specifiche, partizioni del disco e così via.
- Si vuole garantire un elevato livello di controllo sul ridimensionamento dell'applicazione Web.
- È necessario l'accesso diretto ai server che ospitano l'applicazione per qualsiasi altro motivo.

> Per usare le macchine virtuali di Azure nel proprio centro dati o in altri computer locali, usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="file-system"></a>File system

La distribuzione nel file System significa semplicemente copiare i file dell'applicazione in una cartella specifica nel proprio computer. Ciò in genere viene utilizzato a scopo di test o per distribuire l'applicazione per l'uso da un numero limitato di persone, se il computer esegue anche un server. Se la cartella di destinazione è condivisa in rete, la distribuzione nel file system può rendere disponibili i file dell'applicazione Web per altri utenti che possono distribuirli a loro volta a server specifici.

Qualsiasi computer locale che esegue un server può rendere disponibile tramite Internet o Intranet a seconda del modo in cui viene configurato e le reti a cui è connessa l'applicazione. Se si connette un computer direttamente a Internet, prestare particolare attenzione a proteggerlo dalle minacce esterne per la sicurezza. Poiché l'utente gestisce questi computer, ha il controllo completo delle configurazioni hardware e software.

Si noti che se per qualsiasi motivo (ad esempio, l'accesso al computer) non si è in grado di usare servizi cloud come Servizio app di Azure o Macchine virtuali di Azure, è possibile usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) nel proprio centro dati. Azure Stack consente di gestire e usare le risorse di elaborazione con Servizio app di Azure e Macchine virtuali di Azure, mantenendo tutti gli elementi in locale.

### <a name="when-to-choose-file-system-deployment"></a>Quando scegliere la distribuzione nel file system

- È necessario distribuire l'applicazione solo in una condivisione di file da cui altri utenti effettueranno a loro volta la distribuzione a server diversi.
- È necessaria solo una distribuzione locale dei test.
- Si vuole esaminare e potenzialmente modificare in modo indipendente i file dell'applicazione prima di inviarli a un'altra destinazione di distribuzione.

Per altre informazioni, vedere [Guida introduttiva - distribuire in una cartella locale](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>Destinazioni personalizzate (IIS, FTP)

Una destinazione personalizzata consente di distribuire l'applicazione in una destinazione diversa da servizio App di Azure, macchine virtuali di Azure o nel file system locale. È possibile distribuire l'applicazione a un file system o qualsiasi altro server (Internet o Intranet) a cui si ha accesso, inclusi quelli presenti in altri servizi cloud. È anche possibile usare una distribuzione Web (file o .ZIP) e FTP.

Quando si sceglie una destinazione personalizzata Visual Studio richiede un nome di profilo e quindi raccoglie ulteriori informazioni sulla **connessione** tra cui il server o il percorso di destinazione, un nome di sito e le credenziali. È possibile controllare i comportamenti seguenti nella scheda **Impostazioni**:

- La configurazione da distribuire.
- Se rimuovere i file esistenti dalla destinazione.
- Se precompilare durante la pubblicazione.
- Se escludere i file nella cartella App_Data dalla distribuzione.

Visual Studio consente di creare qualsiasi numero di profili di distribuzione personalizzata e di gestire i profili con impostazioni diverse.

### <a name="when-to-choose-custom-deployment"></a>Quando scegliere una distribuzione personalizzata

- Se si usano servizi cloud di un provider diverso da Azure a cui è possibile accedere con URL.
- Si vuole eseguire la distribuzione usando credenziali diverse da quelle usate in Visual Studio o quelle associate direttamente all'account Azure.
- Si vuole eliminare i file dalla destinazione ogni volta che si esegue la distribuzione.

Per altre informazioni, vedere [Guida introduttiva - distribuire in un sito web](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>Passaggi successivi

Esercitazioni:

- [Distribuire un'applicazione .NET Core con lo strumento di pubblicazione](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Pubblicare un'app ASP.NET core in Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Distribuzione in Visual C++](/cpp/ide/deployment-in-visual-cpp)
- [Distribuire le app UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Pubblicare un'app Node. js in Azure con distribuzione Web](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Pubblicare un'app Python in servizio App di Azure](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
