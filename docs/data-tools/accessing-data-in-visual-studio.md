---
title: Strumenti e accesso ai dati
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3a53561e8c62fcf523f13d17d5228d33a6a0af6d
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916724"
---
# <a name="access-data-in-visual-studio"></a>Accedere ai dati in Visual Studio

In Visual Studio è possibile creare applicazioni che si connettono ai dati praticamente in qualsiasi prodotto o servizio del database, in qualsiasi formato, in qualsiasi posizione, in un computer locale, in una rete locale o in un cloud pubblico, privato o ibrido.

Per le applicazioni in JavaScript, Python, PHP, Ruby o C++, è possibile connettersi ai dati, come per qualsiasi altra operazione, ottenendo le librerie e scrivendo il codice. Per le applicazioni .NET, Visual Studio fornisce strumenti che è possibile usare per esplorare le origini dati, creare modelli a oggetti per archiviare e modificare i dati in memoria e associare dati all'interfaccia utente. Microsoft Azure offre SDK per .NET, Java, node. js, PHP, Python, Ruby e app per dispositivi mobili e strumenti in Visual Studio per la connessione ad archiviazione di Azure.

Negli elenchi seguenti vengono illustrati solo alcuni dei numerosi sistemi di database e di archiviazione che possono essere utilizzati da Visual Studio. Le offerte di [Microsoft Azure](https://azure.microsoft.com/) sono servizi dati che includono tutto il provisioning e l'amministrazione dell'archivio dati sottostante. Il carico di lavoro di **sviluppo di Azure** in [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) consente di usare gli archivi dati di Azure direttamente da Visual Studio.

![Carico di lavoro Sviluppo di Azure](media/azure-development-workload.png)

La maggior parte degli altri prodotti di database SQL e NoSQL elencati qui può essere ospitata in un computer locale, in una rete locale o in Microsoft Azure in una macchina virtuale. Se si ospita il database in una macchina virtuale Microsoft Azure, si è responsabili della gestione del database stesso.

**Microsoft Azure**

- Database SQL
- Azure Cosmos DB
- Archiviazione (BLOB, tabelle, code, file)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- E molto altro ancora.

**SQL**

- SQL Server 2005-2016 (include Express e local DB)
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

::: moniker range="vs-2017"

Molti fornitori di database e terze parti supportano l'integrazione di Visual Studio da pacchetti NuGet. È possibile esplorare le offerte in nuget.org o tramite Gestione pacchetti NuGet in Visual Studio (**strumenti** > gestione pacchetti **NuGet** > **gestire i pacchetti NuGet per la soluzione**). Altri prodotti di database si integrano con Visual Studio come estensione. È possibile esplorare queste offerte nella [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o passare a **strumenti** > **estensioni e aggiornamenti** e quindi selezionare **online** nel riquadro sinistro della finestra di dialogo. Per ulteriori informazioni, vedere [sistemi di database compatibili per Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Molti fornitori di database e terze parti supportano l'integrazione di Visual Studio da pacchetti NuGet. È possibile esplorare le offerte in nuget.org o tramite Gestione pacchetti NuGet in Visual Studio (**strumenti** > gestione pacchetti **NuGet** > **gestire i pacchetti NuGet per la soluzione**). Altri prodotti di database si integrano con Visual Studio come estensione. È possibile esplorare queste offerte nella [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o passare a **estensioni** > **Gestisci estensioni** e quindi selezionare **online** nel riquadro sinistro della finestra di dialogo. Per ulteriori informazioni, vedere [sistemi di database compatibili per Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> Il supporto esteso per SQL Server 2005 è terminato il 12 aprile 2016. Non vi è alcuna garanzia che gli strumenti dati in Visual Studio 2015 e versioni successive continueranno a funzionare con SQL Server 2005. Per ulteriori informazioni, vedere l' [annuncio di fine del supporto tecnico per SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Linguaggi .NET

Tutti gli accessi ai dati .NET, incluso in .NET Core, sono basati su ADO.NET, un set di classi che definisce un'interfaccia per l'accesso a qualsiasi tipo di origine dati, sia relazionale che non relazionale. Visual Studio include diversi strumenti e finestre di progettazione che funzionano con ADO.NET per semplificare la connessione ai database, modificare i dati e presentare i dati all'utente. La documentazione in questa sezione descrive come usare questi strumenti. È anche possibile programmare direttamente con gli oggetti comando ADO.NET. Per ulteriori informazioni sulla chiamata diretta delle API ADO.NET, vedere [ADO.NET](/dotnet/framework/data/adonet/index).

Per la documentazione relativa all'accesso ai dati relativa a ASP.NET, vedere [uso dei dati](https://www.asp.net/web-forms/overview/presenting-and-managing-data) nel sito di ASP.NET. Per un'esercitazione sull'uso di Entity Framework con ASP.NET MVC, vedere [Introduzione con Entity Framework 6 Code First con MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Le app piattaforma UWP (Universal Windows Platform) (UWP) C# in o Visual Basic possono usare la Microsoft Azure SDK per .NET per accedere ad archiviazione di Azure e ad altri servizi di Azure. La classe Windows. Web. HttpClient consente la comunicazione con qualsiasi servizio RESTful. Per ulteriori informazioni, vedere [come connettersi a un server http utilizzando Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Per l'archiviazione dei dati nel computer locale, l'approccio consigliato consiste nell'usare SQLite, che viene eseguito nello stesso processo dell'app. Se è necessario un livello ORM (Object-Relational Mapping), è possibile usare Entity Framework. Per ulteriori informazioni, vedere [accesso ai dati](/windows/uwp/data-access/index) nel centro per sviluppatori Windows.

Se ci si connette ai servizi di Azure, assicurarsi di scaricare gli strumenti più recenti di [Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Provider di dati

Affinché un database sia utilizzabile in ADO.NET, è necessario che disponga di un *provider di dati ADO.NET* personalizzato. in caso contrario, deve esporre un'interfaccia ODBC o OLE DB. Microsoft fornisce un [elenco di provider di dati ADO.NET](/dotnet/framework/data/adonet/ado-net-overview) per i prodotti SQL Server, nonché per i provider ODBC e OLE DB.

### <a name="data-modeling"></a>Modellazione dei dati

In .NET sono disponibili tre opzioni per la modellazione e la modifica dei dati in memoria dopo che è stato recuperato da un'origine dati:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) La tecnologia Microsoft ORM preferita. È possibile usarlo per programmare in base ai dati relazionali come oggetti .NET di prima classe. Per le nuove applicazioni, deve essere la prima scelta predefinita quando è necessario un modello. Richiede il supporto personalizzato del provider ADO.NET sottostante.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Un mapper relazionale a oggetti di generazione precedente. Funziona bene per scenari meno complessi, ma non è più in fase di sviluppo attivo.

[Set di impostazioni](../data-tools/dataset-tools-in-visual-studio.md) Il meno recente delle tre tecnologie di modellazione. È progettato principalmente per lo sviluppo rapido di applicazioni "form su dati" in cui non si elaborano grandi quantità di dati o si eseguono query o trasformazioni complesse. Un oggetto DataSet è costituito da oggetti DataTable e DataRow che sono logicamente simili a oggetti di database SQL molto più di oggetti .NET. Per le applicazioni relativamente semplici basate sulle origini dati SQL, è possibile che i set di dati siano ancora una scelta ottimale.

Non è necessario usare nessuna di queste tecnologie. In alcuni scenari, soprattutto se le prestazioni sono fondamentali, è possibile usare semplicemente un oggetto DataReader per leggere dal database e copiare i valori necessari in un oggetto raccolta, ad esempio List\<T >.

## <a name="native-c"></a>C++ nativo

C++nella maggior parte dei casi, le applicazioni che si connettono a SQL Server devono utilizzare [Microsoft® ODBC Driver 13,1 per SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) . Se i server sono collegati, è necessario OLE DB e per usare il [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). È possibile accedere ad altri database usando direttamente i driver [ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) o OLE DB. ODBC è l'interfaccia di database standard corrente, ma la maggior parte dei sistemi di database fornisce funzionalità personalizzate a cui non è possibile accedere tramite l'interfaccia ODBC. OLE DB è una tecnologia di accesso ai dati COM legacy che è ancora supportata ma non consigliata per le nuove applicazioni. Per altre informazioni, vedere [accesso ai dati in C++Visual ](/cpp/data/data-access-in-cpp).

C++i programmi che utilizzano servizi REST possono usare l' [ C++ SDK Rest](https://github.com/Microsoft/cpprestsdk).

C++i programmi che funzionano con Archiviazione di Microsoft Azure possono usare il [client di archiviazione di Microsoft Azure](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

La modellazione dei dati&mdash;Visual Studio non fornisce un livello C++ORM per. [ODB](https://www.codesynthesis.com/products/odb/) è un noto ORM open source per C++.

Per altre informazioni sulla connessione a database da C++ app, vedere [Visual Studio Data Tools per C++ ](../data-tools/visual-studio-data-tools-for-cpp.md). Per ulteriori informazioni sulle tecnologie di C++ accesso ai dati visivi legacy, vedere [accesso ai dati](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript in Visual Studio](/scripting/javascript/javascript-language-reference) è un linguaggio di prima classe per la creazione di app multipiattaforma, app UWP, servizi cloud, siti Web e app Web. È possibile usare Bower, grugnire, Gulp, NPM e NuGet da Visual Studio per installare le librerie JavaScript e i prodotti di database preferiti. Connettersi ad archiviazione e servizi di Azure scaricando gli SDK dal [sito Web di Azure](https://azure.microsoft.com/). Edge. js è una libreria che connette JavaScript sul lato server (node. js) a origini dati ADO.NET.

## <a name="python"></a>Python

Installare il [supporto di Python in Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) per creare applicazioni Python. La documentazione di Azure include varie esercitazioni sulla connessione ai dati, inclusi i seguenti:

- [Django e database SQL in Azure](/azure/app-service/app-service-web-get-started-python)
- [Django e MySQL in Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Usare [BLOB](/azure/storage/blobs/storage-quickstart-blobs-python), [file](/azure/storage/files/storage-python-how-to-use-file-storage), [Code](/azure/storage/queues/storage-python-how-to-use-queue-storage)e [tabelle (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Argomenti correlati

[Microsoft ai platform](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;offre un'introduzione a Microsoft Intelligent cloud, tra cui Cortanana Analytics suite e il supporto per Internet delle cose.

[Archiviazione di Microsoft Azure](/azure/storage/)&mdash;descrive archiviazione di Azure e come creare applicazioni usando BLOB, tabelle, code e file di Azure.

Il [database SQL di azure](/azure/sql-database/)&mdash;descrive come connettersi al database SQL di Azure, un database relazionale come servizio.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;vengono descritti gli strumenti che semplificano la progettazione, l'esplorazione, il test e la distribuzione di applicazioni e database connessi ai dati.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;descrive l'architettura ADO.NET e come usare le classi ADO.NET per gestire i dati dell'applicazione e interagire con le origini dati e il codice XML.

[ADO.NET Entity Framework](/ef/ef6/)&mdash;viene descritto come creare applicazioni di dati che consentono agli sviluppatori di programmare in base a un modello concettuale anziché direttamente a un database relazionale.

[WCF Data Services 4,5](/dotnet/framework/data/wcf/index)&mdash;viene descritto come utilizzare [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] per distribuire servizi dati sul Web o in una rete Intranet che implementano il [Open Data Protocol (OData)](https://www.odata.org/).

[I dati nelle soluzioni office](../vsto/data-in-office-solutions.md)&mdash;contengono collegamenti ad argomenti che illustrano il funzionamento dei dati nelle soluzioni Office. Sono incluse informazioni sulla programmazione orientata agli schemi, sulla memorizzazione dei dati nella cache e sull'accesso ai dati sul lato server.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;descrive le funzionalità di query incorporate in C# e Visual Basic e il modello comune per l'esecuzione di query su database relazionali, documenti XML, set di dati e raccolte in memoria.

[Gli strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;illustrano l'utilizzo di dati XML, il debug di XSLT, le funzionalità XML .NET e l'architettura di XML query.

[Documenti e dati xml](/dotnet/standard/data/xml/index)&mdash;offre una panoramica di un set completo e integrato di classi che funzionano con documenti e dati XML in .NET.
