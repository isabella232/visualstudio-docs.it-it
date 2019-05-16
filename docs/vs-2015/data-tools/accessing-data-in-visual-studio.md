---
title: L'accesso ai dati
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
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 7f13a97adbec1da1bd0f279e14cf510532b9c62f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688628"
---
# <a name="accessing-data-in-visual-studio"></a>Accesso ai dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, è possibile creare applicazioni che si connettono ai dati in qualsiasi prodotto di database o servizio, in qualsiasi formato, ovunque, in un computer locale, in una rete locale o in un cloud pubblico, privato o ibrido.

 Le applicazioni in JavaScript, Python, PHP, Ruby o C++, è necessario connettersi ai dati come si farebbe altro, ottenendo le librerie e la scrittura di codice. Per le applicazioni .NET, Visual Studio offre strumenti che è possibile usare per esplorare le origini dati, creare modelli a oggetti per archiviare e manipolare i dati in memoria e associare i dati all'interfaccia utente.     Microsoft Azure offre SDK per .NET, Java, Node. js, PHP, Python, Ruby e App per dispositivi mobili e gli strumenti in Visual Studio per la connessione ad archiviazione di Azure.

 Gli elenchi seguenti illustrano solo alcune di molti sistemi di archiviazione e database che possono essere utilizzati da Visual Studio. Il [Microsoft Azure](https://azure.microsoft.com/) offerte sono servizi dati che includono tutti i provisioning e l'amministrazione di archivio dati sottostante.  [Gli strumenti di Azure per Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) è un componente facoltativo che consente di lavorare con gli archivi dati di Azure direttamente da Visual Studio. La maggior parte dei altri SQL e NoSQL database prodotti sono elencati di seguito possono essere ospitata in un computer locale, in una rete locale o in Microsoft Azure in una macchina virtuale. In questo scenario, si è responsabili della gestione del database stesso.

 **Microsoft Azure**

||||
|-|-|-|
|Database SQL|DocumentDB|Archiviazione (BLOB, tabelle, code, file)|
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|

 E molto altro ancora.

 **SQL**

||||
|-|-|-|
|SQL Server 2005 – 2016, tra cui LocalDB ed Express|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

 E molto altro ancora.

 **NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|NDatabase|OrientDB|RavenDB|
|VelocityDB|||

 E molto altro ancora.

 Molti fornitori di database e di terze parti supportano l'integrazione di Visual Studio per i pacchetti NuGet. È possibile esplorare le offerte in nuget.org o tramite Gestione pacchetti NuGet in Visual Studio (**degli strumenti** > **Gestione pacchetti NuGet** > **Gestisci NuGet Pacchetti per la soluzione**). Altri prodotti di database si integrano con Visual Studio come un'estensione.   È possibile esplorare queste offerte in Visual Studio Gallery, passare a **degli strumenti** > **estensioni e aggiornamenti** e quindi scegliendo **Online** in a sinistra riquadro della finestra di dialogo.  Per altre informazioni, vedere [installazione di sistemi di database, strumenti ed esempi](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Supporto "Extended" per SQL Server 2005 è terminato il 12 aprile 2016.   Non c'è garanzia che gli strumenti dati in Visual Studio 2015 e versioni successive continuano a funzionare con SQL Server 2005 dopo tale data. Per altre informazioni, vedere la [annuncio di fine del supporto per SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Linguaggi .NET
 Tutti gli accessi di dati .NET, incluso in .NET Core sono basato su ADO.NET, un set di classi che definisce un'interfaccia per l'accesso a qualsiasi tipo di origine dati, relazionali e non relazionali. Visual Studio include diversi strumenti e finestre di progettazione che funzionano con ADO.NET per eseguire la connessione ai database, modificare i dati e presentarli all'utente. La documentazione in questa sezione descrive come usare questi strumenti. È anche possibile programmare direttamente usando gli oggetti comando ADO.NET. Per altre informazioni sulla chiamata ADO.NET APIs direttamente, vedere [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) in MSDN Library.

 Per la documentazione di accesso ai dati correlata in modo specifico per ASP.NET, vedere [utilizzo di dati](http://www.asp.net/web-forms/overview/presenting-and-managing-data) sul sito ASP.NET. Per un'esercitazione sull'uso di Entity Framework con MVC ASP.NET, vedere [Introduzione a Entity Framework 6 Code First con MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Universal Windows Platform (UWP) le App in c# o Visual Basic possono usare Microsoft Azure SDK per .NET per accedere all'archiviazione di Azure e altri servizi di Azure. La classe Windows.Web.HttpClient consente la comunicazione con qualsiasi servizio RESTful. Per altre informazioni, vedere [come connettersi a un server HTTP utilizzando consente](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 Per l'archiviazione dei dati nel computer locale, l'approccio consigliato consiste nell'utilizzare SQLite, che viene eseguito nello stesso processo dell'app. Se è necessario un livello di mapping relazionale a oggetti (ORM), è possibile usare Entity Framework. Per altre informazioni, vedere [DAS](https://msdn.microsoft.com/windows/uwp/data-access/index) nel Centro sviluppatori Windows.

 Se ci si connette ai servizi di Azure, assicurarsi di scaricare la versione più recente [strumenti di Azure SDK](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Provider di dati
 Per un database essere utilizzabile in ADO.NET, deve avere una classe personalizzata *provider di dati ADO.NET* o altrimenti deve esporre un'interfaccia ODBC o OLE DB. Microsoft fornisce una [elenco di provider di dati ADO.NET](https://msdn.microsoft.com/data/dd363565) per i prodotti SQL Server, nonché i provider OLE DB e ODBC.

#### <a name="data-modeling"></a>Modellazione dei dati
 In .NET sono disponibili tre opzioni per la modellazione e la modifica dei dati in memoria dopo aver recuperato da un'origine dati:

 Entity Framework della tecnologia ORM Microsoft preferita. È possibile utilizzare per la programmazione per dati relazionali come oggetti .NET prima classe. Per le nuove applicazioni, deve essere la prima opzione predefinita quando un modello è obbligatorio. Richiede supporto personalizzato dal provider ADO.NET sottostante.

 LINQ to SQL un mapper relazionale a oggetti di generazione precedente. Funziona bene per scenari meno complessi, ma non è più in fase di sviluppo attivo.

 I set di dati meno recenti delle tre tecnologie di modellazione. È progettato principalmente per lo sviluppo rapido di applicazioni "Form over data" in cui è non sono enormi quantità di dati di elaborazione o esecuzione di query complesse o trasformazioni. Un oggetto set di dati è costituito da oggetti DataTable e DataRow in modo logico sono simili a oggetti di database SQL molto più di oggetti .NET. Per le applicazioni relativamente semplici basate su origini dati SQL, i set di dati potrebbe essere comunque una scelta ottimale.

 Non è necessario usare uno qualsiasi di queste tecnologie. In alcuni scenari, specialmente quando le prestazioni sono critiche, è possibile semplicemente utilizzare un oggetto DataReader per leggere dal database e copiare i valori desiderati in un oggetto raccolta, ad esempio elenco\<T >.

### <a name="native-c"></a>C++ nativo
 Le applicazioni C++ che si connettono a SQL Server devono usare la [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). È possibile accedere ad altri database usando [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) o driver OLE DB direttamente. ODBC è l'interfaccia standard del database corrente, ma la maggior parte dei sistemi di database forniscono funzionalità personalizzate che non sono accessibili tramite l'interfaccia ODBC.  OLE DB è una tecnologia di accesso ai dati COM legacy che è ancora supportata ma non consigliata per le nuove applicazioni.  Per altre informazioni, vedere [DAS](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 I programmi C++ che usano servizi REST è possono usare la [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

 I programmi C++ che funzionano con archiviazione di Microsoft Azure possono usare la [il Client di archiviazione di Microsoft Azure](http://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Modellazione dei dati
 Visual Studio non fornisce un livello ORM per C++.  [ODB](http://www.codesynthesis.com/products/odb/) è un prodotto ORM open source più diffusi per C++.

 Per altre informazioni sulle tecnologie di accesso ai dati legacy Visual C++, vedere [l'accesso ai dati](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [JavaScript in Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) è un ottimo linguaggio per la creazione di App multipiattaforma, le app UWP, servizi cloud, siti Web e App web. È possibile usare Bower, Grunt, Gulp, npm e NuGet da Visual Studio per installare le librerie JavaScript preferite e dei prodotti del database. Connettersi ad archiviazione di Azure e servizi, scaricare gli SDK del [sito Web di Azure](https://azure.microsoft.com/).  Edge. js è una libreria che si connette lato server JavaScript (Node. js) a origini dati ADO.NET.

### <a name="python"></a>Python
 Installare [Python Tools per Visual Studio](http://microsoft.github.io/PTVS/) con il tuo framework Python preferito per creare applicazioni CPython o IronPython (.NET).  Gli strumenti Python per il sito Web di Visual Studio ha numerose esercitazioni sulla connessione ai dati, inclusi [Django e Database SQL in Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django e MySQL in Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) e [Bottle e MongoDB in Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>Contenuto della sezione
 [Installazione di sistemi di database, strumenti ed esempi](../data-tools/installing-database-systems-tools-and-samples.md) illustra come ottenere prodotti del database e le estensioni di Visual Studio o i driver che li supportano e dove trovare i database di esempio per scopi di apprendimento e sperimentazione.

 [Visual Studio data tools per .NET](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) descrive come usare finestre degli strumenti di Visual Studio per connettersi alle origini dati, creare i set di dati o modelli di Entity Framework e associare i dati a controlli dell'interfaccia utente.

## <a name="related-topics"></a>Argomenti correlati
 [I dati, dispositivi e Analitica](https://msdn.microsoft.com/data-and-devices) fornisce un'introduzione a Microsoft intelligent cloud, tra cui Cortana Analitica Suite e supporto per Internet delle cose.

 [Archiviazione di Microsoft Azure](/azure/storage/) descrive archiviazione di Azure e su come creare applicazioni usando BLOB di Azure, tabelle, code e file.

 [Database SQL di Azure](https://azure.microsoft.com/documentation/services/sql-database/) viene descritto come connettersi al Database SQL di Azure, un database relazionale come servizio.

 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) vengono descritti gli strumenti che semplificano la progettazione, esplorazione, test e distribuzione di applicazioni basate su dati e database.

 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) descrive l'architettura ADO.NET e come usare le classi ADO.NET per gestire i dati dell'applicazione e interagire con le origini dati e XML.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) viene descritto come creare applicazioni di dati che consentono agli sviluppatori di programmare sulla base di un modello concettuale anziché direttamente in un database relazionale.

 [WCF Data Services 4.5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) viene descritto come utilizzare [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] per distribuire servizi dati nel web o in una rete intranet che implementano le [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

 [I dati nelle soluzioni Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) contiene collegamenti ad argomenti che illustrano il funzionamento dei dati nelle soluzioni Office. Sono incluse informazioni sulla programmazione orientata agli schemi, la memorizzazione nella cache di dati e l'accesso ai dati sul lato server.

 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) descrive le funzionalità di query incorporate in C# e Visual Basic e il modello comune per l'esecuzione di query su database relazionali, documenti XML, i set di dati e raccolte in memoria.

 [Strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) illustra l'uso di funzionalità XML di .NET Framework i dati, debug XSLT, XML e l'architettura di Query XML.

 [Documenti e dati XML](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) offre una panoramica a un set completo e integrato di classi che funzionano con i documenti XML e i dati in .NET Framework.
