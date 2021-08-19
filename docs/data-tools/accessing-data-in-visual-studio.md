---
title: Usare i dati in Visual Studio
description: Usare i dati in Visual Studio. Creare app che si connettono ai dati in altri prodotti o servizi di database su computer locali, LAN o cloud pubblici o privati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b6f79c38b599a66a9609bd88399f075f54f59dd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154979"
---
# <a name="work-with-data-in-visual-studio"></a>Usare i dati in Visual Studio

In Visual Studio è possibile creare applicazioni che si connettono ai dati praticamente in qualsiasi prodotto o servizio di database, in qualsiasi formato, ovunque, in un computer locale, in una rete locale o in un cloud pubblico, privato o ibrido.

Per le applicazioni in JavaScript, Python, PHP, Ruby o C++, è possibile connettersi ai dati come qualsiasi altra operazione, ottenendo librerie e scrivendo codice. Per le applicazioni .NET, Visual Studio offre strumenti che è possibile usare per esplorare le origini dati, creare modelli a oggetti per archiviare e modificare i dati in memoria e associare i dati all'interfaccia utente. Microsoft Azure offre SDK per app .NET, Java, Node.js, PHP, Python, Ruby e per dispositivi mobili e strumenti in Visual Studio per la connessione a Archiviazione di Azure.

::: moniker range="vs-2017"
Gli elenchi seguenti illustrano solo alcuni dei numerosi sistemi di database e archiviazione che possono essere usati da Visual Studio. Le [Microsoft Azure](https://azure.microsoft.com/) offerte sono servizi dati che includono tutto il provisioning e l'amministrazione dell'archivio dati sottostante. Il **carico di lavoro** Sviluppo di Azure Visual Studio [2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) consente di usare gli archivi dati di Azure direttamente da Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
Gli elenchi seguenti illustrano solo alcuni dei numerosi sistemi di database e archiviazione che possono essere usati da Visual Studio. Le [Microsoft Azure](https://azure.microsoft.com/) offerte sono servizi dati che includono tutto il provisioning e l'amministrazione dell'archivio dati sottostante. Il **carico di lavoro** Sviluppo di Azure Visual Studio [2019](https://visualstudio.microsoft.com/downloads) consente di usare gli archivi dati di Azure direttamente da Visual Studio.
::: moniker-end

![Carico Sviluppo di Azure](media/azure-development-workload.png)

La maggior parte degli altri prodotti di database SQL e NoSQL elencati qui può essere ospitata in un computer locale, in una rete locale o in Microsoft Azure in una macchina virtuale. Se si ospita il database in una Microsoft Azure virtuale, si è responsabili della gestione del database stesso.

**Microsoft Azure**

- Database SQL
- Azure Cosmos DB
- Archiviazione (BLOB, tabelle, code, file)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- E altro ancora

**SQL**

- SQL Server 2005-2016 (include Express e Local DB)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- E altro ancora

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB|
- RavenDB
- VelocityDB
- E altro ancora

::: moniker range="vs-2017"

Molti fornitori di database e terze parti supportano Visual Studio'integrazione NuGet pacchetti. È possibile esplorare le offerte in nuget.org o tramite il NuGet Gestione pacchetti in Visual Studio (**Strumenti** NuGet Gestione pacchetti Gestire NuGet  >    >  **pacchetti per la soluzione**). Altri prodotti di database si integrano con Visual Studio come estensione. È possibile esplorare queste offerte in [Visual Studio Marketplace](https://marketplace.visualstudio.com/) oppure passare a Strumenti Estensioni e aggiornamenti e quindi selezionare Online nel riquadro sinistro della  >   finestra di dialogo.  Per altre informazioni, vedere [Sistemi di database compatibili per Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Molti fornitori di database e terze parti supportano Visual Studio'integrazione NuGet pacchetti. È possibile esplorare le offerte in nuget.org o tramite il NuGet Gestione pacchetti in Visual Studio (**Strumenti** NuGet Gestione pacchetti Gestire NuGet  >    >  **pacchetti per la soluzione**). Altri prodotti di database si integrano con Visual Studio come estensione. È possibile esplorare queste offerte in [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o passando a Estensioni Gestisci estensioni e quindi selezionando Online nel riquadro sinistro della  >   finestra di dialogo.  Per altre informazioni, vedere [Sistemi di database compatibili per Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> Il supporto esteso per SQL Server 2005 è terminato il 12 aprile 2016. Non è garantito che gli strumenti dati in Visual Studio 2015 e versioni successive continueranno a funzionare con SQL Server 2005. Per altre informazioni, vedere l'annuncio della fine del supporto [per SQL Server 2005.](https://www.microsoft.com/sql-server/sql-server-2005)

## <a name="net-languages"></a>Linguaggi .NET

Tutti gli accessi ai dati .NET, incluso in .NET Core, si basano su ADO.NET, un set di classi che definisce un'interfaccia per l'accesso a qualsiasi tipo di origine dati, relazionale e non relazionale. Visual Studio dispone di diversi strumenti e finestre di progettazione che funzionano con ADO.NET per consentire la connessione ai database, modificare i dati e presentare i dati all'utente. La documentazione in questa sezione descrive come usare tali strumenti. È anche possibile programmare direttamente sugli oggetti ADO.NET comando. Per altre informazioni sulla chiamata diretta delle API ADO.NET, vedere [ADO.NET](/dotnet/framework/data/adonet/index).

Per la documentazione sull'accesso ai ASP.NET, vedere [Uso dei](https://www.asp.net/web-forms/overview/presenting-and-managing-data) dati nel sito ASP.NET dati. Per un'esercitazione sull'Entity Framework con ASP.NET MVC, vedere Attività iniziali [con Entity Framework 6 Code First MVC 5.](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)

Le app UWP (Universal Windows Platform) in C# o Visual Basic possono usare il Microsoft Azure SDK per .NET per accedere Archiviazione di Azure e altri servizi di Azure. Oggetto Windows. La classe Web.HttpClient consente la comunicazione con qualsiasi servizio RESTful. Per altre informazioni, vedere [Come connettersi a un server HTTP usando Windows. Web.Http](/previous-versions/windows/apps/dn469430(v=win.10)).

Per l'archiviazione dei dati nel computer locale, l'approccio consigliato consiste nell'usare SQLite, che viene eseguito nello stesso processo dell'app. Se è necessario un livello ORM (Object-Relational Mapping), è possibile usare Entity Framework. Per altre informazioni, vedere [Accesso ai dati](/windows/uwp/data-access/index) nel centro Windows developer.

Se ci si connette ai servizi di Azure, assicurarsi di scaricare gli strumenti più recenti [di Azure SDK.](https://azure.microsoft.com/downloads/)

### <a name="data-providers"></a>Provider di dati

Perché un database sia utilizzabile in ADO.NET, deve avere un provider di dati *ADO.NET* personalizzato oppure deve esporre un'interfaccia ODBC o OLE DB dati. Microsoft fornisce un [elenco di ADO.NET di](/dotnet/framework/data/adonet/ado-net-overview) dati per i SQL Server, nonché i provider ODBC OLE DB.

### <a name="data-modeling"></a>Modellazione dati

In .NET sono disponibili tre opzioni per la modellazione e la modifica dei dati in memoria dopo che sono stati recuperati da un'origine dati:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Tecnologia ORM Microsoft preferita. È possibile usarlo per programmare dati relazionali come oggetti .NET di prima classe. Per le nuove applicazioni, deve essere la prima scelta predefinita quando è necessario un modello. Richiede il supporto personalizzato dal provider ADO.NET sottostante.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Mapper relazionale a oggetti di generazione precedente. Funziona bene per scenari meno complessi, ma non è più in fase di sviluppo attivo.

[Set di dati](../data-tools/dataset-tools-in-visual-studio.md) La meno recente delle tre tecnologie di modellazione. È progettato principalmente per lo sviluppo rapido di applicazioni "form over data" in cui non si elaborano grandi quantità di dati o non si eseguono query o trasformazioni complesse. Un oggetto DataSet è costituito da oggetti DataTable e DataRow che sono logicamente SQL oggetti di database molto più degli oggetti .NET. Per le applicazioni relativamente semplici basate SQL origini dati, i set di dati potrebbero essere ancora una scelta ottimale.

Non è necessario usare nessuna di queste tecnologie. In alcuni scenari, soprattutto in cui le prestazioni sono critiche, è possibile usare semplicemente un oggetto DataReader per leggere dal database e copiare i valori necessari in un oggetto raccolta, ad esempio List \<T> .

## <a name="native-c"></a>C++ nativo

Le applicazioni C++ che si connettono a SQL Server devono usare [Microsoft® ODBC Driver 13.1 per](https://www.microsoft.com/download/details.aspx?id=53339) SQL Server nella maggior parte dei casi. Se i server sono collegati, OLE DB necessario e per questo si usa il SQL Server Native Client [.](/sql/relational-databases/native-client/sql-server-native-client) È possibile accedere ad altri database usando [ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017&preserve-view=true) o OLE DB driver. ODBC è l'interfaccia di database standard corrente, ma la maggior parte dei sistemi di database fornisce funzionalità personalizzate a cui non è possibile accedere tramite l'interfaccia ODBC. OLE DB è una tecnologia legacy di accesso ai dati COM ancora supportata ma non consigliata per le nuove applicazioni. Per altre informazioni, vedere [Accesso ai dati in Visual C++](/cpp/data/data-access-in-cpp).

I programmi C++ che utilizzano servizi REST possono usare [l'SDK REST di C++.](https://github.com/Microsoft/cpprestsdk)

I programmi C++ che funzionano con Archiviazione di Microsoft Azure possono usare [il Archiviazione di Microsoft Azure Client](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

La modellazione &mdash; Visual Studio dati non fornisce un livello ORM per C++. [ODB](https://www.codesynthesis.com/products/odb/) è un orM open source diffuso per C++.

Per altre informazioni sulla connessione ai database da app C++, vedere Visual Studio [data tools per C++.](../data-tools/visual-studio-data-tools-for-cpp.md) Per altre informazioni sulle tecnologie di accesso ai Visual C++ legacy, vedere [Accesso ai dati](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript in Visual Studio](/scripting/javascript/javascript-language-reference) è un linguaggio di prima classe per la creazione di app multipiattaforma, app UWP, servizi cloud, siti Web e app Web. È possibile usare Bower, Grunt, Gulp, npm e NuGet dall'Visual Studio per installare le librerie JavaScript e i prodotti di database preferiti. Connessione in Archiviazione e servizi di Azure scaricando gli SDK dal sito [Web di Azure.](https://azure.microsoft.com/) Edge.js è una libreria che connette JavaScript (Node.js) lato server alle origini ADO.NET dati.

## <a name="python"></a>Python

Installare [il supporto python in Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) per creare applicazioni Python. La documentazione di Azure include diverse esercitazioni sulla connessione ai dati, tra cui:

- [Django e database SQL in Azure](/azure/app-service/app-service-web-get-started-python)
- [Django e MySQL in Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Usare [BLOB,](/azure/storage/blobs/storage-quickstart-blobs-python) [file,](/azure/storage/files/storage-python-how-to-use-file-storage) [code](/azure/storage/queues/storage-python-how-to-use-queue-storage)e [tabelle (Cosmo DB).](/azure/cosmos-db/table-storage-how-to-use-python)

## <a name="related-topics"></a>Argomenti correlati

[Piattaforma microsoft per intelligenza artificiale](https://azure.microsoft.com/overview/ai-platform/?v=17.42w) &mdash; Fornisce un'introduzione al cloud intelligente Microsoft, tra cui Cortana Analytics Suite e il supporto per Internet delle cose.

[Archiviazione di Microsoft Azure](/azure/storage/) &mdash; Descrive Archiviazione di Azure e come creare applicazioni usando BLOB, tabelle, code e file di Azure.

[database SQL di Azure](/azure/sql-database/) &mdash; Viene descritto come connettersi a database SQL di Azure, un database relazionale come servizio.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash; Vengono descritti gli strumenti che semplificano la progettazione, l'esplorazione, il test e la distribuzione di database e applicazioni connesse ai dati.

[ADO.NET](/dotnet/framework/data/adonet/index) &mdash; Descrive l'architettura ADO.NET e come usare le classi ADO.NET per gestire i dati dell'applicazione e interagire con origini dati e XML.

[ADO.NET Entity Framework](/ef/ef6/) &mdash; Viene descritto come creare applicazioni dati che consentono agli sviluppatori di programmare in base a un modello concettuale anziché direttamente su un database relazionale.

[WCF Data Services 4.5](/dotnet/framework/data/wcf/index) &mdash; Viene descritto come usare per distribuire servizi dati sul Web o in una intranet che [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] implementa l'Open Data Protocol [(OData).](https://www.odata.org/)

[Dati nelle soluzioni Office dati](../vsto/data-in-office-solutions.md) &mdash; Contiene collegamenti ad argomenti che illustrano il funzionamento dei dati Office soluzioni. Sono incluse informazioni sulla programmazione orientata allo schema, sulla memorizzazione nella cache dei dati e sull'accesso ai dati sul lato server.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) &mdash; Vengono descritte le funzionalità di query incorporate in C# e Visual Basic e il modello comune per l'esecuzione di query su database relazionali, documenti XML, set di dati e raccolte in memoria.

[Strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) &mdash; Illustra l'uso dei dati XML, il debug di XSLT, le funzionalità XML .NET e l'architettura di XML Query.

[Documenti e dati XML](/dotnet/standard/data/xml/index) &mdash; Fornisce una panoramica di un set completo e integrato di classi che funzionano con documenti e dati XML in .NET.