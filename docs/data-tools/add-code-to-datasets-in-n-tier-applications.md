---
title: Aggiungere codice nei set di dati di applicazioni a più livelli
description: Aggiungere codice ai set di dati nelle app a più livelli in Visual Studio. Creare un file di classe parziale per un set di dati e aggiungerne il codice (anziché a DatasetName.Dataset.Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending DataSets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7df5c2fd963ce628f146bde5b8df754866898b20
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631650"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Aggiungere codice nei set di dati di applicazioni a più livelli

È possibile estendere la funzionalità di un set di dati creando un file di classe parziale per il set di dati e aggiungendo al set di dati il codice anziché aggiungere codice a *DatasetName*. File Dataset.Designer). Le classi parziali consentono di dividere il codice per una classe specifica tra più file fisici. Per altre informazioni, vedere [Classi](/dotnet/visual-basic/language-reference/modifiers/partial) e [metodi parziali o parziali.](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)

Il codice che definisce un set di dati viene generato ogni volta che vengono apportate modifiche alla definizione del set di dati (nel set di dati tipizzato). Questo codice viene generato anche quando si apportano modifiche durante l'esecuzione di qualsiasi procedura guidata che modifica la configurazione di un set di dati. Per impedire l'eliminazione del codice durante la rigenerazione di un set di dati, aggiungere codice al file di classe parziale del set di dati.

Per impostazione predefinita, dopo aver separato il codice del set di dati e del TableAdapter, il risultato è un file di classe discreto in ogni progetto. Il progetto originale ha un file denominato *DatasetName.Designer.vb* (o *DatasetName.Designer.cs)* che contiene il codice TableAdapter. Il progetto designato nella proprietà **DataSet Project** contiene un file denominato *DatasetName.DataSet.Designer.vb* (o *DatasetName.DataSet.Designer.cs).* Questo file contiene il codice del set di dati.

> [!NOTE]
> Quando si separano DataSet e TableAdapter (impostando la proprietà **Project DataSet),** le classi di set di dati parziali esistenti nel progetto non verranno spostate automaticamente. Le classi parziali del set di dati esistenti devono essere spostate manualmente nel progetto di set di dati.

> [!NOTE]
> Quando è necessario aggiungere il codice di convalida, il set di dati tipizzato fornisce funzionalità per la generazione e <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> gestori eventi. Per altre informazioni, vedere [Aggiungere la convalida a un set di dati a più livelli.](../data-tools/add-validation-to-an-n-tier-dataset.md)

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Per aggiungere codice ai DataSet nelle applicazioni a più livelli

1. Individuare il progetto che contiene il file *xsd.*

2. Selezionare il file **xsd** per aprire il set di dati.

3. Fare clic con il pulsante destro del mouse sulla tabella dati a cui si vuole aggiungere il codice (il nome della tabella nella barra del titolo) e quindi scegliere **Visualizza codice**.

     Viene creata una classe parziale che viene aperta nell'editor di codice.

4. Aggiungere codice all'interno della dichiarazione di classe parziale.

     L'esempio seguente illustra dove aggiungere il codice a CustomersDataTable in NorthwindDataSet:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Vedi anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Aggiungere il codice nei TableAdapter di applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Creare e configurare oggetti TableAdapter](create-and-configure-tableadapters.md)
- [Panoramica dell'aggiornamento gerarchico](hierarchical-update.md)
- [Strumenti di DataSet in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
