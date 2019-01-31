---
title: Aggiungere il codice nei set di dati di applicazioni a più livelli
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: e2d29f594615796cf320167b4e037eca48d1546d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024449"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Aggiungere il codice nei set di dati di applicazioni a più livelli
È possibile estendere le funzionalità di un set di dati creando un file di classe parziale per il set di dati e aggiungendovi il codice (invece di aggiungere codice per il *DatasetName*. File di DataSet). Classi parziali consentono al codice per una classe specifica da dividere tra più file fisici. Per altre informazioni, vedere [parziali](/dotnet/visual-basic/language-reference/modifiers/partial) oppure [classi e metodi parziali](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

Il codice che definisce un set di dati viene generato ogni volta che vengono apportate modifiche alla definizione del set di dati (nel set di dati tipizzato). Questo codice viene generato anche quando si apportano modifiche durante l'esecuzione di una procedura guidata che consente di modificare la configurazione di un set di dati. Per evitare che il codice in corso l'eliminazione durante la rigenerazione di un set di dati, aggiungere codice al file di classe parziale del set di dati.

Per impostazione predefinita, dopo aver separato il dataset e TableAdapter codice, il risultato è un file di classe discreti in ogni progetto. Il progetto originale include un file denominato *NomeDataset.Designer.vb* (o *NomeDataset.Designer.cs*) che contiene il codice oggetto TableAdapter. Il progetto che è designato nel **DataSetProject** proprietà dispone di un file denominato *NomeDataset* (o *NomeDataset*) . Questo file contiene il codice del dataset.

> [!NOTE]
>  Quando si separano i DataSet e TableAdapter (impostando il **DataSetProject** proprietà), sarà spostate automaticamente classi parziali del dataset presenti nel progetto. Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.

> [!NOTE]
>  Quando il codice di convalida deve essere aggiunto, il dataset tipizzato fornisce la funzionalità per la generazione <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> gestori eventi. Per altre informazioni, vedere [aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Per aggiungere codice al set di dati in applicazioni a più livelli

1.  Individuare il progetto che contiene il *XSD* file.

2.  Selezionare il **XSD** file per aprire il set di dati.

3.  Pulsante destro del mouse la tabella di dati a cui si desidera aggiungere il codice (il nome della tabella nella barra del titolo) e quindi selezionare **Visualizza codice**.

     Una classe parziale viene creata e aperto nell'Editor di codice.

4.  Aggiungere codice all'interno della dichiarazione di classe parziale.

     Nell'esempio seguente mostra dove aggiungere il codice in CustomersDataTable NorthwindDataSet:

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

## <a name="see-also"></a>Vedere anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Aggiungere il codice nei TableAdapter di applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Creare e configurare oggetti TableAdapter](create-and-configure-tableadapters.md)
- [Panoramica dell'aggiornamento gerarchico](hierarchical-update.md)
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)