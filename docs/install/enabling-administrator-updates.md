---
title: Abilitazione degli aggiornamenti dell'amministratore Visual Studio con Microsoft Endpoint Configuration Manager
titleSuffix: ''
description: Altre informazioni su come distribuire gli aggiornamenti dell'amministratore Visual Studio.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: affb5a0c78c1ad1e230c571485385d9f55fc2bec
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307453"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Abilitazione degli aggiornamenti dell'amministratore Visual Studio con Microsoft Endpoint Configuration Manager

Il Microsoft Endpoint Configuration Manager (SCCM) può gestire gli aggiornamenti Visual Studio 2017 e Visual Studio 2019 tramite il flusso di lavoro di gestione degli aggiornamenti software.

> [!NOTE]
> Per semplicità della documentazione, il contenuto seguente farà riferimento ai prodotti Visual Studio 2017, Visual Studio 2019 e Visual Studio 2022 collettivamente come "Visual Studio".

Quando Microsoft pubblica un nuovo aggiornamento Visual Studio nella rete per la distribuzione di contenuti (CDN), Microsoft pubblicherà contemporaneamente un pacchetto di aggiornamento amministratore corrispondente nei Microsoft Update server. Questo consentirà quindi a un amministratore di distribuire l'aggiornamento Visual Studio tramite [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) o [Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) (WSUS). Gestione configurazione possibile configurare per sincronizzare gli aggiornamenti dell'amministratore di Visual Studio dal catalogo WSUS al server del sito e quindi scaricare l'aggiornamento e distribuirlo Visual Studio computer client all'interno dell'organizzazione. Per altre informazioni sulle correzioni presenti in ogni versione di Visual Studio, vedere le [note sulla versione](/visualstudio/releases/2019/release-notes).

Per distribuire Visual Studio aggiornamenti dell'amministratore tramite Gestione configurazione, è necessario eseguire questi due passaggi di preparazione iniziali:
1. Abilitare Gestione configurazione ricevere notifiche di aggiornamento Visual Studio amministratore. 
2. Abilitare (o disabilitare) i computer client per Visual Studio gli aggiornamenti dell'amministratore da Gestione configurazione.

Dopo aver eseguito questi passaggi, è possibile usare le funzionalità di gestione degli aggiornamenti software di Gestione configurazione per distribuire gli aggiornamenti Visual Studio amministratore. I diversi tipi e caratteristiche degli aggiornamenti Visual Studio amministratore sono descritti [in](../install/applying-administrator-updates.md)Applicazione degli aggiornamenti dell'amministratore , che fornisce indicazioni su come e quando devono essere distribuiti in tutta l'organizzazione. Per altre informazioni sulle Gestione configurazione e sulle opzioni, vedere [Distribuire gli aggiornamenti software in Microsoft Endpoint Configuration Manager](/mem/configmgr/sum/deploy-use/deploy-software-updates).

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Abilitare Gestione configurazione ricevere notifiche di aggiornamento Visual Studio amministratore

Per abilitare Gestione configurazione gestire gli aggiornamenti Visual Studio amministratore, è necessario:

* Una versione con licenza corrente di Windows Server che esegue Microsoft Endpoint Configuration Manager (Current Branch) e Windows Server Update Services (WSUS). Non è possibile usare WSUS stesso per distribuire questi aggiornamenti. deve essere usato in combinazione con Gestione configurazione.

* Il server WSUS di primo livello della gerarchia e il server del sito Gestione configurazione di livello superiore devono avere accesso agli URL e alle porte Visual Studio elencati di seguito: Installare e usare Visual Studio e i servizi di Azure dietro un firewall o un [server proxy.](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)  

* Il Microsoft Endpoint Configuration Manager deve essere configurato per ricevere notifiche quando Visual Studio sono disponibili pacchetti di aggiornamento dell'amministratore.  A tale scopo, seguire questa procedura e per altre informazioni, vedere [Introduzione agli aggiornamenti software in Microsoft Endpoint Configuration Manager](/mem/configmgr/sum/understand/software-updates-introduction).

  1. Nella console Gestione configurazione, selezionare Amministrazione **(in** basso a sinistra), quindi Configurazione sito **(in** basso a sinistra), **Quindi Siti** e selezionare il server del sito.

  2. Nella barra **multifunzione della** scheda Home  nella parte superiore, nel pulsante Del gruppo Impostazioni selezionare **Configura componenti del** sito e quindi Selezionare Punto di **aggiornamento software**.

  3. Nella finestra **di dialogo Proprietà componente punto di aggiornamento** software:

        * Nella scheda **Prodotti,** nella gerarchia Strumenti di sviluppo, Runtime e **Ridistribuibili,** scegliere le versioni Visual Studio da sincronizzare.

        * Nella scheda **Classificazioni** verificare che siano selezionate le opzioni "Aggiornamenti della sicurezza", "Feature Pack" e "Aggiornamenti".

  4. Sincronizzare quindi gli aggiornamenti software con il server WSUS scegliendo **Raccolta software** (in basso a sinistra) e quindi nella scheda **Home** della barra multifunzione in alto selezionare il pulsante **Sincronizza aggiornamenti** software. La sincronizzazione degli aggiornamenti software rende disponibili Visual Studio gli aggiornamenti dell'amministratore visibili nella console di Gestione configurazione distribuzione.

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>Abilitare (o disabilitare) la capacità dei computer client di Visual Studio gli aggiornamenti dell'amministratore da Gestione configurazione

Per consentire a un computer client di accettare gli aggiornamenti dell'amministratore di Visual Studio, è necessario assicurarsi che l'utilità rilevamento client di Visual Studio sia installata correttamente e che sia necessario impostare una chiave del Registro di sistema per consentire al client di ricevere gli aggiornamenti dell'amministratore.  

### <a name="visual-studio-client-detector-utility"></a>Visual Studio Utilità rilevamento client

[L Visual Studio Client Detector Utility](https://support.microsoft.com/help/5001148) deve essere installato nei computer client perché gli aggiornamenti dell'amministratore siano riconosciuti e ricevuti correttamente. Questa utilità è stata inclusa in tutti gli aggiornamenti dei prodotti Visual Studio 2017 e Visual Studio 2019 rilasciati il 12 maggio 2020 o dopo il 12 maggio 2020, è inclusa come requisito preliminare con tutti gli aggiornamenti dell'amministratore di Visual Studio ed è anche disponibile nel catalogo Microsoft Update per [l'installazione in](https://catalog.update.microsoft.com) modo indipendente.

### <a name="encoding-administrator-intent-on-the-client-machines"></a>Finalità dell'amministratore di codifica nei computer client

I computer client devono essere abilitati per ricevere gli aggiornamenti dell'amministratore. Questo passaggio è necessario per assicurarsi che gli aggiornamenti non vengano involontariamente o accidentalmente inviati a computer client ignari.

La **chiave AdministratorUpdatesEnabled**   è progettata per consentire all'amministratore di codificare la finalità dell'amministratore. Questa chiave può essere in uno dei percorsi Visual Studio standard, come descritto nella documentazione Impostare le impostazioni predefinite per le distribuzioni aziendali [di Visual Studio](/visualstudio/install/set-defaults-for-enterprise-deployments) aziendale. L'accesso amministratore nel computer client è necessario per creare e impostare il valore di questa chiave.

* Per configurare il computer client in modo che accetti gli aggiornamenti dell'amministratore, impostare la chiave **administratorUpdatesEnabled**   REG_DWORD su **1.**
* Se la  **chiave REG_DWORD AdministratorUpdatesEnabled** è mancante o è impostata su   **0,** gli aggiornamenti dell'amministratore non verranno applicati al computer client.

## <a name="feedback-and-support"></a>Feedback e supporto

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

È possibile usare i metodi seguenti per fornire commenti e suggerimenti sugli aggiornamenti dell Visual Studio amministratore o per segnalare i problemi che influiscono sugli aggiornamenti:

* Fare riferimento alle indicazioni [sulla risoluzione dei Visual Studio problemi di installazione e aggiornamento.](../install/troubleshooting-installation-issues.md)
* Porre domande alla community nel forum Visual Studio [Setup Q&A Forum](/answers/topics/vs-setup.html).
* Passare alla pagina [Visual Studio supporto](https://visualstudio.microsoft.com/vs/support/)tecnico e verificare se il problema è elencato nelle domande frequenti.  È anche possibile selezionare il pulsante [Collegamento al](https://visualstudio.microsoft.com/vs/support/#talktous) supporto tecnico per la Guida della chat.
* [Inviare commenti e suggerimenti sulle funzionalità](https://aka.ms/vs/wsus/feedback) o segnalare un problema al team Visual Studio riguardo a questa esperienza di abilitazione degli aggiornamenti dell'amministratore.
* Contattare il personale dell'organizzazione technical account manager per Microsoft.

## <a name="see-also"></a>Vedi anche

* [Applicazione degli aggiornamenti dell'amministratore](../install/applying-administrator-updates.md)
* [Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md)
* [Ciclo di vita del prodotto e manutenzione di Visual Studio](/visualstudio/productinfo/vs-servicing-vs)
* [Note sulla versione di Visual Studio 2019](/visualstudio/releases/2019/release-notes)
* [Note sulla versione di Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Installa Visual Studio](../install/install-visual-studio.md)
* [Microsoft Update domande frequenti sul catalogo](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager (SCCM)](/mem/configmgr)
* [Importare gli aggiornamenti da Microsoft Catalog in Gestione configurazione](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS)](/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
