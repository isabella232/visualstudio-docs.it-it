---
title: Creazione e gestione di database e applicazioni livello dati
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d6cb4a3beb12d2b33b8b13441df66116fe449d09
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431150"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Creazione e gestione di database e applicazioni livello dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IMPORTANT]
> I progetti di database che sono state incluse nelle versioni precedenti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sono ora disponibili [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] strumenti. Per altre informazioni, vedere [SQL Server Developer Tools](http://go.microsoft.com/fwlink/?LinkId=228126).

 È possibile usare i progetti di database per creare nuovi database, le nuove applicazioni livello dati (DAC), nonché di aggiornare i database esistenti e le applicazioni livello dati. Sia i progetti di database e di applicazione livello dati consentono di applicare tecniche di gestione progetto e di controllo di versione per le tue attività di sviluppo di database in modo molto simile a come si applicano queste tecniche per codice gestito o nativo. Per aiutare il team di sviluppo gestire le modifiche apportate ai database e i server di database tramite la creazione di un *progetto DAC*, *progetto di database*, o un *progetto server* e il relativo inserimento nel controllo della versione. I membri del team possono quindi estrarre i file da creare, compilare e testare le modifiche in un' *ambiente di sviluppo isolato*, o sandbox, prima di condividerli con il team. Per garantire la qualità del codice, il team può terminare e testare tutte le modifiche per una particolare versione del database in un ambiente di staging prima di distribuire le modifiche nell'ambiente di produzione.

 Per un elenco delle funzionalità di database supportate dalle applicazioni livello dati, vedere [funzionalità supportate in applicazioni livello dati](http://go.microsoft.com/fwlink/?LinkId=164239) sul sito web Microsoft. Se si usano funzionalità nel database che non sono supportate dalle applicazioni livello dati, si dovrebbe usare invece un progetto di database per gestire le modifiche apportate al database.

## <a name="common-high-level-tasks"></a>Attività comuni di alto livello

|Attività di alto livello|Contenuto di supporto|
|----------------------|------------------------|
|**Iniziare a sviluppare un'applicazione livello dati:** Un'applicazione livello dati è un nuovo concetto introdotto con [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] che contiene la definizione per un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database e il supporto di oggetti utilizzati da un'applicazione a 3 livelli o il client e server dell'istanza. Un'applicazione livello dati include gli oggetti di database, ad esempio tabelle e viste, insieme alle entità di istanza, ad esempio gli account di accesso. È possibile usare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per creare un progetto di applicazione livello dati, creare un file di pacchetto di applicazione livello dati e inviare tale file di pacchetto di applicazione livello dati a un amministratore del database per la distribuzione in un'istanza del [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] motore di database.|-   [Creazione e gestione di applicazioni livello dati](http://go.microsoft.com/fwlink/?LinkId=160741) (sito web Microsoft)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Eseguire lo sviluppo iterativo di database:** Se sei uno sviluppatore o un tester, estrarre le parti del progetto e quindi eseguire l'aggiornamento in un ambiente di sviluppo isolato. Con questo tipo di ambiente, è possibile testare le modifiche senza influire su altri membri del team. Dopo aver complete le modifiche, estrarre i file in controllo della versione, in cui altri membri del team possono ottenere le modifiche e compilare e distribuirle a un server di prova.|-   [Editor di testo (SQL Server Management Studio) e query](http://go.microsoft.com/fwlink/?LinkId=227327) (sito web Microsoft)<br />-   [Debugger Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) (sito web Microsoft)|
|**Creazione di prototipi, verifica risultati del test e modificare gli script di database e oggetti:** È possibile usare il [!INCLUDE[tsql](../includes/tsql-md.md)] editor per eseguire una di queste attività comuni.|-   [Editor di testo (SQL Server Management Studio) e query](http://go.microsoft.com/fwlink/?LinkId=227327) (sito web Microsoft)|

## <a name="see-also"></a>Vedere anche
 [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
