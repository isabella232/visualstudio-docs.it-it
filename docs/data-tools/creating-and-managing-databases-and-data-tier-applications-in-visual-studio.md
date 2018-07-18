---
title: I progetti di database, i progetti server e progetti di applicazione livello dati in Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 03dca206f38d98c44e711e945f5d4015142f0af9
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758407"
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>Progetti di database e applicazioni livello dati in Visual Studio
È possibile usare i progetti di database per creare nuovi database, le nuove applicazioni livello dati (DAC), nonché di aggiornare i database esistenti e le applicazioni livello dati. Sia i progetti di database e di applicazione livello dati consentono di applicare tecniche di gestione progetto e di controllo di versione per le tue attività di sviluppo di database in modo molto simile a come si applicano queste tecniche per codice gestito o nativo. Si consentono al team di sviluppo per gestire le modifiche al database e i server di database per la creazione di un progetto DAC, progetto di database o un progetto server e il relativo inserimento nel controllo della versione. I membri del team possono quindi estrarre i file per rendere, compilare e testare le modifiche in un ambiente di sviluppo isolato o sandbox, prima di condividerli con il team. Per garantire la qualità del codice, il team può terminare e testare tutte le modifiche per una particolare versione del database in un ambiente di staging prima di distribuire le modifiche nell'ambiente di produzione.

Per un elenco delle funzionalità di database supportate dalle applicazioni livello dati, vedere [funzionalità supportate in applicazioni livello dati](http://go.microsoft.com/fwlink/?LinkId=164239) sul sito web Microsoft. Se si usano funzionalità nel database che non sono supportate dalle applicazioni livello dati, si dovrebbe usare invece un progetto di database per gestire le modifiche apportate al database.

## <a name="common-high-level-tasks"></a>Attività comuni di alto livello

|Attività di alto livello|Contenuto di supporto|
|----------------------|------------------------|
|**Iniziare a sviluppare un'applicazione livello dati:** un'applicazione livello dati è un nuovo concetto introdotto con [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] che contiene la definizione per un [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] database e il supporto di oggetti utilizzati da un client-server o a 3 livelli delle istanze applicazione. Un'applicazione livello dati include gli oggetti di database, ad esempio tabelle e viste, insieme alle entità di istanza, ad esempio gli account di accesso. È possibile usare Visual Studio per creare un progetto di applicazione livello dati, compilare un file di pacchetto di applicazione livello dati e inviare tale file di pacchetto DAC da un amministratore del database per la distribuzione in un'istanza del [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] motore di database.|-   [Creazione e gestione di applicazioni livello dati](http://go.microsoft.com/fwlink/?LinkId=160741) (sito web Microsoft)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Eseguire lo sviluppo di database iterativo:** se sei uno sviluppatore o un tester, estrarre le parti del progetto e quindi eseguire l'aggiornamento in un ambiente di sviluppo isolato. Con questo tipo di ambiente, è possibile testare le modifiche senza influire su altri membri del team. Dopo aver complete le modifiche, estrarre i file in controllo della versione, in cui altri membri del team possono ottenere le modifiche e compilare e distribuirle a un server di prova.|-   [Editor di testo (SQL Server Management Studio) e query](http://go.microsoft.com/fwlink/?LinkId=227327) (sito web Microsoft)<br />-   [Debugger Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) (sito web Microsoft)|
|**La creazione di prototipi, verifica risultati del test e modifica degli script di database e oggetti:** è possibile usare il [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] editor per eseguire una di queste attività comuni.|-   [Editor di testo (SQL Server Management Studio) e query](http://go.microsoft.com/fwlink/?LinkId=227327) (sito web Microsoft)|

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
