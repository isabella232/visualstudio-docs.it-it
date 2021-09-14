---
title: Errore di utilizzo di progetti separati
description: Informazioni su come separare i set di dati e gli oggetti TableAdapter in progetti diversi, in modo da poter separare rapidamente i livelli dell'applicazione e generare applicazioni dati a più livelli.
ms.date: 11/04/2016
ms.topic: how-to
ms.custom: SEO-VS-2020
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 335f6d1ab4a7dba28609a267e6a6ce950cb607ff
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631176"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Separare set di dati e TableAdapter in progetti diversi
I set di dati tipizzati sono stati migliorati in modo che le [classi TableAdapter e](create-and-configure-tableadapters.md) dataset possano essere generate in progetti separati. In questo modo è possibile separare rapidamente i livelli dell'applicazione e generare applicazioni dati a più livelli.

La procedura seguente descrive il  processo di utilizzo del Progettazione DataSet per generare il codice del set di dati in un progetto separato dal progetto che contiene il codice TableAdapter generato.

## <a name="separate-datasets-and-tableadapters"></a>Set di dati separati e oggetti TableAdapter
Quando si separa il codice del set di dati dal codice TableAdapter, il progetto che contiene il codice del set di dati deve trovarsi nella soluzione corrente. Se il progetto non si trova nella soluzione corrente,  non sarà disponibile nell'elenco Project set di dati nella **finestra** Proprietà.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Per separare il set di dati in un progetto diverso

1. Aprire una soluzione che contiene un set di dati (file *xsd).*

    > [!NOTE]
    > Se la soluzione non contiene il progetto in cui si vuole separare il codice del set di dati, creare il progetto o aggiungere un progetto esistente alla soluzione.

2. Fare doppio clic su un file di set di dati tipizzato (un file con estensione *xsd)* in **Esplora soluzioni** per aprire il set di **dati nel Progettazione DataSet**.

3. Selezionare un'area vuota del **Progettazione DataSet**.

4. Nella finestra **Proprietà** individuare il nodo **dataset Project** dati.

5. **Nell'elenco Project** dati selezionare il nome del progetto in cui si vuole generare il codice del set di dati.

     Dopo aver selezionato il progetto in cui si vuole generare il codice del set di dati, la proprietà **File dataSet** viene popolata con un nome file predefinito. Se necessario, è possibile modificare questo nome. Inoltre, se si vuole generare il codice del set di dati in una directory specifica, è possibile impostare la proprietà Project **Cartella** sul nome di una cartella.

    > [!NOTE]
    > Quando si separano i set di dati e gli oggetti TableAdapter (impostando la proprietà **Project DataSet),** le classi di set di dati parziali esistenti nel progetto non verranno spostate automaticamente. Le classi di set di dati parziali esistenti devono essere spostate manualmente nel progetto di set di dati.

6. Salvare il set di dati.

     Il codice del set di dati viene generato nel progetto selezionato nella proprietà **dataset Project** e il codice **TableAdapter** viene generato nel progetto corrente.

Per impostazione predefinita, dopo aver separato il set di dati e il codice TableAdapter, il risultato è un file di classe discreto in ogni progetto. Il progetto originale ha un file denominato *DatasetName.Designer.vb* (o *DatasetName.Designer.cs)* che contiene il codice TableAdapter. Il progetto designato nella proprietà **dataset Project** contiene un file denominato *DatasetName.DataSet.Designer.vb* (o *DatasetName.DataSet.Designer.cs)* che contiene il codice del set di dati.

> [!NOTE]
> Per visualizzare il file di classe generato, selezionare il set di dati o il progetto TableAdapter. Quindi, in **Esplora soluzioni** selezionare **Mostra tutti i file.**

## <a name="see-also"></a>Vedi anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)
