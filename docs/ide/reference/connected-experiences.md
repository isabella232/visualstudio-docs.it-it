---
title: Esperienze connesse in Visual Studio
description: Un'esperienza connessa si connette a Internet da un computer client e fornisce un servizio al cliente.
ms.date: 05/20/2021
ms.topic: conceptual
helpviewer_keywords: ''
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.openlocfilehash: c1b2121b69db3efd053a55aaf25ad0e9750351c4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144093"
---
# <a name="connected-experiences-in-visual-studio"></a>**Esperienze connesse in Visual Studio** #

Visual Studio è costituito da applicazioni software client ed esperienze connesse progettate per consentire di codificare in modo più efficace. [L'aggiornamento NuGet](/nuget/consume-packages/install-use-packages-visual-studio) pacchetto, la selezione di un suggerimento [IntelliCode](/visualstudio/intellicode/overview) e la collaborazione con un altro sviluppatore [Live Share](/visualstudio/liveshare/quickstart/share) esempi di esperienze connesse. 

## <a name="choose-whether-these-connected-experiences-are-available-to-use"></a>Scegliere se queste esperienze connesse sono disponibili per l'uso ##

È possibile scegliere le esperienze connesse da usare. L'uso di determinate esperienze connesse richiede l'accordo per termini diversi e aggiuntivi per il contratto Visual Studio contratto di licenza. Queste esperienze possono essere servizi Servizi online e/o di proprietà di terze parti. Ad esempio, quando si usano GitHub esperienze connesse, verranno applicate l'informativa sulla privacy di [GitHub](https://docs.github.com/github/site-policy/github-privacy-statement) e le Condizioni per il servizio [GitHub](https://docs.github.com/github/site-policy/github-terms-of-service), [GitHub Condizioni](https://docs.github.com/github/site-policy/github-corporate-terms-of-service)per il servizio aziendale e/o Condizioni aggiuntive del prodotto. [](https://docs.github.com/github/site-policy/github-additional-product-terms) Se si [segnala un problema,](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)si accettano le [Condizioni per l'utilizzo e](https://www.microsoft.com/legal/terms-of-use) l'Informativa sulla privacy [Microsoft.](https://privacy.microsoft.com/en-us/privacystatement) Se si usa il servizio NuGet, si accettano le condizioni NuGet [per](https://www.nuget.org/policies/Terms) l'utilizzo e l'Informativa [sulla privacy Microsoft.](https://privacy.microsoft.com/en-us/privacystatement) 

Quando si installa Visual Studio, [è possibile selezionare facoltativamente](/visualstudio/install/install-visual-studio)carichi di lavoro e componenti per installare . I carichi di lavoro e i componenti possono sfruttare software di terze parti e possono abilitare esperienze connesse, a seconda delle funzionalità. Ad esempio, [il download del carico di lavoro sviluppo di Azure consente di pubblicare le app cloud in Azure.](https://visualstudio.microsoft.com/vs/features/azure/) In base alle selezioni di installazione, è anche possibile usare il menu Strumenti e opzioni per connettersi, configurare e usare esperienze connesse. Ad esempio, è possibile connettersi a un server, aggiungere l'autenticazione di Servizi di Azure o modificare le impostazioni di IntelliCode o LiveShare.  

È anche possibile usare le impostazioni del [firewall dell'organizzazione](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server) per abilitare o disabilitare la connessione ai servizi. Si noti che la disabilitazione della connessione a un endpoint può influire negativamente sulle prestazioni delle funzionalità Visual Studio correlate. 

Infine, il Visual Studio Marketplace offre estensioni che possono abilitare esperienze connesse di prima o di terze parti. Visual Studio Marketplace è soggetto alle condizioni per [Visual Studio per l'utilizzo del Marketplace](https://cdn.vsassets.io/v/M146_20190123.39/_content/Microsoft-Visual-Studio-Marketplace-Terms-of-Use.pdf) e all'Informativa sulla privacy [Microsoft.](https://privacy.microsoft.com/en-us/privacystatement) Ogni estensione richiede l'accordo per determinate condizioni per l'utilizzo e l'informativa sulla privacy associata a tale offerta.  


## <a name="required-service-data"></a>Dati del servizio necessari ##

I dati del servizio necessari possono includere informazioni correlate al funzionamento dell'esperienza connessa necessaria per mantenere il servizio sottostante sicuro, aggiornato e le prestazioni previste. Se si sceglie di usare un'esperienza connessa che analizza il contenuto, ad esempio IntelliCode, anche il codice selezionato per il modello viene inviato ed elaborato per fornire l'esperienza di connessione. I dati del servizio necessari possono includere anche le informazioni necessarie a un'esperienza connessa per eseguire la propria attività, ad esempio l'aggiornamento di NuGet pacchetto. È possibile gestire i dati del servizio necessari scegliendo se usare o meno un servizio specifico. Se non si usa un servizio, non vengono raccolti dati del servizio necessari. 

I dati del servizio necessari sono diversi dai dati di diagnostica perché i dati di diagnostica sono correlati al software in esecuzione nel dispositivo. La scelta di partecipare al Visual Studio Analisi utilizzo software [(VSCEIP)](/visualstudio/ide/visual-studio-experience-improvement-program)controlla le impostazioni di privacy per i dati di diagnostica, ma questa impostazione non influisce sull'invio dei dati del servizio necessari. 

## <a name="diagnostic-data-collection"></a>Raccolta dati di diagnostica ##

I dati di diagnostica vengono usati per mantenere Visual Studio e aggiornati, rilevare, diagnosticare e risolvere i problemi e apportare miglioramenti al prodotto. I dati di diagnostica vengono raccolti e inviati a Microsoft Visual Studio software client in esecuzione nel dispositivo dell'utente.

Quando si rifiuta esplicitamente, si rifiuta esplicitamente la raccolta dei dati di diagnostica facoltativa. È necessaria una raccolta di dati di diagnostica per assicurarsi che Visual Studio sia sicuro, aggiornato e funzioni come previsto. La scelta di rifiutare esplicitamente [VSCEIP](/visualstudio/ide/visual-studio-experience-improvement-program)non inciderà sulla raccolta dei dati di diagnostica necessari. 
