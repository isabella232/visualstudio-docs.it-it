---
title: Compatibilità del database
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 94ce946f7c14706b57618f3d9aeb90cc207fcf04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648298"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Sistemi di database compatibili per Visual Studio

Per sviluppare un'applicazione connessa ai dati in Visual Studio, in genere si installa il sistema di database nel computer di sviluppo locale e quindi si distribuisce l'applicazione e il database in un ambiente di produzione quando sono pronti. Visual Studio installa SQL Server Express database locale nel computer come parte del carico di lavoro di **elaborazione e archiviazione dei dati** . Questa istanza del database locale è utile per lo sviluppo di applicazioni connesse ai dati in modo rapido e semplice.

Per poter accedere a un sistema di database dalle applicazioni .NET e renderlo visibile nelle finestre di Visual Studio Data Tools, è necessario che disponga di un provider di dati ADO.NET. Un provider deve supportare specificamente Entity Framework se si prevede di utilizzare Entity Data Model nell'applicazione .NET. Molti provider sono offerti tramite Gestione pacchetti NuGet o tramite il Visual Studio Marketplace.

Se si usano le API di archiviazione di Azure, installare gli emulatori di archiviazione di Azure nel computer locale durante lo sviluppo per evitare addebiti fino a quando non si è pronti per la distribuzione nell'ambiente di produzione. Per altre informazioni, vedere [usare l'emulatore di archiviazione di Azure per sviluppo e test](/azure/storage/common/storage-use-emulator).

Nell'elenco seguente sono inclusi alcuni dei sistemi di database più diffusi che è possibile utilizzare nei progetti di Visual Studio. L'elenco non è esaustivo. Per un elenco di fornitori di terze parti che offrono provider di dati ADO.NET che consentono una profonda integrazione con gli strumenti di Visual Studio, vedere [provider di dati ADO.NET](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server è l'offerta di database Microsoft Flagship. SQL Server 2016 offre prestazioni eccezionali, sicurezza avanzata e funzionalità avanzate di creazione di report e analisi integrate. Viene fornito in varie edizioni progettate per usi diversi: da analisi business a scalabilità elevata e a elevate prestazioni, da usare in un singolo computer. SQL Server Express è un'edizione completa di SQL Server personalizzata per la ridistribuzione e l'incorporamento.  Il database locale è un'edizione semplificata di SQL Server Express che non richiede alcuna configurazione ed è in esecuzione nel processo dell'applicazione. È possibile scaricare uno o entrambi i prodotti dalla [pagina di download SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Molti degli esempi SQL di questa sezione usano SQL Server database locale. SQL Server Management Studio (SSMS) è un'applicazione di gestione di database autonoma che offre più funzionalità rispetto a quelle disponibili in Visual Studio Esplora oggetti di SQL Server. È possibile ottenere SSMS dal collegamento precedente.

## <a name="oracle"></a>Oracle

È possibile scaricare un'edizione a pagamento o gratuita del database Oracle dalla pagina [rete della tecnologia Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) . Per il supporto in fase di progettazione per Entity Framework e TableAdapter, sarà necessario [Oracle Developer Tools per Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Altri prodotti Oracle ufficiali, incluso Oracle Instant client, sono disponibili tramite Gestione pacchetti NuGet. È possibile scaricare gli schemi di esempio Oracle seguendo le istruzioni riportate nella [documentazione online di Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL è un diffuso sistema di database open source ampiamente usato in aziende e siti Web. I download per MySQL, MySQL per Visual Studio e i prodotti correlati si trovano in [MySQL in Windows](http://www.mysql.com/why-mysql/windows/). Le terze parti offrono varie estensioni di Visual Studio e applicazioni di gestione autonoma per MySQL. È possibile esplorare le offerte in Gestione pacchetti NuGet (**strumenti**  > **gestione pacchetti NuGet**  > **gestire i pacchetti NuGet per la soluzione**).

## <a name="postgresql"></a>PostgreSQL

PostgreSQL è un sistema di database relazionale a oggetti open source gratuito. Per installarlo in Windows, è possibile scaricarlo dalla [pagina di download di PostgreSQL](http://www.postgresql.org/download/windows/). È anche possibile compilare PostgreSQL dal codice sorgente. Il sistema di base PostgreSQL include un'interfaccia del linguaggio C. Molte terze parti forniscono pacchetti NuGet per l'uso di PostgreSQL dalle applicazioni .NET. È possibile esplorare le offerte in Gestione pacchetti NuGet (**strumenti**  > **gestione pacchetti NuGet**  > **gestire i pacchetti NuGet per la soluzione**). Il pacchetto più diffuso è probabilmente fornito da [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite è un motore di database SQL incorporato che viene eseguito nel processo dell'applicazione. È possibile scaricarlo dalla [pagina di download di SQLite](http://www.sqlite.org/download.html). Sono disponibili anche molti pacchetti NuGet di terze parti per SQLite. È possibile esplorare le offerte in Gestione pacchetti NuGet (**strumenti**  > **gestione pacchetti NuGet**  > **gestire i pacchetti NuGet per la soluzione**).

## <a name="firebird"></a>Firebird

Firebird è un sistema open source per database SQL. È possibile scaricarlo dalla [pagina di download di Firebird](http://firebirdsql.org/en/downloads/). Un provider di dati ADO.NET è disponibile tramite Gestione pacchetti NuGet.

## <a name="see-also"></a>Vedere anche

- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Come determinare la versione e l'edizione di SQL Server e dei relativi componenti](http://support.microsoft.com/kb/321185)