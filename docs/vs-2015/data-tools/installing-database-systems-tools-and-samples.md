---
title: Installazione di sistemi di database, strumenti ed esempi | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1dea5adb6903c7beaf39c65909296224afa2a44c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518698"
---
# <a name="installing-database-systems-tools-and-samples"></a>Installazione di sistemi di database, strumenti ed esempi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [installazione di sistemi di database, strumenti ed esempi](https://docs.microsoft.com/visualstudio/data-tools/installing-database-systems-tools-and-samples).  
  
  
Visual Studio non include i sistemi di database diversi da quelli usati internamente. Per sviluppare un'applicazione dati connessi in Visual Studio, in genere installa il sistema di database nel computer di sviluppo locale e quindi distribuire l'applicazione e database in un ambiente di produzione quando sono pronte. Per il sistema di database deve essere accessibile da applicazioni .NET e per essere visibile nelle finestre di Visual Studio data tools, è necessario un provider di dati ADO.NET. Un provider deve supportare in modo specifico Entity Framework se si prevede di usare modelli di dati di entità nell'applicazione .NET.     Molti provider vengono offerti tramite Gestione pacchetti NuGet o tramite Visual Studio Gallery.  
  
 Per lo sviluppo di SQL, verificare di disporre di SQL Server Data Tools sia installato in Visual Studio. Scegliere il **vista** menu. Se non viene visualizzato Esplora oggetti di SQL Server, passare al pannello di controllo e modificare Visual Studio. Nel programma di installazione, selezionare **Microsoft SQL Server Data Tools**.  
  
 Se si usa le API di archiviazione di Azure, installare gli emulatori di archiviazione di Azure nel computer locale durante lo sviluppo per evitare addebiti non necessari finché non si è pronti per la distribuzione nell'ambiente di produzione. Per altre informazioni, vedere [usare l'emulatore di archiviazione di Azure per sviluppo e test](https://azure.microsoft.com/en-us/documentation/articles/storage-use-emulator/).  
  
 Nell'elenco seguente include alcuni dei più popolari sistemi di database che possono essere usati nei progetti di Visual Studio. L'elenco non è completo. Per un elenco di fornitori di terze parti che offrono i provider di dati ADO.NET che consentono una profonda integrazione con strumenti di Visual Studio, vedere [provider di dati ADO.NET](https://msdn.microsoft.com/library/dd363565.aspx).  
  
### <a name="microsoft-sql-server"></a>Microsoft SQL Server  
 SQL Server è il database fiore all'occhiello di Microsoft che offre. SQL Server 2016 offre prestazioni elevate, sicurezza avanzata e creazione report completa e integrata e analitica. È disponibile in diverse edizioni che sono progettate per usi diversi: da analitica aziendali altamente scalabili e ad alte prestazioni, da usare in un singolo computer. SQL Server Express è un'edizione completa di SQL Server in cui è stato sviluppato specificamente per la ridistribuzione e l'incorporamento.  LocalDB è una versione semplificata di SQL Server Express che non richiede alcuna configurazione e viene eseguito nel processo dell'applicazione. È possibile scaricare uno o entrambi i prodotti dal [pagina di download di SQL Server Express](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx).    Molti degli esempi SQL in questa sezione utilizzare LocalDB di SQL Server. SQL Server Management Studio (SSMS) è un'applicazione di gestione di database autonomo con più funzionalità rispetto a quella illustrata in Esplora oggetti di Server SQL di Visual Studio. È possibile ottenere SQL Server Management Studio dal collegamento precedente.  
  
### <a name="oracle"></a>Oracle  
 È possibile scaricare una versione a pagamento o gratuita del database Oracle dal [Oracle tecnologia rete](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) pagina. Per il supporto in fase di progettazione per Entity Framework e gli oggetti TableAdapter, è necessario il [strumenti di sviluppo Oracle per Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Altri prodotti Oracle ufficiali, tra cui Oracle Instant Client, sono disponibili tramite Gestione pacchetti NuGet.  È possibile scaricare gli schemi di esempio Oracle, seguendo le istruzioni nel [documentazione Online Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).  
  
### <a name="mysql"></a>MySQL  
 MySQL è un sistema di database open source più diffusi che è ampiamente usato in aziende e siti Web. Download per MySQL e MySQL per Visual Studio e prodotti correlati telemetra [MySQL in Windows](http://www.mysql.com/why-mysql/windows/).  Terze parti offrono varie estensioni di Visual Studio e le applicazioni di gestione autonoma per MySQL. È possibile esplorare le offerte in Gestione pacchetti NuGet (**degli strumenti** > **Gestione pacchetti NuGet** > **Gestisci pacchetti NuGet per la soluzione**) .  
  
### <a name="postgresql"></a>PostgreSQL  
 PostgreSQL è un sistema di database relazionale di oggetti gratuito e open source. Per installarlo in Windows, è possibile scaricarlo dal [pagina di download di PostgreSQL](http://www.postgresql.org/download/windows/).  È anche possibile compilare PostgreSQL dal codice sorgente.  Il sistema di PostgreSQL core include un'interfaccia di linguaggio C. Molte terze parti offrono i pacchetti NuGet per l'uso di PostgreSQL dalle applicazioni .NET.  È possibile esplorare le offerte in Gestione pacchetti NuGet (**degli strumenti** > **Gestione pacchetti NuGet** > **Gestisci pacchetti NuGet per la soluzione**) . Probabilmente il più diffuso pacchetto avviene tramite [npgsql.org](http://www.npgsql.org).  
  
### <a name="sqlite"></a>SQLite  
 SQLite è un motore di database SQL incorporato che viene eseguito nel processo dell'applicazione. È possibile scaricarlo dal [pagina di download di SQLite](http://www.sqlite.org/download.html). Sono disponibili anche molti pacchetti NuGet di terze parti per SQLite. È possibile esplorare le offerte in Gestione pacchetti NuGet (**degli strumenti** > **Gestione pacchetti NuGet** > **Gestisci pacchetti NuGet per la soluzione**) .  
  
### <a name="firebird"></a>Firebird  
 Firebird è un sistema di database SQL open source. È possibile scaricarlo dal [pagina di download Firebird](http://firebirdsql.org/en/downloads/). Provider di dati ADO.NET è disponibile tramite Gestione pacchetti NuGet.  
  
## <a name="see-also"></a>Vedere anche  
 [Come determinare la versione ed edizione di SQL Server e i relativi componenti](http://support.microsoft.com/kb/321185)

