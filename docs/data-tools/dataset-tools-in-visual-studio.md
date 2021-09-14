---
title: Strumenti di set di dati
description: Esaminare gli strumenti del set di dati disponibili in Visual Studio. Informazioni sul flusso di lavoro del set di dati, sui set di dati e sull'architettura a più livelli, sui set di dati e su XML.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1e021a8ab30829aedd0a695a53993998e312ff81
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631422"
---
# <a name="dataset-tools-in-visual-studio"></a>Strumenti di set di dati in Visual Studio

> [!NOTE]
> I set di dati e le classi correlate sono tecnologie .NET legacy dei primi anni 2000 che consentono alle applicazioni di usare i dati in memoria mentre le applicazioni vengono disconnesse dal database. Sono particolarmente utili per le applicazioni che consentono agli utenti di modificare i dati e rendere persistenti le modifiche nel database. Anche se i set di dati si sono dimostrati una tecnologia di grande successo, è consigliabile che le nuove applicazioni .NET usino Entity Framework. Entity Framework un modo più naturale per usare i dati tabulari come modelli a oggetti e offre un'interfaccia di programmazione più semplice.

Un `DataSet` oggetto è un oggetto in memoria che è essenzialmente un mini-database. Contiene oggetti , e in cui è possibile archiviare e modificare i dati di uno o più database senza dover `DataTable` `DataColumn` mantenere una connessione `DataRow` aperta. Il set di dati mantiene le informazioni sulle modifiche ai dati, in modo che gli aggiornamenti possano essere monitorati e inviati di nuovo al database quando l'applicazione viene riconnessa.

I set di dati e le classi correlate sono definiti nello spazio <xref:System.Data?displayProperty=fullName> dei nomi nell'API .NET. È possibile creare e modificare i set di dati in modo dinamico nel codice usando ADO.NET. La documentazione in questa sezione illustra come usare i set di dati usando Visual Studio finestre di progettazione. I set di dati creati tramite le finestre di progettazione usano **oggetti TableAdapter** per interagire con il database. I set di dati creati a livello di codice usano **oggetti DataAdapter.** Per informazioni sulla creazione di set di dati a livello di codice, vedere [DataAdapter e DataReader .](/dotnet/framework/data/adonet/dataadapters-and-datareaders)

Se l'applicazione deve solo leggere i dati da un database e non eseguire aggiornamenti, aggiunte o eliminazioni, è in genere possibile ottenere prestazioni migliori usando un oggetto per recuperare i dati in un oggetto generico o in un altro oggetto `DataReader` `List` raccolta. Se si visualizzano i dati, è possibile associare l'interfaccia utente alla raccolta.

## <a name="dataset-workflow"></a>Flusso di lavoro del set di dati

Visual Studio strumenti per semplificare l'uso dei set di dati. Il flusso di lavoro end-to-end di base è:

- Usare la [finestra Origini dati per](add-new-data-sources.md#data-sources-window) creare un nuovo set di dati da una o più origini dati. Usare il **Progettazione DataSet** per configurare il set di dati e impostarne le proprietà. Ad esempio, è necessario specificare le tabelle dell'origine dati da includere e le colonne di ogni tabella. Scegliere con attenzione per risparmiare la quantità di memoria necessaria per il set di dati. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).

- Specificare le relazioni tra le tabelle in modo che le chiavi esterne vengano gestite correttamente. Per altre informazioni, vedere [Riempire i set di dati tramite TableAdapter.](../data-tools/fill-datasets-by-using-tableadapters.md)

- Usare la **Configurazione guidata TableAdapter** per specificare la query o il stored procedure che popola il set di dati e le operazioni di database (aggiornamento, eliminazione e così via) da implementare. Per altre informazioni, vedere gli argomenti seguenti:

  - [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Modifica di dati nei set di dati](../data-tools/edit-data-in-datasets.md)

  - [Convalidare i dati nei set di dati](../data-tools/validate-data-in-datasets.md)

  - [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)

- Eseguire query e cercare i dati nel set di dati. Per altre informazioni, vedere [Eseguire query sui set di dati](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] abilita [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) sui dati in un <xref:System.Data.DataSet> oggetto . Per altre informazioni, vedere [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

- Usare la **finestra Origini dati** per associare i controlli dell'interfaccia utente al set di dati o alle singole colonne e per specificare le colonne modificabili dall'utente. Per altre informazioni, vedere [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Set di dati e architettura a più livelli

Per informazioni sui set di dati nelle applicazioni a più livelli, vedere Usare i set di [dati in applicazioni a più livelli.](../data-tools/work-with-datasets-in-n-tier-applications.md)

## <a name="datasets-and-xml"></a>Set di dati e XML

Per informazioni sulla conversione di set di dati da e verso XML, vedere Leggere dati [XML in](../data-tools/read-xml-data-into-a-dataset.md) un set di dati e Salvare un set di dati [come XML.](../data-tools/save-a-dataset-as-xml.md)

## <a name="see-also"></a>Vedi anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
