---
title: Esperienze connesse in Visual Studio
description: Un'esperienza connessa si connette a Internet da un computer client e fornisce un servizio al cliente.
ms.date: 05/20/2021
ms.topic: conceptual
helpviewer_keywords: ''
author: SayyedaM
ms.author: sayyedamussa
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.openlocfilehash: 246b2496248cc66c180c577fdd1f7a202609117d
ms.sourcegitcommit: 7393a37ce77c5b80312ce787baa060c91d41d959
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113114779"
---
# <a name="connected-experiences-in-visual-studio"></a>**Esperienze connesse in Visual Studio** #

Visual Studio è costituito da applicazioni software client ed esperienze connesse progettate per consentire di codificare in modo più efficace. [L'aggiornamento di un pacchetto NuGet,](/nuget/consume-packages/install-use-packages-visual-studio) la selezione di un suggerimento [IntelliCode](/visualstudio/intellicode/overview)e la collaborazione con un altro sviluppatore [tramite Live Share](/visualstudio/liveshare/quickstart/share) sono esempi di esperienze connesse. 

## <a name="choose-whether-these-connected-experiences-are-available-to-use"></a>Scegliere se queste esperienze connesse sono disponibili per l'uso ##

È possibile scegliere le esperienze connesse da usare. L'uso di determinate esperienze connesse richiede l'accordo con condizioni diverse e aggiuntive Visual Studio contratto di licenza. Queste esperienze possono essere di proprietà di Microsoft Servizi online e/o servizi di proprietà di terze parti. Ad esempio, quando si usano esperienze connesse a GitHub, verranno applicate l'Informativa sulla privacy di [GitHub](https://docs.github.com/github/site-policy/github-privacy-statement) e le Condizioni per l'utilizzo del servizio di [GitHub,](https://docs.github.com/github/site-policy/github-terms-of-service)le Condizioni per l'utilizzo del servizio aziendale di [GitHub](https://docs.github.com/github/site-policy/github-corporate-terms-of-service)e/o condizioni aggiuntive [per](https://docs.github.com/github/site-policy/github-additional-product-terms) il prodotto. Se si [segnala un problema,](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)si accettano le [Condizioni per l'utilizzo di Microsoft](https://www.microsoft.com/legal/terms-of-use) e l'Informativa sulla privacy di [Microsoft.](https://privacy.microsoft.com/en-us/privacystatement) Se si usa il servizio NuGet, si accettano le Condizioni per l'utilizzo di [NuGet](https://www.nuget.org/policies/Terms) e [l'Informativa sulla privacy di Microsoft.](https://privacy.microsoft.com/en-us/privacystatement) 

Quando si installa Visual Studio, [è possibile selezionare facoltativamente](/visualstudio/install/install-visual-studio)carichi di lavoro e componenti per installare . I carichi di lavoro e i componenti possono sfruttare terze parti e consentire esperienze connesse a seconda delle funzionalità. Ad esempio, [il download del carico di lavoro Sviluppo di Azure consente di pubblicare le app cloud in Azure.](https://visualstudio.microsoft.com/vs/features/azure/) In base alle selezioni di installazione, è anche possibile usare il menu Strumenti e opzioni per connettersi, configurare e usare le esperienze connesse. Ad esempio, è possibile connettersi a un server, aggiungere l'autenticazione dei servizi di Azure o modificare le impostazioni di IntelliCode o LiveShare.  

È anche possibile usare le impostazioni del [firewall dell'organizzazione](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server) per abilitare o disabilitare la connessione ai servizi. Si noti che la disabilitazione della connessione a un endpoint può influire negativamente sulle prestazioni delle funzionalità Visual Studio correlate. 

Infine, il Visual Studio Marketplace offre estensioni che possono consentire esperienze connesse di terze parti o di terze parti. Visual Studio Marketplace è soggetto alle condizioni per l Visual Studio Marketplace [per l'utilizzo](https://cdn.vsassets.io/v/M146_20190123.39/_content/Microsoft-Visual-Studio-Marketplace-Terms-of-Use.pdf) e all'Informativa [sulla privacy di Microsoft.](https://privacy.microsoft.com/en-us/privacystatement) Ogni estensione richiede il contratto per particolari condizioni per l'utilizzo e informativa sulla privacy associate a tale offerta.  


## <a name="required-service-data"></a>Dati del servizio necessari ##

I dati del servizio necessari possono includere informazioni correlate al funzionamento dell'esperienza connessa necessaria per garantire la sicurezza, l'aggiornamento e le prestazioni del servizio sottostante come previsto. Se si sceglie di usare un'esperienza connessa che analizza il contenuto, ad esempio IntelliCode, viene inviato ed elaborato anche il codice selezionato per il modello per fornire l'esperienza di connessione. I dati del servizio necessari possono includere anche le informazioni necessarie a un'esperienza connessa per eseguire l'attività, ad esempio l'aggiornamento di un pacchetto NuGet. È possibile gestire i dati del servizio necessari scegliendo se usare o meno un determinato servizio. Se non si usa un servizio, non vengono raccolti dati del servizio necessari. 

I dati del servizio necessari sono diversi dai dati di diagnostica perché i dati di diagnostica sono correlati al software in esecuzione nel dispositivo. La scelta di partecipare al Visual Studio Analisi utilizzo software [(VSCEIP)](/visualstudio/ide/visual-studio-experience-improvement-program)controlla le impostazioni di privacy per i dati di diagnostica, ma questa impostazione non influisce sull'invio dei dati del servizio necessari. 

## <a name="diagnostic-data-collection"></a>Raccolta dati di diagnostica ##

I dati di diagnostica vengono usati per mantenere Visual Studio e aggiornati, rilevare, diagnosticare e risolvere i problemi e anche apportare miglioramenti al prodotto. I dati di diagnostica vengono raccolti e inviati a Microsoft Visual Studio software client in esecuzione nel dispositivo dell'utente.

Quando si rifiuta esplicitamente, si rifiuta esplicitamente la raccolta dei dati di diagnostica facoltativi. È necessaria una raccolta di dati di diagnostica per assicurarsi che Visual Studio sia sicuro, aggiornato e funzioni come previsto. La scelta di rifiutare esplicitamente [VSCEIP](/visualstudio/ide/visual-studio-experience-improvement-program)non inciderà sulla raccolta dei dati di diagnostica richiesta. 
