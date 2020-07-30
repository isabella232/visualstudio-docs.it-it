---
title: Guida a Visual Studio Enterprise
description: Configurare e risolvere i problemi di Visual Studio in un ambiente aziendale.
ms.date: 07/29/2020
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3d223d6e1e6ed3bf4b75b1c66bcc0f9dc897cfed
ms.sourcegitcommit: b8ce85a6d9c7fcceaad0fba625202f5ecf8f368c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2020
ms.locfileid: "87440677"
---
# <a name="visual-studio-enterprise-guide"></a>Guida a Visual Studio Enterprise
Se si vuole risparmiare tempo durante l'esecuzione della propria azienda in Visual Studio, iniziare da qui. Questa guida aziendale include suggerimenti che consentono di installare e aggiornare Visual Studio in scenari aziendali comuni, di essere sbloccati in caso di problemi e di informazioni su come segnalare un problema se è necessaria una maggiore assistenza. 

## <a name="get-started"></a>Introduzione 
Informazioni su come distribuire Visual Studio nell'azienda in ambienti in rete e offline. 

- **Informazioni sulle opzioni per la distribuzione aziendale in ambienti di rete**. La [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md) fornisce linee guida basate sullo scenario per gli amministratori di sistema. 

- **[Ottenere suggerimenti per la risoluzione dei problemi](troubleshooting-installation-issues.md)**. Ottieni assistenza durante l'installazione o l'aggiornamento di Visual Studio e Scopri come segnalare un problema se sei bloccato. Questi suggerimenti includono istruzioni dettagliate per risolvere la maggior parte dei problemi di installazione online o offline. 

- **[Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)**. Se non si è connessi a Internet o si ha una connettività Internet limitata, trovare le opzioni per l'installazione di Visual Studio. 

- **[Creare pacchetti del programma di avvio automatico](../deployment/creating-bootstrapper-packages.md)**. Informazioni su come creare pacchetti del programma di avvio automatico personalizzati creando manifesti di prodotto e di pacchetto. 

- **[Applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)**. È possibile applicare il codice Product Key a livello di programmazione come parte dello script utilizzato per automatizzare la distribuzione di Visual Studio. È possibile impostare un codice Product Key su un dispositivo a livello di codice, durante un'installazione di Visual Studio o al termine di un'installazione. 

## <a name="install-visual-studio"></a>Installare Visual Studio 

Informazioni su come installare Visual Studio in scenari aziendali comuni. 

- **[Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)**. Usare diversi parametri per controllare o personalizzare l'installazione di Visual Studio. Automatizzare il processo di installazione o creare una cache dei file di installazione per un uso successivo. 

- **Vedere [esempi di parametri della riga di comando per l'installazione di Visual Studio](command-line-parameter-examples.md)**. Per illustrare come usare i parametri della riga di comando per installare Visual Studio, visualizzare diversi esempi che è possibile personalizzare in base alle esigenze. 

- **[Installare e usare Visual Studio e i servizi di Azure protetti da un firewall o un server proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)**. Se l'organizzazione utilizza misure di sicurezza, ad esempio un firewall o un server proxy, è possibile aggiungere URL di dominio a un "elenco Consenti" e porte e protocolli che possono essere aperti in modo da ottenere la migliore esperienza durante l'installazione e l'utilizzo di Visual Studio e dei servizi di Azure. 

- **[Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md)**. Memorizzare nella cache i file per l'installazione iniziale insieme a tutti gli aggiornamenti del prodotto in una singola cartella.  

## <a name="update-visual-studio"></a>Aggiornare Visual Studio 

Informazioni su come aggiornare correttamente Visual Studio e correggere i problemi di aggiornamento. 

- **[Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)**. Aggiornare un layout di installazione di rete di Visual Studio con gli ultimi aggiornamenti del prodotto in modo che possa essere usato sia come punto di installazione per l'aggiornamento più recente di Visual Studio sia per gestire installazioni già distribuite nelle workstation client.

- **[Aggiornare Visual Studio in base a una linea di base di manutenzione](update-servicing-baseline.md)**. Conoscere il valore nell'aggiornamento di una linea di base e apprendere la differenza tra le versioni secondarie e gli aggiornamenti del servizio. 

- **[Aggiornare Visual Studio usando un layout minimo offline](update-minimal-layout.md)**. Per i computer che non sono connessi a Internet, la creazione di un layout minimo è il modo più semplice e rapido per aggiornare le istanze di Visual Studio offline.

- ** [Ripristinare Visual Studio](repair-visual-studio.md) per correggere i problemi di aggiornamento**. In alcuni casi l'installazione di Visual Studio può risultare danneggiata Una correzione è utile per la correzione di problemi in fase di installazione per tutte le operazioni di installazione, inclusi gli aggiornamenti. 

- **Seguire le [linee di base di sicurezza di Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines)**. Microsoft è dedicata a fornire ai propri clienti sistemi operativi sicuri, ad esempio Windows 10 e Windows Server, e app sicure, ad esempio Microsoft Edge. Oltre alla garanzia di sicurezza dei propri prodotti, Microsoft consente anche di avere un controllo accurato sugli ambienti fornendo diverse funzionalità di configurazione. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche 

- [Guida alla produttività per Visual Studio](../ide/productivity-features.md)



