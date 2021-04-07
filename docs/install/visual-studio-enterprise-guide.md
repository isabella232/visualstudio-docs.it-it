---
title: Guida di Visual Studio per le aziende
description: Configurare e risolvere i problemi di Visual Studio in un ambiente aziendale.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e5e8a28ac89c2bea85aee8323060bf948266ad2e
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547388"
---
# <a name="visual-studio-enterprise-guide"></a>Guida di Visual Studio per le aziende
Se si vuole risparmiare tempo durante l'esecuzione della propria azienda in Visual Studio, iniziare da qui. Questa guida aziendale include suggerimenti che consentono di installare e aggiornare Visual Studio in scenari aziendali comuni, di essere sbloccati in caso di problemi e di informazioni su come segnalare un problema se è necessaria una maggiore assistenza. 

## <a name="get-started"></a>Introduzione 
Informazioni su come distribuire Visual Studio nell'azienda in ambienti in rete e offline.

- **[Abilitazione degli aggiornamenti dell'amministratore tramite Microsoft Endpoint Configuration Manager (SCCM)](enabling-administrator-updates.md)**.  Gli aggiornamenti di Visual Studio sono inclusi nel [catalogo Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) e nella [Windows Server Update Services (WSUS)](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus). Gli amministratori dell'organizzazione possono quindi scaricare l'aggiornamento e distribuirlo ai computer client di Visual Studio all'interno dell'organizzazione utilizzando strumenti di distribuzione standard, ad esempio Microsoft endpoint Configuration Manager (SCCM).

- **Informazioni sulle opzioni per la distribuzione aziendale in ambienti di rete**. La [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md) fornisce linee guida basate sullo scenario per gli amministratori di sistema. 

- **[Ottenere suggerimenti per la risoluzione dei problemi](troubleshooting-installation-issues.md)**. Ottieni assistenza durante l'installazione o l'aggiornamento di Visual Studio e Scopri come segnalare un problema se sei bloccato. Questi suggerimenti includono istruzioni dettagliate per risolvere la maggior parte dei problemi di installazione online o offline. 

- **[Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)**. Se non si è connessi a Internet o si ha una connettività Internet limitata, trovare le opzioni per l'installazione di Visual Studio. 

- **[Creare pacchetti del programma di avvio automatico](../deployment/creating-bootstrapper-packages.md)**. Informazioni su come creare pacchetti del programma di avvio automatico personalizzati creando manifesti di prodotto e di pacchetto. 

- **[Applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)**. È possibile applicare il codice Product Key a livello di programmazione come parte dello script utilizzato per automatizzare la distribuzione di Visual Studio. È possibile impostare un codice Product Key su un dispositivo a livello di codice, durante un'installazione di Visual Studio o al termine di un'installazione. 

## <a name="install-visual-studio"></a>Installare Visual Studio 

Informazioni su come installare Visual Studio in scenari aziendali comuni. 

- **[Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)**. Usare diversi parametri per controllare o personalizzare l'installazione di Visual Studio. Automatizzare il processo di installazione o creare una cache dei file di installazione per un uso successivo. Per ulteriori informazioni, vedere [esempi di parametri della riga di comando](command-line-parameter-examples.md).

- **[Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md)**. Memorizzare nella cache i file per l'installazione iniziale insieme a tutti gli aggiornamenti del prodotto in una singola cartella. 

- **[Installare e usare Visual Studio e i servizi di Azure protetti da un firewall o un server proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)**. Se l'organizzazione utilizza misure di sicurezza, ad esempio un firewall o un server proxy, è possibile aggiungere URL di dominio a "Allow" e porte e protocolli da aprire in modo da ottenere un'esperienza ottimale durante l'installazione e l'utilizzo di Visual Studio e dei servizi di Azure. 

- **[Installare i certificati necessari per l'installazione offline](../install/install-certificates-for-visual-studio-offline.md)**. Installare i certificati necessari se il computer client è completamente disconnesso da Internet.

## <a name="update-visual-studio"></a>Aggiornare Visual Studio 

Informazioni su come aggiornare correttamente Visual Studio e correggere i problemi di aggiornamento. 

- **[Applicare gli aggiornamenti dell'amministratore utilizzando Microsoft Endpoint Configuration Manager (SCCM)](../install/applying-administrator-updates.md)**. Informazioni sulla distribuzione degli aggiornamenti della funzionalità, della sicurezza e della qualità di Visual Studio tramite SCCM. 

- **[Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)**. Aggiornare un layout di installazione di rete di Visual Studio con gli ultimi aggiornamenti del prodotto in modo che possa essere usato sia come punto di installazione per l'aggiornamento più recente di Visual Studio sia per gestire installazioni già distribuite nelle workstation client.

- **[Aggiornare Visual Studio in base a una linea di base di manutenzione](update-servicing-baseline.md)**. Conoscere il valore nell'aggiornamento di una linea di base e apprendere la differenza tra le versioni secondarie e gli aggiornamenti del servizio. 

- **[Aggiornare Visual Studio usando un layout minimo offline](update-minimal-layout.md)**. Per i computer che non sono connessi a Internet, la creazione di un layout minimo è il modo più semplice e rapido per aggiornare le istanze di Visual Studio offline.

- **[Ripristinare Visual Studio](repair-visual-studio.md) per correggere i problemi di aggiornamento**. In alcuni casi l'installazione di Visual Studio può risultare danneggiata Una correzione è utile per la correzione di problemi in fase di installazione per tutte le operazioni di installazione, inclusi gli aggiornamenti. 

- **Seguire le [linee di base di sicurezza di Windows](/windows/security/threat-protection/windows-security-baselines)**. Microsoft è dedicata a fornire ai propri clienti sistemi operativi sicuri, ad esempio Windows 10 e Windows Server, e app sicure, ad esempio Microsoft Edge. Oltre alla garanzia di sicurezza dei propri prodotti, Microsoft consente anche di avere un controllo accurato sugli ambienti fornendo diverse funzionalità di configurazione. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche 

- [Guida alla produttività per Visual Studio](../ide/productivity-features.md)

