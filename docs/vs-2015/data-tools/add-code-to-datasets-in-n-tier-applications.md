---
title: Aggiungere codice a DataSet in applicazioni a più livelli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aed37ee9cdd8c221fcfb114db426a6286ee8ad6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673113"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Aggiungere il codice nei set di dati di applicazioni a più livelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per estendere la funzionalità di un set di dati, è possibile creare un file di classe parziale per il set di dati e aggiungervi codice, anziché aggiungere codice a *DataSetName*. File dataset. Designer). Le classi parziali consentono di dividere il codice per una classe specifica tra più file fisici. Per altre informazioni, vedere [classi e metodi](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1) [parziali](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) o parziali.

Il codice che definisce un set di dati viene generato ogni volta che vengono apportate modifiche alla definizione del set di dati. Questo codice viene generato anche quando si apportano modifiche durante l'esecuzione di una procedura guidata che modifica la configurazione di un set di dati. Per impedire l'eliminazione del codice durante la rigenerazione di un set di dati, aggiungere il codice al file di classe parziale del set di dati.

Per impostazione predefinita, dopo aver separato il set di dati e `TableAdapter` codice, il risultato è un file di classe discreto in ogni progetto. Il progetto originale ha un *set di dati*denominato. Designer. vb (o *DataSetName*. Designer.cs) che contiene il codice `TableAdapter`. Il progetto designato nella proprietà del **progetto DataSet** contiene un file denominato *DataSetName*. DataSet. designer. vb (o *DataSetName*. DataSet.Designer.cs). Questo file contiene il codice del set di dati.

> [!NOTE]
> Quando si separano i set di dati e si `TableAdapter`s (impostando la proprietà del **progetto DataSet** ), le classi del set di dati parziali esistenti nel progetto non verranno spostate automaticamente. Le classi parziali del set di dati esistenti devono essere spostate manualmente nel progetto DataSet.

> [!NOTE]
> Quando è necessario aggiungere il codice di convalida, Progettazione DataSet fornisce funzionalità per la generazione di gestori eventi <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging>. Per altre informazioni, vedere [aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="add-code-to-datasets-in-n-tier-applications"></a>Aggiungere il codice nei set di dati di applicazioni a più livelli

1. Individuare il progetto che contiene il file XSD (set di dati).

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

## <a name="see-also"></a>Vedere anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Aggiungere il codice nei TableAdapter di applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [Panoramica di TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [Panoramica dell'aggiornamento gerarchico](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)