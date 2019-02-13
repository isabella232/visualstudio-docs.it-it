---
title: Aggiungere il codice nei TableAdapter di applicazioni a più livelli
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 75f7dd3149785520023657bb86ec8172dc379ab6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926996"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Aggiungere il codice nei TableAdapter di applicazioni a più livelli
È possibile estendere le funzionalità di un oggetto TableAdapter mediante la creazione di un file di classe parziale per i TableAdapter e aggiungendovi il codice (invece di aggiungere codice per il *DatasetName.DataSet.Designer* file). Classi parziali consentono al codice per una classe specifica da dividere tra più file fisici. Per altre informazioni, vedere [parziali](/dotnet/visual-basic/language-reference/modifiers/partial) oppure [parziale (tipo)](/dotnet/csharp/language-reference/keywords/partial-type).

Il codice che definisce un oggetto TableAdapter viene generato ogni volta che vengono apportate modifiche all'oggetto TableAdapter del set di dati. Questo codice viene generato anche quando vengono apportate modifiche durante l'esecuzione di una procedura guidata che consente di modificare la configurazione del TableAdapter. Per evitare che il codice in corso l'eliminazione durante la rigenerazione di un oggetto TableAdapter, aggiungere codice al file di classe parziale dell'oggetto TableAdapter.

Per impostazione predefinita, dopo aver separato il dataset e TableAdapter codice, il risultato è un file di classe discreti in ogni progetto. Il progetto originale include un file denominato *NomeDataset.Designer.vb* (o *NomeDataset.Designer.cs*) che contiene il codice oggetto TableAdapter. Il progetto che è designato nel **DataSetProject** proprietà ha un file denominato *NomeDataset* (o *NomeDataset*) che contiene il codice di set di dati.

> [!NOTE]
>  Quando si separano i dataset e gli oggetti TableAdapter (impostando la proprietà **Progetto DataSet**), le classi parziali del dataset presenti nel progetto non vengono spostate automaticamente. Le classi parziali del dataset devono essere spostate manualmente il progetto di set di dati.

> [!NOTE]
> Il set di dati fornisce la funzionalità per la generazione <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> gestori di eventi quando la convalida è necessaria. Per altre informazioni, vedere [aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Aggiungere il codice utente in un oggetto TableAdapter in un'applicazione a più livelli

1.  Individuare il progetto che contiene il *XSD* file.

2.  Fare doppio clic il *XSD* file per aprire il **Progettazione Dataset**.

3.  Fare doppio clic su oggetto TableAdapter che si desidera aggiungere il codice per e quindi selezionare **Visualizza codice**.

     Una classe parziale viene creata e aperto nell'Editor di codice.

4.  Aggiungere codice all'interno della dichiarazione di classe parziale.

5.  L'esempio seguente mostra dove aggiungere il codice per il `CustomersTableAdapter` nella `NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Vedere anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Aggiungere il codice nei set di dati di applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Creare e configurare oggetti TableAdapter](create-and-configure-tableadapters.md)
- [Panoramica dell'aggiornamento gerarchico](hierarchical-update.md)
