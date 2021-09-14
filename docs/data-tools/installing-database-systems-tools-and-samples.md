---
title: Compatibilità del database
description: Esaminare i sistemi di database compatibili per Visual Studio, ad esempio Microsoft SQL Server, Oracle, MySQL, PostgreSQL, SQLite e Firebird.
ms.custom: SEO-VS-2020
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6ccbf0866022e6e602938d2a5f86f8374eb73c89
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631284"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Sistemi di database compatibili per Visual Studio

Per sviluppare un'applicazione connessa ai dati in Visual Studio, in genere si installa il sistema di database nel computer di sviluppo locale e quindi si distribuiscono l'applicazione e il database in un ambiente di produzione quando sono pronti. Visual Studio installa SQL Server Express Local DB nel computer come parte del carico di lavoro Elaborazione ed **archiviazione** dati. Questa Local DB è utile per lo sviluppo di applicazioni connesse ai dati in modo semplice e rapido.

Perché un sistema di database sia accessibile dalle applicazioni .NET e sia visibile nelle finestre degli strumenti dati di Visual Studio, deve disporre di un provider ADO.NET dati. Un provider deve supportare Entity Framework se si prevede di usare i modelli di dati di entità nell'applicazione .NET. Molti provider vengono offerti tramite il NuGet Gestione pacchetti o tramite il marketplace Visual Studio.

Se si usano le API di archiviazione di Azure, installare gli emulatori di archiviazione di Azure nel computer locale durante lo sviluppo per evitare addebiti fino a quando non si è pronti per la distribuzione nell'ambiente di produzione. Per altre informazioni, vedere [Usare l'emulatore di archiviazione di Azure per sviluppo e test](/azure/storage/common/storage-use-emulator).

L'elenco seguente include alcuni dei sistemi di database più diffusi che possono essere usati nei Visual Studio progetti. L'elenco non è completo. Per un elenco di fornitori di terze parti che offrono ADO.NET provider di dati che consentono una stretta integrazione con gli strumenti di Visual Studio, vedere ADO.NET [Provider di dati](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server è l'offerta di database microsoft. SQL Server 2016 offre prestazioni all'avanguardia, sicurezza avanzata e funzionalità avanzate di creazione di report e analisi integrate. Viene fornito in diverse edizioni progettate per usi diversi: dall'analisi aziendale altamente scalabile e ad alte prestazioni, all'uso in un singolo computer. SQL Server Express è un'edizione completa di SQL Server personalizzata per la ridistribuzione e l'incorporamento.  Local DB è un'edizione semplificata SQL Server Express che non richiede alcuna configurazione ed è in esecuzione nel processo dell'applicazione. È possibile scaricare uno o entrambi i prodotti dalla [pagina SQL Server Express download](https://www.microsoft.com/sql-server/sql-server-editions-express). Molti esempi di SQL in questa sezione usano SQL Server Local DB. SQL Server Management Studio (SSMS) è un'applicazione di gestione di database autonoma che dispone di più funzionalità rispetto a quelle fornite in Visual Studio SQL Server Esplora oggetti. È possibile ottenere SSMS dal collegamento precedente.

## <a name="oracle"></a>Oracle

È possibile scaricare un'edizione gratuita o a pagamento del database Oracle dalla pagina [oracle technology network.](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html) Per il supporto in fase di progettazione Entity Framework e TableAdapter, è necessario il Strumenti di sviluppo [Oracle per Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/). Altri prodotti Oracle ufficiali, tra cui Oracle Instant Client, sono disponibili tramite il NuGet Gestione pacchetti. È possibile scaricare gli schemi di esempio Oracle seguendo le istruzioni nella [documentazione online di Oracle.](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)

## <a name="mysql"></a>MySQL

MySQL è un diffuso sistema di database open source ampiamente usato nelle aziende e nei siti Web. I download per MySQL, MySQL per Visual Studio e i prodotti correlati sono disponibili in [MySQL in Windows](https://www.mysql.com/why-mysql/windows/). Terze parti offrono varie Visual Studio e applicazioni di gestione autonome per MySQL. È possibile esplorare le offerte nel NuGet Gestione pacchetti (**Strumenti**  >  **NuGet Gestione pacchetti**  >  **Gestire NuGet pacchetti per la soluzione**).

## <a name="postgresql"></a>PostgreSQL

PostgreSQL è un sistema di database relazionale a oggetti open source gratuito. Per installarlo in Windows, è possibile scaricarlo dalla pagina di [download di PostgreSQL.](https://www.postgresql.org/download/windows/) È anche possibile compilare PostgreSQL dal codice sorgente. Il sistema di base PostgreSQL include un'interfaccia del linguaggio C. Molte terze parti forniscono pacchetti NuGet per l'uso di PostgreSQL da applicazioni .NET. È possibile esplorare le offerte nel NuGet Gestione pacchetti (**Strumenti**  >  **NuGet Gestione pacchetti**  >  **Gestire NuGet pacchetti per la soluzione**). Probabilmente, il pacchetto più diffuso viene fornito da [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite è un motore SQL database incorporato che viene eseguito nel processo dell'applicazione. È possibile scaricarlo dalla pagina [di download di SQLite.](https://www.sqlite.org/download.html) Sono disponibili anche molti NuGet di terze parti per SQLite. È possibile esplorare le offerte nel NuGet Gestione pacchetti (**Strumenti**  >  **NuGet Gestione pacchetti**  >  **Gestire NuGet pacchetti per la soluzione**).

## <a name="firebird"></a>Firebird

Firebird è un sistema di database SQL open source. È possibile scaricarlo dalla pagina [di download di Firebird.](http://firebirdsql.org/en/downloads/) Un provider ADO.NET è disponibile tramite il NuGet Gestione pacchetti.

## <a name="see-also"></a>Vedi anche

- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Come determinare la versione e l'edizione di SQL Server e dei relativi componenti](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
