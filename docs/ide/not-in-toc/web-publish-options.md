---
title: "Quali sono le opzioni di pubblicazione più adatte? | Microsoft Docs"
ms.custom: 
ms.date: 03/09/2017
ms.reviewer: riande
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ASP.NET, web applications, deployment, publishing
ms.assetid: 3A13F685-531C-457D-A98E-631888011E4B
caps.latest.revision: "1"
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 10cb0ca2d5190ce73f0fd67da5b1f795d5aa8dd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# Quali sono le opzioni di pubblicazione più adatte?

Dall'interno di Visual Studio le applicazioni Web possono essere pubblicate direttamente nelle destinazioni seguenti:

- [Servizio app di Azure](#azure-app-service)
- [Macchine virtuali di Azure](#azure-virtual-machines)
- [File system](#file-system)
- [Destinazioni personalizzate (IIS, FTP e così via) ](#custom-targets), inclusi tutti i server Web arbitrari.

Nella scheda **Pubblica** è possibile selezionare un profilo di pubblicazione esistente, importare un profilo esistente o crearne uno nuovo usando le opzioni descritte di seguito.

## Servizio app di Azure

[Servizio app di Azure](https://azure.microsoft.com/documentation/articles/app-service-value-prop-what-is/) consente agli sviluppatori di creare rapidamente un'ampia gamma di servizi e applicazioni Web scalabili senza gestire l'infrastruttura.

Per le applicazioni Web in particolare, un servizio app è un contenitore per un'[*app Web*](https://azure.microsoft.com/en-us/documentation/articles/app-service-web-overview/) che si può paragonare a un host Web tradizionale. Vale a dire, un'app Web offre le risorse di elaborazione necessarie per eseguire il codice lato server e renderlo disponibile su Internet.

Per determinare la potenza di calcolo di un'app Web, scegliere un [piano tariffario](https://azure.microsoft.com/documentation/articles/azure-web-sites-web-hosting-plans-in-depth-overview/) per il servizio app che la contiene. È possibile fare in modo che più app Web (e altri tipi di app) condividano lo stesso servizio app senza modificare il piano tariffario. Ad esempio, è possibile ospitare app Web di sviluppo, gestione temporanea e produzione insieme nello stesso servizio app.

Un servizio app viene eseguito nelle macchine virtuali ospitate nel cloud di Azure, ma tali macchine vengono gestite automaticamente. A ogni app Web di un servizio app verrà assegnato un URL \*.azurewebsites.net univoco. Tutti i piani tariffari diversi da quello gratuito consentono l'assegnazione di nomi di dominio personalizzati al sito.

### Quando scegliere Servizio App di Azure

- Si vuole distribuire un'applicazione Web accessibile via Internet.
- Si vuole adeguare automaticamente l'applicazione Web in base alla richiesta senza doverla ridistribuire.
- Non si vuole gestire l'infrastruttura di server, inclusi gli aggiornamenti software.
- Non sono necessarie personalizzazioni a livello di computer sui server che ospitano l'applicazione Web.


> Per usare Servizio app di Azure nel proprio centro dati o in altri computer locali, usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).


## Macchine virtuali di Azure

Le [macchine virtuali (VM) di Azure](https://azure.microsoft.com/documentation/services/virtual-machines/) consentono di creare e gestire qualsiasi numero di risorse di elaborazione nel cloud. Con l'assunzione della responsabilità per tutto il software e tutti gli aggiornamenti nelle macchine virtuali, è possibile personalizzare le macchine in base alle esigenze dell'applicazione Web. È possibile accedere alle macchine virtuali direttamente con Desktop remoto e ognuna di esse manterrà l'indirizzo IP assegnato finché lo si ritiene opportuno.

Il ridimensionamento di un'applicazione Web ospitata in macchine virtuali comporta l'attivazione di altre macchine virtuali in base alla richiesta e quindi la distribuzione del software necessario. Questo livello di controllo aggiuntivo consente di ridimensionare le macchine in modo diverso nelle diverse aree geografiche globali. Se ad esempio l'applicazione viene usata da dipendenti dislocati in varie sedi regionali, è possibile ridimensionare le macchine virtuali in base al numero di dipendenti di quelle sedi, potenzialmente riducendo i costi.

Per altre informazioni, vedere il [confronto dettagliato](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) tra Servizio app di Azure, Macchine virtuali di Azure e altri servizi di Azure che è possibile usare come destinazione della distribuzione usando l'opzione Personalizzata in Visual Studio.

### Quando scegliere Macchine virtuali di Azure

- Si vuole distribuire un'applicazione Web accessibile via Internet, con controllo completo della durata degli indirizzi IP assegnati.
- Sono necessarie personalizzazioni a livello di computer sui server, che includono software aggiuntivo come ad esempio un sistema di database specializzato, configurazioni di rete specifiche, partizioni del disco e così via.
- Si vuole garantire un elevato livello di controllo sul ridimensionamento dell'applicazione Web.
- È necessario l'accesso diretto ai server che ospitano l'applicazione per qualsiasi altro motivo.

> Per usare le macchine virtuali di Azure nel proprio centro dati o in altri computer locali, usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).


## File system

Effettuare la distribuzione nel file system significa semplicemente copiare i file dell'applicazione Web in una cartella specifica del proprio computer. Questo sistema viene spesso usato a scopo di test o per distribuire l'applicazione per l'uso destinato a un numero limitato di persone, se il computer esegue anche un server Web. Se la cartella di destinazione è condivisa in rete, la distribuzione nel file system può rendere disponibili i file dell'applicazione Web per altri utenti che possono distribuirli a loro volta a server specifici.

Qualsiasi computer locale che esegue un server Web è in grado di rendere l'applicazione disponibile su Internet o Intranet, in base al tipo di configurazione e alle reti a cui è connesso. Se si connette un computer direttamente a Internet, prestare particolare attenzione a proteggerlo dalle minacce esterne per la sicurezza. Poiché l'utente gestisce questi computer, ha il controllo completo delle configurazioni hardware e software.

Si noti che se per qualsiasi motivo (ad esempio, l'accesso al computer) non si è in grado di usare servizi cloud come Servizio app di Azure o Macchine virtuali di Azure, è possibile usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) nel proprio centro dati. Azure Stack consente di gestire e usare le risorse di elaborazione con Servizio app di Azure e Macchine virtuali di Azure, mantenendo tutti gli elementi in locale.

### Quando scegliere la distribuzione nel file system

- È necessario distribuire l'applicazione solo in una condivisione di file da cui altri utenti effettueranno a loro volta la distribuzione a server diversi.
- È necessaria solo una distribuzione locale dei test.
- Si vuole esaminare e potenzialmente modificare in modo indipendente i file dell'applicazione prima di inviarli a un'altra destinazione di distribuzione.



## Destinazioni personalizzate

Una destinazione personalizzata consente di distribuire l'applicazione Web a una destinazione diversa da Servizio app di Azure, Macchine virtuali di Azure o il file system locale. È possibile distribuire l'applicazione a un file system o qualsiasi altro server (Internet o Intranet) a cui si ha accesso, inclusi quelli presenti in altri servizi cloud. È anche possibile usare una distribuzione Web (file o .ZIP) e FTP.

Quando si sceglie una destinazione personalizzata Visual Studio richiede un nome di profilo e quindi raccoglie ulteriori informazioni sulla **connessione** tra cui il server o il percorso di destinazione, un nome di sito e le credenziali. È possibile controllare i comportamenti seguenti nella scheda **Impostazioni**:

- La configurazione da distribuire.
- Se rimuovere i file esistenti dalla destinazione.
- Se precompilare durante la pubblicazione.
- Se escludere i file nella cartella App_Data dalla distribuzione.

Visual Studio consente di creare qualsiasi numero di profili di distribuzione personalizzata e di gestire i profili con impostazioni diverse.

### Quando scegliere una distribuzione personalizzata

- Se si usano servizi cloud di un provider diverso da Azure a cui è possibile accedere con URL.
- Si vuole eseguire la distribuzione usando credenziali diverse da quelle usate in Visual Studio o quelle associate direttamente all'account Azure.
- Si vuole eliminare i file dalla destinazione ogni volta che si esegue la distribuzione.
