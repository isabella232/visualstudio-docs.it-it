---
title: Accesso ai dati
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 78d950b777d866835ef516c4910180b21de295e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545002"
---
# <a name="accessing-data-in-visual-studio"></a>Accesso ai dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio è possibile creare applicazioni che si connettono ai dati praticamente in qualsiasi prodotto o servizio del database, in qualsiasi formato, in qualsiasi posizione, in un computer locale, in una rete locale o in un cloud pubblico, privato o ibrido.

 Per le applicazioni in JavaScript, Python, PHP, Ruby o C++, è possibile connettersi ai dati, come per qualsiasi altra operazione, ottenendo le librerie e scrivendo il codice. Per le applicazioni .NET, Visual Studio fornisce strumenti che è possibile usare per esplorare le origini dati, creare modelli a oggetti per archiviare e modificare i dati in memoria e associare dati all'interfaccia utente.     Microsoft Azure offre SDK per .NET, Java, Node.js, PHP, Python, Ruby e app per dispositivi mobili e strumenti in Visual Studio per la connessione ad archiviazione di Azure.

 Negli elenchi seguenti vengono illustrati solo alcuni dei numerosi sistemi di database e di archiviazione che possono essere utilizzati da Visual Studio. Le offerte di [Microsoft Azure](https://azure.microsoft.com/) sono servizi dati che includono tutto il provisioning e l'amministrazione dell'archivio dati sottostante.  [Strumenti di Azure per Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) è un componente facoltativo che consente di lavorare con gli archivi dati di Azure direttamente da Visual Studio. La maggior parte degli altri prodotti di database SQL e NoSQL elencati qui può essere ospitata in un computer locale, in una rete locale o in Microsoft Azure in una macchina virtuale. In questo scenario, l'utente è responsabile della gestione del database stesso.

 **Microsoft Azure**

- Database SQL

- DocumentDB

-Archiviazione (BLOB, tabelle, code, file)

- SQL Data Warehouse

- SQL Server Stretch Database

- StorSimple

 E altro ancora

 **SQL**

- SQL Server 2005 – 2016, tra cui Express e local DB
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite

 E altro ancora

 **NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB
- RavenDB
- VelocityDB

 E altro ancora

 Molti fornitori di database e terze parti supportano l'integrazione di Visual Studio da pacchetti NuGet. È possibile esplorare le offerte in NuGet.org o tramite Gestione pacchetti NuGet in Visual Studio (**strumenti**  >  **gestione**pacchetti NuGet  >  **Gestisci pacchetti NuGet per la soluzione**). Altri prodotti di database si integrano con Visual Studio come estensione.   È possibile esplorare queste offerte in Visual Studio Gallery passando a **strumenti**  >  **estensioni e aggiornamenti** e quindi selezionando **online** nel riquadro sinistro della finestra di dialogo.  Per ulteriori informazioni, vedere [installazione di sistemi di database, strumenti ed esempi](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Il supporto esteso per SQL Server 2005 è terminato il 12 aprile 2016.   Non vi è alcuna garanzia che gli strumenti dati in Visual Studio 2015 e versioni successive continueranno a funzionare con SQL Server 2005 dopo tale data. Per ulteriori informazioni, vedere l' [annuncio di fine del supporto tecnico per SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Linguaggi .NET
 Tutti gli accessi ai dati .NET, incluso in .NET Core, sono basati su ADO.NET, un set di classi che definisce un'interfaccia per l'accesso a qualsiasi tipo di origine dati, sia relazionale che non relazionale. Visual Studio include diversi strumenti e finestre di progettazione che funzionano con ADO.NET per semplificare la connessione ai database, modificare i dati e presentare i dati all'utente. La documentazione in questa sezione descrive come usare questi strumenti. È anche possibile programmare direttamente con gli oggetti comando ADO.NET. Per ulteriori informazioni sulla chiamata diretta delle API ADO.NET, vedere [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) in MSDN Library.

 Per la documentazione relativa all'accesso ai dati specificamente correlata a ASP.NET, vedere  [utilizzo dei dati](/aspnet/web-forms/overview/presenting-and-managing-data/) nel sito di ASP.NET. Per un'esercitazione sull'uso di Entity Framework con ASP.NET MVC, vedere [Introduzione con Entity Framework 6 Code First con MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Le app piattaforma UWP (Universal Windows Platform) (UWP) in C# o Visual Basic possono usare la Microsoft Azure SDK per .NET per accedere ad archiviazione di Azure e ad altri servizi di Azure. La classe Windows. Web. HttpClient consente la comunicazione con qualsiasi servizio RESTful. Per ulteriori informazioni, vedere [come connettersi a un server http utilizzando Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 Per l'archiviazione dei dati nel computer locale, l'approccio consigliato consiste nell'usare SQLite, che viene eseguito nello stesso processo dell'app. Se è necessario un livello ORM (Object-Relational Mapping), è possibile usare Entity Framework. Per ulteriori informazioni, vedere [accesso ai dati](https://msdn.microsoft.com/windows/uwp/data-access/index) nel centro per sviluppatori Windows.

 Se ci si connette ai servizi di Azure, assicurarsi di scaricare gli strumenti più recenti di [Azure SDK](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Provider di dati
 Affinché un database sia utilizzabile in ADO.NET, è necessario che disponga di un *provider di dati ADO.NET* personalizzato. in caso contrario, deve esporre un'interfaccia ODBC o OLE DB. Microsoft fornisce un [elenco di provider di dati ADO.NET](https://msdn.microsoft.com/data/dd363565) per SQL Server prodotti, nonché per i provider ODBC e OLE DB.

#### <a name="data-modeling"></a>Modellazione dati
 In .NET sono disponibili tre opzioni per la modellazione e la modifica dei dati in memoria dopo che è stato recuperato da un'origine dati:

 Entity Framework la tecnologia Microsoft ORM preferita. È possibile usarlo per programmare in base ai dati relazionali come oggetti .NET di prima classe. Per le nuove applicazioni, deve essere la prima scelta predefinita quando è necessario un modello. Richiede il supporto personalizzato del provider ADO.NET sottostante.

 LINQ to SQL un mapper relazionale a oggetti di generazione precedente. Funziona bene per scenari meno complessi, ma non è più in fase di sviluppo attivo.

 Imposta i set di impostazioni meno recenti delle tre tecnologie di modellazione. È progettato principalmente per lo sviluppo rapido di applicazioni "form su dati" in cui non si elaborano grandi quantità di dati o si eseguono query o trasformazioni complesse. Un oggetto DataSet è costituito da oggetti DataTable e DataRow che sono logicamente simili a oggetti di database SQL molto più di oggetti .NET. Per le applicazioni relativamente semplici basate sulle origini dati SQL, è possibile che i set di dati siano ancora una scelta ottimale.

 Non è necessario usare nessuna di queste tecnologie. In alcuni scenari, soprattutto se le prestazioni sono fondamentali, è possibile usare semplicemente un oggetto DataReader per leggere dal database e copiare i valori necessari in un oggetto raccolta, ad esempio List \<T> .

### <a name="native-c"></a>C++ nativo
 Le applicazioni C++ che si connettono a SQL Server devono usare il [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). È possibile accedere ad altri database usando direttamente i driver [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) o OLE DB. ODBC è l'interfaccia di database standard corrente, ma la maggior parte dei sistemi di database fornisce funzionalità personalizzate a cui non è possibile accedere tramite l'interfaccia ODBC.  OLE DB è una tecnologia di accesso ai dati COM legacy che è ancora supportata ma non consigliata per le nuove applicazioni.  Per ulteriori informazioni, vedere [accesso ai dati](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 I programmi c++ che utilizzano i servizi REST possono utilizzare [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

 I programmi C++ che funzionano con Archiviazione di Microsoft Azure possono usare il [client di archiviazione di Microsoft Azure](https://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Modellazione dati
 Visual Studio non fornisce un livello ORM per C++.  [ODB](https://www.codesynthesis.com/products/odb/) è un noto ORM open source per C++.

 Per ulteriori informazioni sulle tecnologie legacy di accesso ai dati Visual C++, vedere  [accesso ai dati](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [JavaScript in Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) è un linguaggio di prima classe per la creazione di app multipiattaforma, app UWP, servizi cloud, siti Web e app Web. È possibile usare Bower, grugnire, Gulp, NPM e NuGet da Visual Studio per installare le librerie JavaScript e i prodotti di database preferiti. Connettersi ad archiviazione e servizi di Azure scaricando gli SDK dal [sito Web di Azure](https://azure.microsoft.com/).  Edge.js è una libreria che connette JavaScript sul lato server (Node.js) alle origini dati ADO.NET.

### <a name="python"></a>Python
 Installare  [Python Tools for Visual Studio](http://microsoft.github.io/PTVS/) insieme al framework Python preferito per creare applicazioni CPython o IronPython (.NET).  Il sito Web di Python Tools for Visual Studio offre diverse esercitazioni sulla connessione ai dati, tra cui [Django e il database SQL in Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django e MySQL in Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) e [Bottle e MongoDB in Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>Contenuto della sezione
 [Installazione di sistemi di database, strumenti ed esempi](../data-tools/installing-database-systems-tools-and-samples.md) Viene illustrato come ottenere i prodotti di database e le estensioni o i driver di Visual Studio che li supportano, oltre a individuare i database di esempio a scopo di sperimentazione e apprendimento.

 [Visual Studio Data Tools per .NET](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) Viene descritto come utilizzare le finestre degli strumenti di Visual Studio per connettersi a origini dati, creare set di dati o modelli Entity Framework e associare i dati ai controlli dell'interfaccia utente.

## <a name="related-topics"></a>Argomenti correlati
 [Dati, dispositivi e analisi](https://msdn.microsoft.com/data-and-devices) Viene fornita un'introduzione a Microsoft Intelligent cloud, tra cui Cortanana Analytics suite e il supporto per Internet delle cose.

 [Archiviazione di Microsoft Azure](/azure/storage/) Descrive archiviazione di Azure e come creare applicazioni usando BLOB, tabelle, code e file di Azure.

 [Database SQL di Azure](https://azure.microsoft.com/documentation/services/sql-database/) Viene descritto come connettersi al database SQL di Azure, un database relazionale come servizio.

 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) Vengono descritti gli strumenti che semplificano la progettazione, l'esplorazione, il test e la distribuzione di applicazioni e database connessi ai dati.

 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) Viene descritta l'architettura ADO.NET e viene illustrato come utilizzare le classi ADO.NET per gestire i dati dell'applicazione e interagire con le origini dati e il codice XML.

 [Entity Framework ADO.NET](https://msdn.microsoft.com/data/ef) Viene descritto come creare applicazioni di dati che consentono agli sviluppatori di programmare in base a un modello concettuale anziché direttamente a un database relazionale.

 [WCF Data Services 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) Viene descritto come utilizzare [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] per distribuire servizi dati nel Web o in una rete Intranet che implementano il [Open Data Protocol (OData)](https://www.odata.org/).

 [Dati nelle soluzioni Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Contiene collegamenti ad argomenti che illustrano il funzionamento dei dati nelle soluzioni Office. Sono incluse informazioni sulla programmazione orientata agli schemi, sulla memorizzazione dei dati nella cache e sull'accesso ai dati sul lato server.

 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) Vengono descritte le funzionalità di query incorporate in C# e Visual Basic e il modello comune per l'esecuzione di query su database relazionali, documenti XML, set di dati e raccolte in memoria.

 [Strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) Viene illustrato l'utilizzo di dati XML, il debug di XSLT, .NET Framework funzionalità XML e l'architettura di XML Query.

 [Documenti e dati XML](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) Viene fornita una panoramica di un set completo e integrato di classi che funzionano con documenti e dati XML nel .NET Framework.
