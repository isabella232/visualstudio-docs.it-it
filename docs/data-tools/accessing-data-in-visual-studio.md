---
title: Strumenti e l'accesso ai dati
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 9b3d41ab51e2f7f7e410e9c8443d864ab46328b2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979942"
---
# <a name="access-data-in-visual-studio"></a>Accedere ai dati in Visual Studio

In Visual Studio, è possibile creare applicazioni che si connettono ai dati in qualsiasi prodotto di database o servizio, in qualsiasi formato, ovunque, in un computer locale, in una rete locale o in un cloud pubblico, privato o ibrido.

Le applicazioni in JavaScript, Python, PHP, Ruby o C++, è necessario connettersi ai dati come si farebbe altro, ottenendo le librerie e la scrittura di codice. Per le applicazioni .NET, Visual Studio offre strumenti che è possibile usare per esplorare le origini dati, creare modelli a oggetti per archiviare e manipolare i dati in memoria e associare i dati all'interfaccia utente. Microsoft Azure offre SDK per .NET, Java, Node. js, PHP, Python, Ruby e App per dispositivi mobili e gli strumenti in Visual Studio per la connessione ad archiviazione di Azure.

Gli elenchi seguenti illustrano solo alcune di molti sistemi di archiviazione e database che possono essere utilizzati da Visual Studio. Il [Microsoft Azure](https://azure.microsoft.com/) offerte sono servizi dati che includono tutti i provisioning e l'amministrazione di archivio dati sottostante. Il **sviluppo di Azure** carico di lavoro in [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) consente di lavorare con gli archivi dati di Azure direttamente da Visual Studio.

![Carico di lavoro Sviluppo di Azure](media/azure-development-workload.png)

La maggior parte dei altri SQL e NoSQL database prodotti sono elencati di seguito possono essere ospitata in un computer locale, in una rete locale o in Microsoft Azure in una macchina virtuale. Se si ospita il database in una macchina virtuale di Microsoft Azure, si è responsabili della gestione del database stesso.

**Microsoft Azure**

- Database SQL
- Azure Cosmos DB
- Archiviazione (BLOB, tabelle, code, file)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- E molto altro ancora.

**SQL**

- SQL Server 2005-2016 (include Express e database locale)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- E molto altro ancora.

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB|
- RavenDB
- VelocityDB
- E molto altro ancora.

Molti fornitori di database e di terze parti supportano l'integrazione di Visual Studio per i pacchetti NuGet. È possibile esplorare le offerte in nuget.org o tramite Gestione pacchetti NuGet in Visual Studio (**degli strumenti** > **Gestione pacchetti NuGet** > **Gestisci NuGet Pacchetti per la soluzione**). Altri prodotti di database si integrano con Visual Studio come un'estensione. È possibile esplorare queste offerte in Visual Studio Marketplace, passare a **Tools**, **estensioni e aggiornamenti** e quindi selezionando **Online** nel riquadro sinistro della finestra di finestra di dialogo. Per altre informazioni, vedere [sistemi di database compatibili per Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Supporto "Extended" per SQL Server 2005 è terminato il 12 aprile 2016. Non c'è garanzia che gli strumenti dati in Visual Studio 2015 e versioni successive continuano a funzionare con SQL Server 2005 dopo tale data. Per altre informazioni, vedere la [annuncio di fine del supporto per SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Linguaggi .NET

Tutti gli accessi di dati .NET, incluso in .NET Core sono basato su ADO.NET, un set di classi che definisce un'interfaccia per l'accesso a qualsiasi tipo di origine dati, relazionali e non relazionali. Visual Studio include diversi strumenti e finestre di progettazione che funzionano con ADO.NET per eseguire la connessione ai database, modificare i dati e presentarli all'utente. La documentazione in questa sezione descrive come usare questi strumenti. È anche possibile programmare direttamente usando gli oggetti comando ADO.NET. Per altre informazioni sulla chiamata ADO.NET APIs direttamente, vedere [ADO.NET](/dotnet/framework/data/adonet/index).

Per la documentazione di accesso ai dati correlata ad ASP.NET, vedere [utilizzo di dati](https://www.asp.net/web-forms/overview/presenting-and-managing-data) sul sito ASP.NET. Per un'esercitazione sull'uso di Entity Framework con MVC ASP.NET, vedere [Introduzione a Entity Framework 6 Code First con MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

App universali di Windows Platform (UWP) in C# o Visual Basic possono usare Microsoft Azure SDK per .NET per accedere all'archiviazione di Azure e altri servizi di Azure. La classe Windows.Web.HttpClient consente la comunicazione con qualsiasi servizio RESTful. Per altre informazioni, vedere [come connettersi a un server HTTP utilizzando consente](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Per l'archiviazione dei dati nel computer locale, l'approccio consigliato consiste nell'utilizzare SQLite, che viene eseguito nello stesso processo dell'app. Se è necessario un livello di mapping relazionale a oggetti (ORM), è possibile usare Entity Framework. Per altre informazioni, vedere [DAS](/windows/uwp/data-access/index) nel Centro sviluppatori Windows.

Se ci si connette ai servizi di Azure, assicurarsi di scaricare la versione più recente [strumenti di Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Provider di dati

Per un database essere utilizzabile in ADO.NET, deve avere una classe personalizzata *provider di dati ADO.NET* o altrimenti deve esporre un'interfaccia ODBC o OLE DB. Microsoft fornisce una [elenco di provider di dati ADO.NET](https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) per i prodotti SQL Server, nonché i provider OLE DB e ODBC.

### <a name="data-modeling"></a>Modellazione dei dati

In .NET sono disponibili tre opzioni per la modellazione e la modifica dei dati in memoria dopo aver recuperato da un'origine dati:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) della tecnologia ORM Microsoft preferita. È possibile utilizzare per la programmazione per dati relazionali come oggetti .NET prima classe. Per le nuove applicazioni, deve essere la prima opzione predefinita quando un modello è obbligatorio. Richiede supporto personalizzato dal provider ADO.NET sottostante.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) un mapper relazionale a oggetti di generazione precedente. Funziona bene per scenari meno complessi, ma non è più in fase di sviluppo attivo.

[I set di dati](../data-tools/dataset-tools-in-visual-studio.md) dal meno recente delle tre tecnologie di modellazione. È progettato principalmente per lo sviluppo rapido di applicazioni "Form over data" in cui è non sono enormi quantità di dati di elaborazione o esecuzione di query complesse o trasformazioni. Un oggetto set di dati è costituito da oggetti DataTable e DataRow in modo logico sono simili a oggetti di database SQL molto più di oggetti .NET. Per le applicazioni relativamente semplici basate su origini dati SQL, i set di dati potrebbe essere comunque una scelta ottimale.

Non è necessario usare uno qualsiasi di queste tecnologie. In alcuni scenari, specialmente quando le prestazioni sono critiche, è possibile semplicemente utilizzare un oggetto DataReader per leggere dal database e copiare i valori desiderati in un oggetto raccolta, ad esempio elenco\<T >.

## <a name="native-c"></a>C++ nativo

Le applicazioni C++ che si connettono a SQL Server devono usare la [Microsoft® ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) nella maggior parte dei casi. Se i server collegati, OLE DB è necessaria e per cui usano i [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). È possibile accedere ad altri database usando [ODBC](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) o driver OLE DB direttamente. ODBC è l'interfaccia standard del database corrente, ma la maggior parte dei sistemi di database forniscono funzionalità personalizzate che non sono accessibili tramite l'interfaccia ODBC. OLE DB è una tecnologia di accesso ai dati COM legacy che è ancora supportata ma non consigliata per le nuove applicazioni. Per altre informazioni, vedere [l'accesso ai dati in Visual C++](/cpp/data/data-access-in-cpp).

I programmi C++ che usano servizi REST è possono usare la [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

I programmi C++ che funzionano con archiviazione di Microsoft Azure possono usare la [il Client di archiviazione di Microsoft Azure](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

Modellazione dei dati&mdash;Visual Studio non fornisce un livello ORM per C++. [ODB](https://www.codesynthesis.com/products/odb/) è un prodotto ORM open source più diffusi per C++.

Per altre informazioni sulla connessione ai database da app C++, vedere [Visual Studio data tools per C++](../data-tools/visual-studio-data-tools-for-cpp.md). Per altre informazioni sulle tecnologie di accesso ai dati legacy Visual C++, vedere [DAS](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript in Visual Studio](/scripting/javascript/javascript-language-reference) è un ottimo linguaggio per la creazione di App multipiattaforma, le app UWP, servizi cloud, siti Web e App web. È possibile usare Bower, Grunt, Gulp, npm e NuGet da Visual Studio per installare le librerie JavaScript preferite e dei prodotti del database. Connettersi ad archiviazione di Azure e servizi, scaricare gli SDK del [sito Web di Azure](https://azure.microsoft.com/). Edge. js è una libreria che si connette lato server JavaScript (Node. js) a origini dati ADO.NET.

## <a name="python"></a>Python

Installare [supporto di Python in Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) per creare applicazioni Python. Documentazione di Azure presenta numerose esercitazioni sulla connessione ai dati, inclusi i seguenti:

- [Django e Database SQL in Azure](/azure/app-service/app-service-web-get-started-python)
- [Django e MySQL in Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Rivolgersi [BLOB](/azure/storage/blobs/storage-quickstart-blobs-python), [file](/azure/storage/files/storage-python-how-to-use-file-storage), [code](/azure/storage/queues/storage-python-how-to-use-queue-storage), e [tabelle (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Argomenti correlati

[Piattaforma Microsoft AI](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;fornisce un'introduzione a Microsoft intelligent cloud, tra cui Cortana Analitica Suite e supporto per Internet delle cose.

[Archiviazione di Microsoft Azure](/azure/storage/)&mdash;descrive archiviazione di Azure e su come creare applicazioni usando BLOB di Azure, tabelle, code e file.

[Database SQL di Azure](/azure/sql-database/)&mdash;viene descritto come connettersi al Database SQL di Azure, un database relazionale come servizio.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;vengono descritti gli strumenti che semplificano la progettazione, esplorazione, test e distribuzione di applicazioni basate su dati e database.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;descrive l'architettura ADO.NET e come usare le classi ADO.NET per gestire i dati dell'applicazione e interagire con le origini dati e XML.

[ADO.NET Entity Framework](https://docs.microsoft.com/ef/ef6/)&mdash;viene descritto come creare applicazioni di dati che consentono agli sviluppatori di programmare sulla base di un modello concettuale anziché direttamente in un database relazionale.

[WCF Data Services 4.5](/dotnet/framework/data/wcf/index)&mdash;viene descritto come utilizzare [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] per distribuire servizi dati nel web o in una rete intranet che implementano il [Open Data Protocol (OData)](https://www.odata.org/).

[I dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)&mdash;contiene collegamenti ad argomenti che illustrano il funzionamento dei dati nelle soluzioni Office. Sono incluse informazioni sulla programmazione orientata agli schemi, la memorizzazione nella cache di dati e l'accesso ai dati sul lato server.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;descrive le funzionalità di query incorporate in C# e Visual Basic e il modello comune per l'esecuzione di query su database relazionali, documenti XML, i set di dati e raccolte in memoria.

[Strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;illustra l'uso di funzionalità XML di .NET Framework i dati, debug XSLT, XML e l'architettura di Query XML.

[Documenti e dati XML](/dotnet/standard/data/xml/index)&mdash;offre una panoramica a un set completo e integrato di classi che funzionano con i documenti XML e i dati in .NET Framework.
