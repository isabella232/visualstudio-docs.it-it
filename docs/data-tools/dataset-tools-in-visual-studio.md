---
title: Strumenti di set di dati
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3796a9b7a1d37911601574e02c89e8ccebb684ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72642110"
---
# <a name="dataset-tools-in-visual-studio"></a>Strumenti di set di dati in Visual Studio

> [!NOTE]
> I set di dati e le classi correlate sono tecnologie .NET legacy dei primi 2000 che consentono alle applicazioni di utilizzare i dati in memoria mentre le applicazioni sono disconnesse dal database. Sono particolarmente utili per le applicazioni che consentono agli utenti di modificare i dati e salvare nuovamente le modifiche nel database. Sebbene i set di risultati abbiano dimostrato una tecnologia molto efficace, è consigliabile che le nuove applicazioni .NET usino Entity Framework. Entity Framework offre un metodo più naturale per lavorare con i dati tabulari come modelli a oggetti e dispone di un'interfaccia di programmazione più semplice.

Un oggetto `DataSet` è un oggetto in memoria che essenzialmente è un mini-database. Contiene gli oggetti `DataTable`, `DataColumn` e `DataRow` in cui è possibile archiviare e modificare i dati da uno o più database senza dover gestire una connessione aperta. Il set di dati mantiene le informazioni sulle modifiche apportate ai dati, quindi gli aggiornamenti possono essere rilevati e restituiti al database quando l'applicazione viene riconnessa.

I set di impostazioni e le classi correlate sono definiti nello spazio dei nomi <xref:System.Data?displayProperty=fullName> nell'API .NET. È possibile creare e modificare i set di impostazioni in modo dinamico nel codice usando ADO.NET. La documentazione in questa sezione illustra come usare i set di impostazioni usando le finestre di progettazione di Visual Studio. I set di dati creati mediante le finestre di progettazione utilizzano oggetti **TableAdapter** per interagire con il database. I set di impostazioni creati a livello di codice utilizzano oggetti **DataAdapter** . Per informazioni sulla creazione di set di dati a livello di codice, vedere [DataAdapters e DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

Se l'applicazione deve solo leggere dati da un database e non eseguire aggiornamenti, aggiunte o eliminazioni, in genere è possibile ottenere prestazioni migliori usando un oggetto `DataReader` per recuperare i dati in un oggetto generico `List` o in un altro oggetto Collection. Se si visualizzano i dati, è possibile associare i dati all'interfaccia utente alla raccolta.

## <a name="dataset-workflow"></a>Flusso di lavoro DataSet

Visual Studio offre strumenti per semplificare l'uso dei set di impostazioni. Il flusso di lavoro end-to-end di base è:

- Utilizzare la [finestra Origini dati](add-new-data-sources.md#data-sources-window) per creare un nuovo set di dati da una o più origini dati. Utilizzare il **Progettazione DataSet** per configurare il set di dati e impostare le relative proprietà. È ad esempio necessario specificare le tabelle dell'origine dati da includere e le colonne di ogni tabella. Scegliere con attenzione per conservare la quantità di memoria richiesta dal set di dati. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).

- Specificare le relazioni tra le tabelle in modo che le chiavi esterne vengano gestite correttamente. Per ulteriori informazioni, vedere [Fill DataSets by using TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

- Utilizzare la **Configurazione guidata TableAdapter** per specificare la query o stored procedure che popola il set di dati e le operazioni di database (Update, DELETE e così via) da implementare. Per altre informazioni, vedere gli argomenti seguenti:

  - [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Modificare i dati nei set di dati](../data-tools/edit-data-in-datasets.md)

  - [Convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md)

  - [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)

- Eseguire una query e cercare i dati nel set di dati. Per altre informazioni, vedere [query DataSets](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] Abilita [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) sui dati in un oggetto <xref:System.Data.DataSet>. Per altre informazioni, vedere [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

- Utilizzare la finestra **origini dati** per associare i controlli dell'interfaccia utente al set di dati o alle singole colonne e per specificare quali colonne sono modificabili dall'utente. Per altre informazioni, vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Set di impostazioni e architettura a più livelli

Per informazioni sui set di dati nelle applicazioni a più livelli, vedere usare i set di dati [nelle applicazioni a più livelli](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>DataSet e XML

Per informazioni sulla conversione di set di dati in e da XML, vedere [leggere i dati XML in un set di dati](../data-tools/read-xml-data-into-a-dataset.md) e [salvare un set di dati come XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
