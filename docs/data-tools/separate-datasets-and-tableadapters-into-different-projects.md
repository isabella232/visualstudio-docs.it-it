---
title: Separare set di dati e TableAdapter in progetti diversi
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cb70705d29ad636329803656aeaa1a27ddf237d5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402761"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Separare set di dati e TableAdapter in progetti diversi
I dataset tipizzati sono stati migliorati in modo che il [TableAdapter](create-and-configure-tableadapters.md) e classi di set di dati possono essere generate in progetti separati. Ciò consente di separare i livelli applicazione rapidamente e generare applicazioni dati a più livelli.

La procedura seguente descrive il processo d'uso di **Progettazione Dataset** per generare codice del set di dati in un progetto separato dal progetto che contiene il codice generato TableAdapter.

## <a name="separate-datasets-and-tableadapters"></a>Set di dati separati e gli oggetti TableAdapter
Quando si separa il codice del dataset dal codice del TableAdapter, il progetto che contiene il codice del dataset debba trovarsi nella soluzione corrente. Se non si trova il progetto nella soluzione corrente, non sarà disponibile nel **DataSetProject** nell'elenco il **proprietà** finestra.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Per separare il set di dati in un progetto diverso

1. Aprire una soluzione che contiene un set di dati (*XSD* file).

    > [!NOTE]
    > Se la soluzione non contiene il progetto in cui si desidera separare il codice di set di dati, creare il progetto oppure aggiungere un progetto esistente alla soluzione.

2. Fare doppio clic su un file di set di dati tipizzato (un *XSD* file) nel **Esplora soluzioni** per aprire il set di dati nel **Progettazione Dataset**.

3. Selezionare un'area vuota del **Progettazione Dataset**.

4. Nel **delle proprietà** finestra, individuare il **DataSetProject** nodo.

5. Nel **DataSetProject** elencare, selezionare il nome del progetto in cui si desidera generare il codice del set di dati.

     Dopo aver selezionato il progetto in cui si desidera generare il codice del set di dati, il **DataSet File** proprietà viene popolata con un nome file predefinito. Se necessario, è possibile modificare questo nome. Inoltre, se si desidera generare il codice del set di dati in una directory specifica, è possibile impostare il **cartella del progetto** proprietà sul nome di una cartella.

    > [!NOTE]
    > Quando si separano i DataSet e TableAdapter (impostando il **DataSetProject** proprietà), sarà spostate automaticamente classi parziali del dataset presenti nel progetto. Le classi parziali del dataset devono essere spostate manualmente il progetto di set di dati.

6. Salvare il set di dati.

     Il codice di set di dati viene generato nel progetto selezionato nel **DataSetProject** proprietà e il **TableAdapter** codice viene generato nel progetto corrente.

Per impostazione predefinita, dopo aver separato il dataset e TableAdapter codice, il risultato è un file di classe discreti in ogni progetto. Il progetto originale include un file denominato *NomeDataset.Designer.vb* (o *NomeDataset.Designer.cs*) che contiene il codice oggetto TableAdapter. Il progetto che è designato nel **DataSetProject** proprietà ha un file denominato *NomeDataset* (o *NomeDataset*) che contiene il codice di set di dati.

> [!NOTE]
> Per visualizzare il file di classe generata, selezionare il set di dati o di un progetto di TableAdapter. Quindi, nella **Esplora soluzioni**, selezionare **Mostra tutti i file**.

## <a name="see-also"></a>Vedere anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)