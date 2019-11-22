---
title: Installazione di sistemi di database, strumenti ed esempi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 091338e411369e40f19e028cd19b6cb2e697718c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299604"
---
# <a name="installing-database-systems-tools-and-samples"></a>Installazione di sistemi di database, strumenti ed esempi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio non include alcun sistema di database diverso da quelli usati internamente. Per sviluppare un'applicazione connessa ai dati in Visual Studio, in genere si installa il sistema di database nel computer di sviluppo locale e quindi si distribuisce l'applicazione e il database in un ambiente di produzione quando sono pronti. Affinché il sistema di database sia accessibile dalle applicazioni .NET e sia visibile nelle finestre di Visual Studio Data Tools, deve disporre di un provider di dati ADO.NET. Un provider deve supportare specificamente Entity Framework se si prevede di utilizzare Entity Data Model nell'applicazione .NET.     Molti provider sono offerti tramite Gestione pacchetti NuGet o tramite Visual Studio Gallery.

 Per lo sviluppo di SQL, assicurarsi di avere SQL Server Data Tools installato in Visual Studio. Scegliere il menu **Visualizza** . Se non viene visualizzato Esplora oggetti di SQL Server, passare al pannello di controllo e modificare Visual Studio. Nel programma di installazione selezionare **Microsoft SQL Server Data Tools**.

 Se si usano le API di archiviazione di Azure, installare gli emulatori di archiviazione di Azure nel computer locale durante lo sviluppo per evitare addebiti fino a quando non si è pronti per la distribuzione nell'ambiente di produzione. Per altre informazioni, vedere [usare l'emulatore di archiviazione di Azure per sviluppo e test](https://azure.microsoft.com/documentation/articles/storage-use-emulator/).

 Nell'elenco seguente sono inclusi alcuni dei sistemi di database più diffusi che è possibile utilizzare nei progetti di Visual Studio. L'elenco non è esaustivo. Per un elenco di fornitori di terze parti che offrono provider di dati ADO.NET che consentono una profonda integrazione con gli strumenti di Visual Studio, vedere [provider di dati ADO.NET](https://msdn.microsoft.com/library/dd363565.aspx).

### <a name="microsoft-sql-server"></a>Microsoft SQL Server
 SQL Server è l'offerta di database Microsoft Flagship. SQL Server 2016 offre prestazioni eccezionali, sicurezza avanzata e funzionalità avanzate di creazione di report e analisi integrate. Viene fornito in varie edizioni progettate per usi diversi: da analisi business a scalabilità elevata e a elevate prestazioni, da usare in un singolo computer. SQL Server Express è un'edizione completa di SQL Server personalizzata per la ridistribuzione e l'incorporamento.  Il database locale è un'edizione semplificata di SQL Server Express che non richiede alcuna configurazione ed è in esecuzione nel processo dell'applicazione. È possibile scaricare uno o entrambi i prodotti dalla [pagina di download SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Molti degli esempi SQL di questa sezione usano SQL Server database locale. SQL Server Management Studio (SSMS) è un'applicazione di gestione di database autonoma che offre più funzionalità rispetto a quelle disponibili in Visual Studio Esplora oggetti di SQL Server. È possibile ottenere SSMS dal collegamento precedente.

### <a name="oracle"></a>Oracle
 È possibile scaricare un'edizione a pagamento o gratuita del database Oracle dalla pagina [rete della tecnologia Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) . Per il supporto in fase di progettazione per Entity Framework e TableAdapter, sarà necessario [Oracle strumenti di sviluppo per Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/). Altri prodotti Oracle ufficiali, incluso Oracle Instant client, sono disponibili tramite Gestione pacchetti NuGet.  È possibile scaricare gli schemi di esempio Oracle seguendo le istruzioni riportate nella [documentazione online di Oracle](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

### <a name="mysql"></a>MySQL
 MySQL è un diffuso sistema di database open source ampiamente usato in aziende e siti Web. I download per MySQL, MySQL per Visual Studio e i prodotti correlati si trovano in [MySQL in Windows](https://www.mysql.com/why-mysql/windows/).  Le terze parti offrono varie estensioni di Visual Studio e applicazioni di gestione autonoma per MySQL. È possibile esplorare le offerte in Gestione pacchetti NuGet (**strumenti** > **gestione pacchetti NuGet** > **gestire i pacchetti NuGet per la soluzione**).

### <a name="postgresql"></a>PostgreSQL
 PostgreSQL è un sistema di database relazionale a oggetti open source gratuito. Per installarlo in Windows, è possibile scaricarlo dalla [pagina di download di PostgreSQL](http://www.postgresql.org/download/windows/).  È anche possibile compilare PostgreSQL dal codice sorgente.  Il sistema di base PostgreSQL include un'interfaccia del linguaggio C. Molte terze parti forniscono pacchetti NuGet per l'uso di PostgreSQL dalle applicazioni .NET.  È possibile esplorare le offerte in Gestione pacchetti NuGet (**strumenti** > **gestione pacchetti NuGet** > **gestire i pacchetti NuGet per la soluzione**). Probabilmente il pacchetto più diffuso è fornito da [npgsql.org](http://www.npgsql.org/).

### <a name="sqlite"></a>SQLite
 SQLite è un motore di database SQL incorporato che viene eseguito nel processo dell'applicazione. È possibile scaricarlo dalla [pagina di download di SQLite](http://www.sqlite.org/download.html). Sono disponibili anche molti pacchetti NuGet di terze parti per SQLite. È possibile esplorare le offerte in Gestione pacchetti NuGet (**strumenti** > **gestione pacchetti NuGet** > **gestire i pacchetti NuGet per la soluzione**).

### <a name="firebird"></a>Firebird
 Firebird è un sistema open source per database SQL. È possibile scaricarlo dalla [pagina di download di Firebird](http://firebirdsql.org/en/downloads/). Un provider di dati ADO.NET è disponibile tramite Gestione pacchetti NuGet.

## <a name="see-also"></a>Vedere anche
 [Come determinare la versione e l'edizione di SQL Server e dei relativi componenti](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
