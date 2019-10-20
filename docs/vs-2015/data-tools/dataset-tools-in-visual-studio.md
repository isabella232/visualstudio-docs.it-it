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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23e4deba53288383a569f6da6e14d27f723825ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657378"
---
# <a name="dataset-tools-in-visual-studio"></a>Strumenti di set di dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> I set di dati e le classi correlate sono tecnologie .NET legacy dei primi 2000 che consentono alle applicazioni di utilizzare i dati in memoria mentre le applicazioni sono disconnesse dal database. Sono particolarmente utili per le applicazioni che consentono agli utenti di modificare i dati e salvare nuovamente le modifiche nel database. Sebbene i set di risultati abbiano dimostrato una tecnologia molto efficace, è consigliabile che le nuove applicazioni .NET usino Entity Framework. Entity Framework offre un metodo più naturale per lavorare con i dati tabulari come modelli a oggetti e dispone di un'interfaccia di programmazione più semplice.

 Un oggetto DataSet è un oggetto in memoria che essenzialmente è un mini-database. Contiene oggetti DataTable, DataColumn e DataRow in cui è possibile archiviare e modificare i dati da uno o più database senza dover gestire una connessione aperta. Il set di dati mantiene le informazioni sulle modifiche apportate ai dati, quindi gli aggiornamenti possono essere rilevati e restituiti al database quando l'applicazione viene riconnessa.

 I set di dati e le classi correlate sono definiti nello spazio dei nomi System. Data nella libreria di classi .NET Framework. È possibile creare e modificare i set di impostazioni in modo dinamico nel codice. Per ulteriori informazioni su come eseguire questa operazione, vedere ADO.NET. La documentazione in questa sezione illustra come usare i set di impostazioni usando le finestre di progettazione di Visual Studio. Un aspetto da tenere presente: i set di dati eseguiti tramite le finestre di progettazione utilizzano oggetti TableAdapter per interagire con il database, mentre i set di dati creati a livello di codice utilizzano oggetti DataAdapter. Per informazioni sulla creazione di set di dati a livello di codice, vedere [DataAdapters e DataReaders](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

 Se l'applicazione deve solo leggere dati da un database e non eseguire aggiornamenti, aggiunte o eliminazioni, in genere è possibile ottenere prestazioni migliori usando un oggetto DataReader per recuperare i dati in un oggetto elenco generico o in un altro oggetto Collection. Se si visualizzano i dati, è possibile associare i dati all'interfaccia utente alla raccolta.

## <a name="dataset-workflow"></a>Flusso di lavoro DataSet
 In Visual Studio sono disponibili numerosi strumenti per semplificare l'utilizzo dei set di impostazioni. Il flusso di lavoro end-to-end di base è:

- Utilizzare la finestra **origine dati** per creare un nuovo set di dati da una o più origini dati. Utilizzare il **Progettazione DataSet** per configurare il set di dati e impostare le relative proprietà. È ad esempio necessario specificare le tabelle dell'origine dati da includere e le colonne di ogni tabella. Scegliere con attenzione per conservare la quantità di memoria necessaria per il set di dati. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).

- Specificare le relazioni tra le tabelle in modo che le chiavi esterne vengano gestite correttamente. Per ulteriori informazioni, vedere [Fill DataSets by using TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

- Utilizzare la **Configurazione guidata TableAdapter** per specificare la query o la stored procedure che compilerà il set di dati e le operazioni di database (Update, DELETE e così via) da implementare. Per altre informazioni, vedere gli argomenti seguenti:

  - [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Modificare i dati nei set di dati](../data-tools/edit-data-in-datasets.md)

  - [Convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md)

  - [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)

- Eseguire una query e cercare i dati nel set di dati. Per altre informazioni, vedere [query DataSets](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] Abilita [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) sui dati in un oggetto <xref:System.Data.DataSet>. Per altre informazioni, vedere [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).

- Utilizzare la finestra **origini dati** per associare i controlli dell'interfaccia utente al set di dati o alle singole colonne e per specificare quali colonne sono modificabili dall'utente. Per altre informazioni, vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Set di impostazioni e architettura a più livelli
 Per informazioni sui set di dati nelle applicazioni a più livelli, vedere usare i set di dati [nelle applicazioni a più livelli](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>DataSet e XML
 Per informazioni sulla conversione di set di dati in e da XML, vedere [leggere i dati XML in un set di dati](../data-tools/read-xml-data-into-a-dataset.md) e [salvare un set di dati come XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Vedere anche
 [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
