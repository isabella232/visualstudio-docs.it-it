---
title: Abilitazione degli aggiornamenti dell'amministratore Visual Studio con Microsoft Endpoint Configuration Manager
titleSuffix: ''
description: Altre informazioni su come distribuire gli aggiornamenti dell'amministratore in Visual Studio.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: f3cfe29c9c8c912e7a88f08b04235de1d390f8e6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627072"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Abilitazione degli aggiornamenti dell'amministratore Visual Studio con Microsoft Endpoint Configuration Manager

Il Microsoft Endpoint Configuration Manager (SCCM) può gestire gli aggiornamenti Visual Studio 2017 e Visual Studio 2019 tramite il flusso di lavoro di gestione degli aggiornamenti software.

> [!NOTE]
> Per semplicità nella documentazione, il contenuto seguente farà riferimento ai prodotti Visual Studio 2017, Visual Studio 2019 e Visual Studio 2022 collettivamente come "Visual Studio".

Quando Microsoft pubblica un nuovo aggiornamento Visual Studio nel rete per la distribuzione di contenuti (rete CDN), Microsoft pubblicherà contemporaneamente un pacchetto di aggiornamento amministratore corrispondente nei server Microsoft Update. In questo modo un amministratore può distribuire l'aggiornamento Visual Studio tramite [il catalogo di Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) o [Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) (WSUS). Gestione configurazione può essere configurato per sincronizzare gli aggiornamenti dell'amministratore di Visual Studio dal catalogo WSUS nel server del sito e quindi può scaricare l'aggiornamento e distribuirlo nei computer client Visual Studio tutta l'organizzazione. Per altre informazioni sulle correzioni presenti in ogni versione di Visual Studio, vedere le note [sulla versione](/visualstudio/releases/2019/release-notes).

Per distribuire Visual Studio di amministratore tramite Gestione configurazione, è necessario eseguire questi due passaggi di preparazione iniziali:
1. Abilitare Gestione configurazione ricevere notifiche di aggiornamento Visual Studio amministratore. 
2. Abilitare (o disabilitare) i computer client per la ricezione Visual Studio gli aggiornamenti dell'amministratore Gestione configurazione.

Dopo aver eseguito questi passaggi, è possibile usare le funzionalità di gestione degli aggiornamenti software di Gestione configurazione distribuire gli aggiornamenti Visual Studio amministratore. I diversi tipi e caratteristiche degli aggiornamenti Visual Studio amministratore sono descritti [in](../install/applying-administrator-updates.md)Applicazione degli aggiornamenti dell'amministratore, che fornisce indicazioni su come e quando devono essere distribuiti in tutta l'organizzazione. Per altre informazioni sulle Gestione configurazione e sulle opzioni, vedere [Distribuire gli aggiornamenti software in Microsoft Endpoint Configuration Manager](/mem/configmgr/sum/deploy-use/deploy-software-updates).

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Abilitare Gestione configurazione ricevere notifiche di Visual Studio di aggiornamento dell'amministratore

Per consentire Gestione configurazione gestire gli aggiornamenti Visual Studio amministratore, è necessario:

* Una versione con licenza corrente di Windows Server che esegue Microsoft Endpoint Configuration Manager (Current Branch) e Windows Server Update Services (WSUS). Non è possibile usare WSUS per distribuire questi aggiornamenti. deve essere usato in combinazione con Gestione configurazione.

* Il server WSUS di livello superiore della gerarchia e il server del sito Gestione configurazione di livello superiore devono avere accesso agli URL e alle porte di Visual Studio elencati di seguito: Installare e usare Visual Studio e i servizi di Azure dietro un firewall o un [server proxy.](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)  

* Il Microsoft Endpoint Configuration Manager deve essere configurato per ricevere notifiche quando sono Visual Studio pacchetti di aggiornamento dell'amministratore.  A tale scopo, seguire questa procedura e per altre informazioni, vedere [Introduzione agli aggiornamenti software in Microsoft Endpoint Configuration Manager](/mem/configmgr/sum/understand/software-updates-introduction).

  1. Nella console Gestione configurazione, selezionare **Amministrazione** (in basso a sinistra), quindi Configurazione del sito **(al** centro a sinistra), siti **e** infine il server del sito.

  2. Nella scheda **Home** della barra multifunzione nella parte superiore, nel **pulsante Impostazioni** gruppo, selezionare Configura componenti del sito **e** quindi selezionare Punto di **aggiornamento software.**

  3. Nella finestra **di dialogo Proprietà componente punto di aggiornamento** software :

        * Nella scheda **Prodotti,** nella gerarchia **Strumenti di sviluppo, Runtime** e Ridistribuibili, scegliere le versioni di Visual Studio da sincronizzare.

        * Nella scheda **Classificazioni** verificare che siano selezionate le opzioni "Aggiornamenti della sicurezza", "Feature Pack" e "Aggiornamenti".

  4. Sincronizzare quindi gli aggiornamenti software con il server WSUS scegliendo **Raccolta software** (in basso a sinistra) e quindi nella scheda **Home** della barra multifunzione in alto selezionare il pulsante **Sincronizza aggiornamenti** software. La sincronizzazione degli aggiornamenti software rende disponibili Visual Studio gli aggiornamenti dell'amministratore nella console di Gestione configurazione distribuzione.

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>Abilitare (o disabilitare) la capacità dei computer client di Visual Studio gli aggiornamenti dell'amministratore da Gestione configurazione

Per consentire a un computer client di accettare gli aggiornamenti dell'amministratore di Visual Studio, è necessario assicurarsi che l'utilità rilevamento client di Visual Studio sia installata correttamente e che sia necessario impostare una chiave del Registro di sistema per consentire al client di ricevere gli aggiornamenti dell'amministratore.  

### <a name="visual-studio-client-detector-utility"></a>Visual Studio Utilità Rilevamento client

[L Visual Studio Client Detector Utility](https://support.microsoft.com/help/5001148) deve essere installata nei computer client perché gli aggiornamenti dell'amministratore siano riconosciuti e ricevuti correttamente. Questa utilità è stata inclusa in tutti gli aggiornamenti dei prodotti Visual Studio 2017 e Visual Studio 2019 rilasciati il 12 maggio 2020 o dopo il 12 maggio 2020, è inclusa come prerequisiti per tutti gli aggiornamenti dell'amministratore di Visual Studio ed è disponibile anche nel catalogo [di Microsoft Update](https://catalog.update.microsoft.com) per l'installazione indipendente.

### <a name="encoding-administrator-intent-on-the-client-machines"></a>Finalità dell'amministratore della codifica nei computer client

I computer client devono essere abilitati per ricevere gli aggiornamenti dell'amministratore. Questo passaggio è necessario per assicurarsi che gli aggiornamenti non vengano involontariamente o accidentalmente inviati a computer client non insospettatori.

La **chiave AdministratorUpdatesEnabled**   è progettata per consentire all'amministratore di codificare la finalità dell'amministratore. Questa chiave può essere in una qualsiasi delle Visual Studio standard, come descritto nella documentazione Impostare i valori predefiniti per le distribuzioni aziendali [Visual Studio](/visualstudio/install/set-defaults-for-enterprise-deployments) distribuzione. L'accesso amministrativo nel computer client è necessario per creare e impostare il valore di questa chiave.

* Per configurare il computer client in modo che accetti gli aggiornamenti dell'amministratore, impostare la chiave REG_DWORD **AdministratorUpdatesEnabled**   su **1.**
* Se la chiave REG_DWORD  **AdministratorUpdatesEnabled** è mancante o è impostata su   **0,** l'applicazione degli aggiornamenti dell'amministratore al computer client verrà bloccata.

## <a name="feedback-and-support"></a>Feedback e supporto

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

È possibile usare i metodi seguenti per fornire commenti e suggerimenti sugli aggiornamenti Visual Studio amministratore o segnalare problemi che influiscono sugli aggiornamenti:

* Fare riferimento alle indicazioni [sulla risoluzione Visual Studio problemi di installazione e aggiornamento.](../install/troubleshooting-installation-issues.md)
* Porre domande alla community [all'indirizzo Visual Studio Setup Q&A Forum](/answers/topics/vs-setup.html).
* Passare alla pagina [Visual Studio supporto](https://visualstudio.microsoft.com/vs/support/)tecnico e verificare se il problema è elencato nelle domande frequenti.  È anche possibile selezionare il pulsante [Collegamento al supporto](https://visualstudio.microsoft.com/vs/support/#talktous) per la Guida alla chat.
* [Inviare commenti e suggerimenti sulle funzionalità o segnalare un problema](https://aka.ms/vs/wsus/feedback) al team Visual Studio riguardo a questa esperienza di abilitazione degli aggiornamenti dell'amministratore.
* Contattare l'amministratore dell'technical account manager per Microsoft.

## <a name="see-also"></a>Vedi anche

* [Applicazione degli aggiornamenti dell'amministratore](../install/applying-administrator-updates.md)
* [Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md)
* [Ciclo di vita del prodotto e manutenzione di Visual Studio](/visualstudio/productinfo/vs-servicing-vs)
* [Note sulla versione di Visual Studio 2019](/visualstudio/releases/2019/release-notes)
* [Note sulla versione di Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Installa Visual Studio](../install/install-visual-studio.md)
* [Microsoft Update domande frequenti sul catalogo](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager (SCCM)](/mem/configmgr)
* [Importare gli aggiornamenti da Microsoft Catalog Gestione configurazione](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS)](/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
