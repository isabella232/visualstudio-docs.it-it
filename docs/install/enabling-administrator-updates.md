---
title: Abilitazione degli aggiornamenti dell'amministratore a Visual Studio con Microsoft endpoint Configuration Manager
titleSuffix: ''
description: Altre informazioni su come distribuire gli aggiornamenti dell'amministratore in Visual Studio.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9ca14e1f4e84777fd1781249dd54a6646fb2c72a
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547479"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Abilitazione degli aggiornamenti dell'amministratore a Visual Studio con Microsoft endpoint Configuration Manager

Microsoft endpoint Configuration Manager (SCCM) può gestire gli aggiornamenti dell'amministratore di Visual Studio 2017 e Visual Studio 2019 usando il flusso di lavoro di gestione degli aggiornamenti software.

> [!NOTE]
> Per semplificare la documentazione, il contenuto seguente fa riferimento ai prodotti Visual Studio 2017 e Visual Studio 2019 collettivamente come "Visual Studio".

Quando Microsoft pubblica un nuovo aggiornamento di Visual Studio nella rete per la distribuzione di contenuti (CDN), Microsoft pubblicherà contemporaneamente un pacchetto di aggiornamento dell'amministratore corrispondente ai server Microsoft Update. Questo consentirà quindi a un amministratore di distribuire l'aggiornamento di Visual Studio tramite il [catalogo Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) o [Windows Server Update Services](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) (WSUS). Configuration Manager possibile configurare per sincronizzare gli aggiornamenti dell'amministratore di Visual Studio dal catalogo WSUS al server del sito, quindi è possibile scaricare l'aggiornamento e distribuirlo ai computer client di Visual Studio all'interno dell'organizzazione. Per ulteriori informazioni sulle correzioni presenti in ogni versione di Visual Studio, vedere le note sulla [versione](https://docs.microsoft.com/visualstudio/releases/2019/release-notes). 

Per distribuire gli aggiornamenti degli amministratori di Visual Studio tramite Configuration Manager, è necessario eseguire i due passaggi di preparazione iniziali seguenti: 
1. Abilitare Configuration Manager per ricevere le notifiche di aggiornamento dell'amministratore di Visual Studio. 
2. Abilitare (o disabilitare) i computer client per ricevere gli aggiornamenti dell'amministratore di Visual Studio da Configuration Manager.

Dopo aver eseguito questi passaggi, è possibile usare le funzionalità di gestione degli aggiornamenti software di Configuration Manager per distribuire gli aggiornamenti dell'amministratore di Visual Studio. I diversi tipi e caratteristiche degli aggiornamenti dell'amministratore di Visual Studio sono descritti in [applicazione degli aggiornamenti dell'amministratore](../install/applying-administrator-updates.md), che fornisce indicazioni su come e quando devono essere distribuiti nell'intera organizzazione. Per ulteriori informazioni sulle funzionalità e le opzioni di Configuration Manager, vedere [distribuire aggiornamenti software in Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/deploy-use/deploy-software-updates). 

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Abilitare Configuration Manager per ricevere le notifiche di aggiornamento dell'amministratore di Visual Studio 

Per consentire Configuration Manager di gestire gli aggiornamenti degli amministratori di Visual Studio, è necessario: 

* Una versione con licenza corrente di Windows Server che esegue Microsoft endpoint Configuration Manager (Current Branch) e Windows Server Update Services (WSUS). Non è possibile usare WSUS per distribuire questi aggiornamenti; deve essere usato insieme a Configuration Manager. 

* Il server WSUS di primo livello della gerarchia e il server del sito di Configuration Manager di livello superiore devono avere accesso alle porte e agli URL di Visual Studio elencati di seguito: [installare e usare Visual Studio e i servizi di Azure protetti da un firewall o un server proxy](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md).  

* Il Configuration Manager Microsoft endpoint deve essere configurato per ricevere notifiche quando sono disponibili i pacchetti di aggiornamento dell'amministratore di Visual Studio.  A tale scopo, attenersi alla procedura seguente e per altre informazioni, vedere [Introduction to Software Updates in Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/understand/software-updates-introduction).

  1. Nella console di Configuration Manager selezionare **Amministrazione** (in basso a sinistra), quindi selezionare **configurazione del sito** (metà sinistra), quindi **siti** e selezionare il server del sito. 

  2. Nella scheda **Home** della barra multifunzione nella parte superiore, nel pulsante gruppo **Impostazioni** , selezionare **Configura componenti del sito**, quindi selezionare punto di **aggiornamento software**. 

  3. Nella finestra di dialogo **proprietà del componente del punto di aggiornamento software** : 

        * Nella scheda **prodotti** , sotto la gerarchia **strumenti di sviluppo, Runtime e ridistribuibili** , scegliere le versioni di Visual Studio che si desidera sincronizzare.   

        * Nella scheda **classificazioni** verificare che siano selezionati "aggiornamenti della sicurezza", "Feature Pack" e "aggiornamenti".   

  4. Successivamente, sincronizzare gli aggiornamenti software con il server WSUS scegliendo **raccolta software** (in basso a sinistra), quindi nella scheda **Home** della barra multifunzione nella parte superiore, selezionare il pulsante **Sincronizza aggiornamenti software** . La sincronizzazione degli aggiornamenti software renderà disponibili gli aggiornamenti degli amministratori di Visual Studio disponibili in e in grado di essere distribuiti dalla console di Configuration Manager.   

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>Abilitare o disabilitare la possibilità per i computer client di ricevere gli aggiornamenti dell'amministratore di Visual Studio da Configuration Manager

Per consentire a un computer client di accettare gli aggiornamenti dell'amministratore di Visual Studio, è necessario verificare che l'utilità rilevatore client di Visual Studio sia installata correttamente ed è necessario impostare una chiave del registro di sistema per consentire al client di ricevere gli aggiornamenti dell'amministratore.  

### <a name="visual-studio-client-detector-utility"></a>Utilità rilevatore client di Visual Studio 

L' [utilità rilevatore client di Visual Studio](https://support.microsoft.com/help/5001148) deve essere installata nei computer client affinché gli aggiornamenti dell'amministratore vengano correttamente riconosciuti e ricevuti. Questa utilità è stata inclusa con tutti gli aggiornamenti del prodotto Visual Studio 2017 e Visual Studio 2019 rilasciati il 12 maggio 2020, che è un prerequisito con tutti gli aggiornamenti degli amministratori di Visual Studio ed è disponibile anche nel [catalogo Microsoft Update](https://catalog.update.microsoft.com) per l'installazione indipendente. 

### <a name="encoding-administrator-intent-on-the-client-machines"></a>Codifica Intent Administrator nei computer client 

I computer client devono essere abilitati per la ricezione degli aggiornamenti dell'amministratore. Questo passaggio è necessario per assicurarsi che gli aggiornamenti non siano involontariamente o accidentalmente inviati a computer client non sospetti. 

La chiave **AdministratorUpdatesEnabled**   è progettata per l'amministratore per codificare lo scopo dell'amministratore. Questa chiave può trovarsi in uno dei percorsi standard di Visual Studio, come descritto nella documentazione relativa alle [distribuzioni predefinite per le distribuzioni aziendali di Visual Studio](https://docs.microsoft.com/visualstudio/install/set-defaults-for-enterprise-deployments) . Per creare e impostare il valore di questa chiave, è necessario l'accesso amministrativo al computer client. 

* Per configurare il computer client in modo che accetti gli aggiornamenti amministrativi ****, impostare la   chiave di REG_DWORD AdministratorUpdatesEnabled su **1**. 
* Se la  ****   chiave di REG_DWORD AdministratorUpdatesEnabled è **mancante o è impostata su 0**, l'applicazione degli aggiornamenti dell'amministratore al computer client non verrà bloccata. 

## <a name="feedback-and-support"></a>Feedback e supporto
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

È possibile utilizzare i metodi seguenti per fornire commenti e suggerimenti sugli aggiornamenti degli amministratori di Visual Studio o per segnalare problemi che influiscono sugli aggiornamenti:
* Vedere la guida alla [risoluzione dei problemi di installazione e aggiornamento di Visual Studio](../install/troubleshooting-installation-issues.md) .
* Porre domande alla community nel programma di [installazione di Visual Studio Q&un forum](https://docs.microsoft.com/answers/topics/vs-setup.html).
* Passare alla [pagina del supporto di Visual Studio](https://visualstudio.microsoft.com/vs/support/)e verificare se il problema è elencato nelle domande frequenti.  È anche possibile selezionare il pulsante [link supporto](https://visualstudio.microsoft.com/vs/support/#talktous) per la Guida di chat.
* [Fornire commenti sulle funzionalità o segnalare un problema](https://aka.ms/vs/wsus/feedback) al team di Visual Studio in merito a questa esperienza di abilitazione degli aggiornamenti dell'amministratore.
* Rivolgersi all'account manager tecnico dell'organizzazione per Microsoft.

## <a name="see-also"></a>Vedi anche
* [Applicazione degli aggiornamenti amministratore](../install/applying-administrator-updates.md)
* [Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md)
* [Ciclo di vita del prodotto e manutenzione di Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)
* [Note sulla versione di Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/release-notes)
* [Note sulla versione di Visual Studio 2017](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes)
* [Installa Visual Studio](../install/install-visual-studio.md)
* [Domande frequenti sul catalogo Microsoft Update](https://www.catalog.update.microsoft.com/faq.aspx)
* [Documentazione di Microsoft endpoint Configuration Manager (SCCM)](https://docs.microsoft.com/mem/configmgr)
* [Importare gli aggiornamenti da Microsoft Catalog in Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Documentazione di Windows Server Update Services (WSUS)](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
