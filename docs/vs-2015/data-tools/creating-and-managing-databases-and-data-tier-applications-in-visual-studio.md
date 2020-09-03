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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b793789e092b46f14db397c1f8aef4e98544f856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851688"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Creazione e gestione di database e applicazioni livello dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IMPORTANT]
> I progetti di database inclusi nelle versioni precedenti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sono ora disponibili in [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] strumenti. Per ulteriori informazioni, vedere [SQL Server Developer Tools](https://msdn.microsoft.com/library/hh272686(VS.103).aspx).

 È possibile utilizzare i progetti di database per creare nuovi database, nuove applicazioni del livello dati (DAC) e per aggiornare i database esistenti e le applicazioni del livello dati. I progetti di database e di applicazione livello dati consentono di applicare tecniche di controllo della versione e di gestione dei progetti allo sviluppo del database in modo analogo all'applicazione di tali tecniche a codice gestito o nativo. È possibile consentire al team di sviluppo di gestire le modifiche apportate ai database e ai server di database creando un progetto di *applicazione livello dati*, un *progetto di database*o un *progetto server* e inserendolo nel controllo della versione. I membri del team possono quindi estrarre i file per creare, compilare e testare le modifiche in un *ambiente di sviluppo isolato*, o sandbox, prima di condividerli con il team. Per garantire la qualità del codice, il team può completare e testare tutte le modifiche per una particolare versione del database in un ambiente di gestione temporanea prima di distribuire le modifiche in produzione.

 Per un elenco delle funzionalità di database supportate dalle applicazioni livello dati, vedere [funzionalità supportate nelle applicazioni livello dati](https://msdn.microsoft.com/library/ee362013(VS.100).aspx) nel sito Web Microsoft. Se si utilizzano le funzionalità del database non supportate dalle applicazioni livello dati, è necessario utilizzare un progetto di database per gestire le modifiche apportate al database.

## <a name="common-high-level-tasks"></a>Attività di alto livello comuni

|Attività di alto livello|Contenuto di supporto|
|----------------------|------------------------|
|**Avviare lo sviluppo di un'applicazione livello dati:** Un'applicazione livello dati è un nuovo concetto introdotto con [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] che contiene la definizione per un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database e gli oggetti istanza di supporto utilizzati da un'applicazione client-server o a tre livelli. Un'applicazione livello dati include oggetti di database, ad esempio tabelle e viste, insieme a entità di istanza quali gli account di accesso. È possibile utilizzare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per creare un progetto di applicazione livello dati SQL Server, compilare un file di pacchetto di applicazione livello dati e inviare il file del pacchetto di applicazione livello dati a un amministratore del database per la distribuzione in un'istanza del [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] motore di database|-   [Creazione e gestione di applicazioni livello dati](https://msdn.microsoft.com/library/ee361996(VS.100).aspx) (sito Web Microsoft)<br />-   [SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(SQL.110).aspx)|
|**Esecuzione dello sviluppo iterativo di database:** Se si è uno sviluppatore o un tester, estrarre le parti del progetto e aggiornarle in un ambiente di sviluppo isolato. Utilizzando questo tipo di ambiente, è possibile testare le modifiche senza influire sugli altri membri del team. Una volta completate le modifiche, è possibile archiviare nuovamente i file nel controllo della versione, in modo che gli altri membri del team possano ottenere le modifiche e compilarle e distribuirle in un server di prova.|-   [Editor di query e di testo (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (sito Web Microsoft)<br />-   [Debugger Transact-SQL](https://msdn.microsoft.com/library/cc645997(SQL.110).aspx) (sito Web Microsoft)|
|**Prototipi, verifica dei risultati dei test e modifica degli script e degli oggetti di database:** È possibile utilizzare l' [!INCLUDE[tsql](../includes/tsql-md.md)] Editor per eseguire una di queste attività comuni.|-   [Editor di query e di testo (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (sito Web Microsoft)|

## <a name="see-also"></a>Vedere anche
 [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
