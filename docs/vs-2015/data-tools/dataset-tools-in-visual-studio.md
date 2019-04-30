---
title: Strumenti di set di dati
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0dc80bd821a85c475adba7fbbc264ab6b5a76a9b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431134"
---
# <a name="dataset-tools-in-visual-studio"></a>Strumenti di set di dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> I set di dati e le classi correlate sono tecnologie .NET legacy dal degli anni 2000 anticipata che consentono alle applicazioni a funzionare con i dati in memoria mentre le applicazioni vengono disconnessi dal database. Sono particolarmente utili per le applicazioni che consentono agli utenti di modificare i dati e rendere permanenti le modifiche nel database. Anche se i set di dati hanno dimostrato di essere una tecnologia di grande successo, è consigliabile che le nuove applicazioni .NET usano Entity Framework. Entity Framework fornisce un modo più semplice per lavorare con dati tabulari come modelli a oggetti, e ha un'interfaccia di programmazione più semplice.

 Un oggetto set di dati è un oggetto in memoria che è fondamentalmente un mini-database. Contiene gli oggetti DataTable e DataColumn DataRow in cui è possibile archiviare e modificare i dati da uno o più database senza dover gestire una connessione aperta. Il set di dati mantiene le informazioni sulle modifiche apportate ai dati, in modo che gli aggiornamenti possono essere rilevati e inviati nuovamente al database quando l'applicazione verrà riconnessa.

 I set di dati e le classi correlate sono definite nello spazio dei nomi System. Data nella libreria di classi .NET Framework. È possibile creare e modificare i set di dati in modo dinamico nel codice. Per altre informazioni su come eseguire questa operazione, vedere ADO.NET. La documentazione in questa sezione viene illustrato come utilizzare i set di dati tramite le finestre di progettazione di Visual Studio. Una cosa da sapere: set di dati che vengono effettuate tramite le finestre di progettazione usano oggetti TableAdapter per interagire con il database, mentre i set di dati che vengono apportate a livello di codice usano gli oggetti DataAdapter. Per informazioni sulla creazione di set di dati a livello di codice, vedere [DataAdapter e DataReader](http://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

 Se l'applicazione deve solo leggere i dati da un database e non eseguire gli aggiornamenti, aggiunge o Elimina, è possibile ottenere prestazioni migliori in genere tramite un oggetto DataReader per recuperare dati in un oggetto List generico o un altro oggetto della raccolta. Se si visualizzano i dati, è possibile associare l'interfaccia utente alla raccolta.

## <a name="dataset-workflow"></a>Flusso di lavoro di set di dati
 Visual Studio fornisce numerosi strumenti per semplificare l'utilizzo di set di dati. Il flusso di lavoro end-to-end base è:

- Usare la **Zdroj dat** finestra per creare un nuovo set di dati da uno o più origini dati. Usare la **Progettazione Dataset** per configurare il set di dati e impostare le relative proprietà. Ad esempio, è necessario specificare quali tabelle dall'origine dati da includere e le colonne da ogni tabella. Scegliere con attenzione conservare la quantità di memoria che richiede il set di dati. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).

- Specificare le relazioni tra le tabelle in modo che le chiavi esterne vengono gestite correttamente. Per altre informazioni, vedere [compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).

- Usare la **configurazione guidata TableAdapter** per specificare la query o stored procedure in grado di popolare il set di dati e le operazioni di database (update, delete e così via) da implementare. Per altre informazioni, vedere gli argomenti seguenti:

    - [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

    - [Modificare i dati nei set di dati](../data-tools/edit-data-in-datasets.md)

    - [Convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md)

    - [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)

- Eseguire query e cercare i dati nel set di dati. Per altre informazioni, vedere [eseguire query sui set di dati](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] Abilita [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) sui dati in un <xref:System.Data.DataSet> oggetto. Per altre informazioni, vedere [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).

- Usare la **Zdroje dat** finestra consente di associare i controlli dell'interfaccia utente per il set di dati o le singole colonne e per specificare quali colonne sono modificabili dall'utente. Per altre informazioni, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Architettura a più livelli e i set di dati
 Per informazioni sui set di dati nelle applicazioni a più livelli, vedere [lavorare con i set di dati nelle applicazioni a n livelli](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Set di dati e XML
 Per informazioni sulla conversione dei set di dati da e verso XML, vedere [legge i dati XML in un set di dati](../data-tools/read-xml-data-into-a-dataset.md) e [Salva un set di dati come XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Vedere anche
 [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
