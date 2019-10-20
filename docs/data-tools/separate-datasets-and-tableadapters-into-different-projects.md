---
title: Separare set di dati e TableAdapter in progetti diversi
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9198378c5acf492216e2bebaceb210073766ea23
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648181"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Separare set di dati e TableAdapter in progetti diversi
I DataSet tipizzati sono stati migliorati in modo che le classi [TableAdapters](create-and-configure-tableadapters.md) e DataSet possano essere generate in progetti distinti. Ciò consente di separare rapidamente i livelli dell'applicazione e generare applicazioni dati a più livelli.

Nella procedura riportata di seguito viene descritto il processo di utilizzo del **Progettazione DataSet** per generare il codice del set di dati in un progetto separato dal progetto che contiene il codice TableAdapter generato.

## <a name="separate-datasets-and-tableadapters"></a>Set di impostazioni e TableAdapter separati
Quando si separa il codice del set di dati dal codice TableAdapter, il progetto che contiene il codice del set di dati deve trovarsi nella soluzione corrente. Se il progetto non si trova nella soluzione corrente, non sarà disponibile nell'elenco **progetto DataSet** nella finestra **Proprietà** .

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Per separare il set di dati in un progetto diverso

1. Aprire una soluzione contenente un set di dati (file*xsd* ).

    > [!NOTE]
    > Se la soluzione non contiene il progetto in cui si desidera separare il codice del set di dati, creare il progetto o aggiungere un progetto esistente alla soluzione.

2. Fare doppio clic su un file di set di dati tipizzato (un file con *estensione XSD* ) in **Esplora soluzioni** per aprire il set di dati nel **Progettazione DataSet**.

3. Selezionare un'area vuota del **Progettazione DataSet**.

4. Nella finestra **Proprietà** individuare il nodo del **progetto DataSet** .

5. Nell'elenco **progetto DataSet** selezionare il nome del progetto in cui si desidera generare il codice del set di dati.

     Dopo aver selezionato il progetto in cui si desidera generare il codice del set di dati, la proprietà **file del set di dati** viene popolata con un nome di file predefinito. Se necessario, è possibile modificare questo nome. Inoltre, se si desidera generare il codice del set di dati in una directory specifica, è possibile impostare la proprietà **cartella di progetto** sul nome di una cartella.

    > [!NOTE]
    > Quando si separano i set di dati e i TableAdapter (impostando la proprietà del **progetto DataSet** ), le classi del set di dati parziali esistenti nel progetto non verranno spostate automaticamente. Le classi di set di dati parziali esistenti devono essere spostate manualmente nel progetto DataSet.

6. Salvare il set di dati.

     Il codice del set di dati viene generato nel progetto selezionato nella proprietà del **progetto DataSet** e il codice **TableAdapter** viene generato nel progetto corrente.

Per impostazione predefinita, dopo aver separato il set di dati e il codice TableAdapter, il risultato è un file di classe discreto in ogni progetto. Il progetto originale include un file denominato *DataSetName. designer. vb* (o *DataSetName.designer.cs*) che contiene il codice TableAdapter. Il progetto designato nella proprietà del **progetto DataSet** include un file denominato *DataSetname. DataSet. designer. vb* (o *DataSetName.DataSet.designer.cs*) che contiene il codice del set di dati.

> [!NOTE]
> Per visualizzare il file di classe generato, selezionare il set di dati o il progetto TableAdapter. Quindi, in **Esplora soluzioni**, selezionare **Mostra tutti i file**.

## <a name="see-also"></a>Vedere anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)