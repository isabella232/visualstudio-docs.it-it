---
title: Guida di Visual Studio per le aziende
description: Configurare e risolvere i Visual Studio in un ambiente aziendale.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: ''
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 16624eb602b5ef02d7871ba579e0e2bdc5bdb337
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/26/2021
ms.locfileid: "122981011"
---
# <a name="visual-studio-enterprise-guide"></a>Guida di Visual Studio per le aziende
Se si sta cercando di risparmiare tempo mentre l'azienda è in esecuzione Visual Studio, iniziare da qui. Questa guida aziendale include suggerimenti che consentono di installare e aggiornare Visual Studio in scenari aziendali comuni, di essere sbloccati se si verificano problemi e di apprendere come segnalare un problema se è necessaria assistenza. 

## <a name="get-started"></a>Introduzione 
Informazioni su come distribuire i Visual Studio aziendali in ambienti in rete e offline.

- **[Abilitazione degli aggiornamenti dell'amministratore tramite Microsoft Endpoint Configuration Manager (SCCM).](enabling-administrator-updates.md)**  Visual Studio aggiornamenti sono inclusi nel [catalogo Microsoft Update e](https://www.catalog.update.microsoft.com/Home.aspx) nel Windows Server Update Services [(WSUS).](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) Enterprise amministratori possono quindi scaricare l'aggiornamento e distribuirlo Visual Studio computer client all'interno dell'organizzazione usando strumenti di distribuzione standard, ad esempio Microsoft Endpoint Configuration Manager (SCCM).

- **Informazioni su opzioni per la distribuzione aziendale in ambienti di rete.** La [Visual Studio amministratore fornisce](visual-studio-administrator-guide.md) indicazioni basate su scenario per gli amministratori di sistema. 

- **[Ottenere suggerimenti per la risoluzione dei problemi](troubleshooting-installation-issues.md)**. Ottenere assistenza durante l'installazione o l'aggiornamento Visual Studio e su come segnalare un problema se si è bloccati. Questi suggerimenti includono istruzioni dettagliate che dovrebbero risolvere la maggior parte dei problemi di installazione online o offline. 

- **[Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)**. Se non si è connessi a Internet o la connettività Internet è limitata, trovare le opzioni per l'installazione Visual Studio. 

- **[Creare pacchetti del programma di avvio automatico](../deployment/creating-bootstrapper-packages.md)**. Informazioni su come creare pacchetti del programma di avvio automatico personalizzati creando manifesti di prodotti e pacchetti. 

- **[Applicare automaticamente i codici Product Key durante la Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)**. È possibile applicare il codice Product Key a livello di programmazione come parte dello script utilizzato per automatizzare la distribuzione di Visual Studio. È possibile impostare un codice Product Key in un dispositivo a livello di codice, durante un'installazione di Visual Studio o al termine di un'installazione. 

## <a name="install-visual-studio"></a>Installare Visual Studio 

Informazioni su come installare Visual Studio in scenari aziendali comuni. 

- **[Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)**. Usare un'ampia gamma di parametri per controllare o personalizzare l Visual Studio installazione. Automatizzare il processo di installazione o creare una cache dei file di installazione per un uso successivo. Per altre informazioni, vedere esempi [di parametri della riga di comando.](command-line-parameter-examples.md)

- **[Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md)**. Memorizzare nella cache i file per l'installazione iniziale insieme a tutti gli aggiornamenti del prodotto in una singola cartella. 

- **[Installare e usare i Visual Studio e i servizi di Azure dietro un firewall o un server proxy.](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)** Se l'organizzazione usa misure di sicurezza, ad esempio un firewall o un server proxy, è possibile aggiungere url di dominio a un "elenco elementi consentiti" e porte e protocolli da aprire per ottenere la migliore esperienza durante l'installazione e l'uso di Visual Studio e servizi di Azure. 

- **[Installare i certificati necessari per l'installazione offline.](../install/install-certificates-for-visual-studio-offline.md)** Installare i certificati necessari se il computer client è completamente disconnesso da Internet.

## <a name="update-visual-studio"></a>Aggiornare Visual Studio 

Informazioni su come aggiornare i Visual Studio e risolvere i problemi di aggiornamento. 

- **[Applicare gli aggiornamenti dell'amministratore Microsoft Endpoint Configuration Manager (SCCM).](../install/applying-administrator-updates.md)** Informazioni sulla distribuzione Visual Studio funzionalità, sicurezza e aggiornamenti qualitativi tramite SCCM. 

- **[Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)**. Aggiornare un layout di installazione di rete di Visual Studio con gli aggiornamenti più recenti del prodotto in modo che possa essere usato sia come punto di installazione per l'aggiornamento più recente di Visual Studio sia per mantenere le installazioni già distribuite nelle workstation client.

- **[Aggiornare Visual Studio in una baseline di manutenzione](update-servicing-baseline.md)**. Comprendere il valore dell'aggiornamento in una baseline e la differenza tra le versioni secondarie e gli aggiornamenti di manutenzione. 

- **[Aggiornare Visual Studio usando un layout offline minimo.](update-minimal-layout.md)** Per i computer non connessi a Internet, la creazione di un layout minimo è il modo più semplice e rapido per aggiornare le istanze di Visual Studio offline.

- **[Ripristinare Visual Studio](repair-visual-studio.md) per risolvere i problemi di aggiornamento**. In alcuni casi l'installazione di Visual Studio può risultare danneggiata Un ripristino è utile per risolvere i problemi relativi alla fase di installazione in tutte le operazioni di installazione, inclusi gli aggiornamenti. 

- **Seguire [Windows baseline di sicurezza.](/windows/security/threat-protection/windows-security-baselines)** Microsoft è dedicata a offrire ai clienti sistemi operativi sicuri, ad esempio Windows 10 e Windows Server, e app sicure, ad esempio Microsoft Edge. Oltre alla garanzia di sicurezza dei prodotti, Microsoft consente anche di avere un controllo completo degli ambienti fornendo varie funzionalità di configurazione. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche 

- [Guida alla produttività per Visual Studio](../ide/productivity-features.md)

