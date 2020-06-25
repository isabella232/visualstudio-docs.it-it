---
title: Aggiungere codice nei set di dati di applicazioni a più livelli
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a57a05ddb8317ea31b852ded369ad7ef69d40bd0
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283086"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Aggiungere codice nei set di dati di applicazioni a più livelli

Per estendere la funzionalità di un set di dati, è possibile creare un file di classe parziale per il set di dati e aggiungervi codice, anziché aggiungere codice a *DataSetName*. File dataset. Designer). Le classi parziali consentono di dividere il codice per una classe specifica tra più file fisici. Per altre informazioni, vedere [classi e metodi](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods) [parziali](/dotnet/visual-basic/language-reference/modifiers/partial) o parziali.

Il codice che definisce un set di dati viene generato ogni volta che vengono apportate modifiche alla definizione del set di dati (nel DataSet tipizzato). Questo codice viene generato anche quando si apportano modifiche durante l'esecuzione di una procedura guidata che modifica la configurazione di un set di dati. Per impedire l'eliminazione del codice durante la rigenerazione di un set di dati, aggiungere il codice al file di classe parziale del set di dati.

Per impostazione predefinita, dopo aver separato il set di dati e il codice TableAdapter, il risultato è un file di classe discreto in ogni progetto. Il progetto originale include un file denominato *DataSetName. designer. vb* (o *DataSetName.designer.cs*) che contiene il codice TableAdapter. Il progetto designato nella proprietà del **progetto DataSet** contiene un file denominato *DataSetname. DataSet. designer. vb* (o *DataSetName.DataSet.designer.cs*). Questo file contiene il codice del set di dati.

> [!NOTE]
> Quando si separano i set di dati e i TableAdapter (impostando la proprietà del **progetto DataSet** ), le classi del set di dati parziali esistenti nel progetto non verranno spostate automaticamente. Le classi parziali del set di dati esistenti devono essere spostate manualmente nel progetto DataSet.

> [!NOTE]
> Quando è necessario aggiungere il codice di convalida, il set di dati tipizzato fornisce funzionalità per la generazione <xref:System.Data.DataTable.ColumnChanging> e i <xref:System.Data.DataTable.RowChanging> gestori eventi. Per altre informazioni, vedere [aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Per aggiungere codice a DataSet in applicazioni a più livelli

1. Individuare il progetto che contiene il file *xsd* .

2. Selezionare il file con **estensione XSD** per aprire il set di dati.

3. Fare clic con il pulsante destro del mouse sulla tabella dati a cui si desidera aggiungere il codice (il nome della tabella nella barra del titolo), quindi scegliere **Visualizza codice**.

     Viene creata una classe parziale che viene aperta nell'editor di codice.

4. Aggiungere codice all'interno della dichiarazione di classe parziale.

     Nell'esempio seguente viene illustrato come aggiungere codice a CustomersDataTable nel NorthwindDataSet:

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
- [Strumenti per set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
