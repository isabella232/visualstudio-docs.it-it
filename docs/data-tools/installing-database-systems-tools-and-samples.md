---
title: Compatibilità del database
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9115e675c43e04496712784371ac2301ef7c2f8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566690"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Sistemi di database compatibili per Visual Studio

Per sviluppare un'applicazione dati connessi in Visual Studio, in genere installa il sistema di database nel computer di sviluppo locale e quindi distribuire l'applicazione e database in un ambiente di produzione quando sono pronte. Visual Studio viene installato SQL Server Express LocalDB nel computer con il **elaborazione ed archiviazione dati** carico di lavoro. Questa istanza di Local DB è utile per lo sviluppo di applicazioni basate su dati rapidamente e facilmente.

Per un sistema di database deve essere accessibile da applicazioni .NET e per essere visibile nelle finestre di Visual Studio data tools, deve avere un provider di dati ADO.NET. Un provider deve supportare in modo specifico Entity Framework se si prevede di usare modelli di dati di entità nell'applicazione .NET. Molti provider vengono offerti tramite Gestione pacchetti NuGet o tramite Visual Studio Marketplace.

Se si usa API di archiviazione di Azure, installare gli emulatori di archiviazione di Azure nel computer locale durante lo sviluppo per evitare addebiti non necessari finché non si è pronti per la distribuzione nell'ambiente di produzione. Per altre informazioni, vedere [usare l'emulatore di archiviazione di Azure per sviluppo e test](/azure/storage/common/storage-use-emulator).

Nell'elenco seguente include alcuni dei più popolari sistemi di database che possono essere usati nei progetti di Visual Studio. L'elenco non è completo. Per un elenco di fornitori di terze parti che offrono i provider di dati ADO.NET che consentono una profonda integrazione con strumenti di Visual Studio, vedere [provider di dati ADO.NET](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server è il database fiore all'occhiello di Microsoft che offre. SQL Server 2016 offre prestazioni elevate, sicurezza avanzata e creazione report completa e integrata e analitica. È disponibile in diverse edizioni che sono progettate per usi diversi: da analitica aziendali altamente scalabili e ad alte prestazioni, da usare in un singolo computer. SQL Server Express è un'edizione completa di SQL Server in cui è stato sviluppato specificamente per la ridistribuzione e l'incorporamento.  LocalDB è una versione semplificata di SQL Server Express che non richiede alcuna configurazione e viene eseguito nel processo dell'applicazione. È possibile scaricare uno o entrambi i prodotti dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Molti degli esempi SQL in questa sezione utilizzare LocalDB di SQL Server. SQL Server Management Studio (SSMS) è un'applicazione di gestione di database autonomo con più funzionalità rispetto a quella illustrata in Esplora oggetti di Server SQL di Visual Studio. È possibile ottenere SQL Server Management Studio dal collegamento precedente.

## <a name="oracle"></a>Oracle

È possibile scaricare una versione a pagamento o gratuita del database Oracle dal [rete tecnologia Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) pagina. Per il supporto in fase di progettazione per Entity Framework e gli oggetti TableAdapter, è necessario il [strumenti di sviluppo Oracle per Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Altri prodotti Oracle ufficiali, tra cui Oracle Instant Client, sono disponibili tramite Gestione pacchetti NuGet. È possibile scaricare gli schemi di esempio Oracle, seguendo le istruzioni nel [documentazione online Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL è un sistema di database open source più diffusi che è ampiamente usato in aziende e siti Web. Download per MySQL e MySQL per Visual Studio e prodotti correlati telemetra [MySQL in Windows](http://www.mysql.com/why-mysql/windows/). Terze parti offrono varie estensioni di Visual Studio e le applicazioni di gestione autonoma per MySQL. È possibile esplorare le offerte in Gestione pacchetti NuGet (**degli strumenti** > **Gestione pacchetti NuGet** > **Gestisci pacchetti NuGet per la soluzione**) .

## <a name="postgresql"></a>PostgreSQL

PostgreSQL è un sistema di database relazionale di oggetti gratuito e open source. Per installarlo in Windows, è possibile scaricarlo dal [pagina di download di PostgreSQL](http://www.postgresql.org/download/windows/). È anche possibile compilare PostgreSQL dal codice sorgente. Il sistema di PostgreSQL core include un'interfaccia di linguaggio C. Molte terze parti offrono i pacchetti NuGet per l'uso di PostgreSQL dalle applicazioni .NET. È possibile esplorare le offerte in Gestione pacchetti NuGet (**degli strumenti** > **Gestione pacchetti NuGet** > **Gestisci pacchetti NuGet per la soluzione**) . Ad esempio, il più diffuso pacchetto avviene tramite [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite è un motore di database SQL incorporato che viene eseguito nel processo dell'applicazione. È possibile scaricarlo dal [pagina di download di SQLite](http://www.sqlite.org/download.html). Sono disponibili anche molti pacchetti NuGet di terze parti per SQLite. È possibile esplorare le offerte in Gestione pacchetti NuGet (**degli strumenti** > **Gestione pacchetti NuGet** > **Gestisci pacchetti NuGet per la soluzione**) .

## <a name="firebird"></a>Firebird

Firebird è un sistema di database SQL open source. È possibile scaricarlo dal [pagina di download Firebird](http://firebirdsql.org/en/downloads/). Provider di dati ADO.NET è disponibile tramite Gestione pacchetti NuGet.

## <a name="see-also"></a>Vedere anche

- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Come determinare la versione e l'edizione di SQL Server e dei relativi componenti](http://support.microsoft.com/kb/321185)