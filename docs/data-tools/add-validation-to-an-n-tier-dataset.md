---
title: Aggiungere la convalida a un set di dati a più livelli
description: Aggiungere la convalida a un set di dati a più livelli in Visual Studio. Convalidare le modifiche a singole colonne o righe intere.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6d9774b45743b57941d08903375d29b663b64192
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631619"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Aggiungere la convalida a un set di dati a più livelli
L'aggiunta della convalida a un set di dati separato in una soluzione a più livelli è fondamentalmente uguale all'aggiunta della convalida a un set di dati a file singolo (un set di dati in un singolo progetto). La posizione suggerita per l'esecuzione della convalida dei dati è <xref:System.Data.DataTable.ColumnChanging> durante gli eventi e/o <xref:System.Data.DataTable.RowChanging> di una tabella dati.

Il set di dati fornisce la funzionalità per creare classi parziali a cui è possibile aggiungere codice utente agli eventi di modifica delle colonne e delle righe delle tabelle di dati nel set di dati. Per altre informazioni sull'aggiunta di codice a un set di dati in una soluzione a più livelli, vedere Aggiungere codice ai set di dati [in](../data-tools/add-code-to-datasets-in-n-tier-applications.md)applicazioni a più livelli e Aggiungere codice a TableAdapter in applicazioni [a più livelli.](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) Per altre informazioni sulle classi parziali, vedere [Procedura: Suddividere](../ide/class-designer/how-to-split-a-class-into-partial-classes.md) una classe in classi parziali (Progettazione classi) o [Classi e metodi parziali](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
> Quando si separano i set di dati dai TableAdapter (impostando la proprietà **Project DataSet),** le classi di set di dati parziali esistenti nel progetto non verranno spostate automaticamente. Le classi di set di dati parziali esistenti devono essere spostate manualmente nel progetto di set di dati.

> [!NOTE]
> Progettazione set di dati non crea automaticamente gestori eventi in C# per gli <xref:System.Data.DataTable.ColumnChanging> eventi e <xref:System.Data.DataTable.RowChanging> . È necessario creare manualmente un gestore eventi e associare il gestore eventi all'evento sottostante. Le procedure seguenti descrivono come creare i gestori eventi necessari sia in Visual Basic che in C#.

## <a name="validate-changes-to-individual-columns"></a>Convalidare le modifiche alle singole colonne
Convalidare i valori nelle singole colonne gestendo <xref:System.Data.DataTable.ColumnChanging> l'evento . L'evento viene generato quando viene modificato un <xref:System.Data.DataTable.ColumnChanging> valore in una colonna. Creare un gestore eventi per <xref:System.Data.DataTable.ColumnChanging> l'evento facendo doppio clic sulla colonna desiderata nel **Progettazione DataSet**.

La prima volta che si fa doppio clic su una colonna, la finestra di progettazione genera un gestore eventi per <xref:System.Data.DataTable.ColumnChanging> l'evento . Viene `If...Then` creata anche un'istruzione che verifica la colonna specifica. Ad esempio, il codice seguente viene generato quando si fa doppio clic **sulla colonna RequiredDate** nella tabella Northwind Orders:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> Nei progetti C# il Progettazione DataSet solo classi parziali per il set di dati e le singole tabelle nel set di dati. Il Progettazione DataSet crea automaticamente gestori eventi per gli eventi e in C# come <xref:System.Data.DataTable.ColumnChanging> in <xref:System.Data.DataTable.RowChanging> Visual Basic. Nei progetti C# è necessario costruire manualmente un metodo per gestire l'evento e associare il metodo all'evento sottostante. La procedura seguente illustra i passaggi per creare i gestori eventi necessari sia in Visual Basic che in C#.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Per aggiungere la convalida durante le modifiche ai singoli valori di colonna

1. Aprire il set di dati facendo doppio clic sul file *xsd* in **Esplora soluzioni**. Per altre informazioni, vedere [Procedura dettagliata: Creazione di un set di dati nel Progettazione DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Fare doppio clic sulla colonna da convalidare. Questa azione crea il <xref:System.Data.DataTable.ColumnChanging> gestore eventi.

    > [!NOTE]
    > Il Progettazione DataSet crea automaticamente un gestore eventi per l'evento C#. Il codice necessario per gestire l'evento in C# è incluso nella sezione successiva. `SampleColumnChangingEvent` viene creato e quindi collegato <xref:System.Data.DataTable.ColumnChanging> all'evento nel metodo <xref:System.Data.DataTable.EndInit%2A> .

3. Aggiungere il codice per verificare `e.ProposedValue` che contenga dati che soddisfano i requisiti dell'applicazione. Se il valore proposto non è accettabile, impostare la colonna per indicare che contiene un errore.

     Nell'esempio di codice seguente viene verificato che la **colonna Quantity** contenga un valore maggiore di 0. Se **Quantity** è minore o uguale a 0, la colonna viene impostata su un errore. La `Else` clausola cancella l'errore se **Quantity** è maggiore di 0. Il codice nel gestore eventi di modifica della colonna dovrebbe essere simile al seguente:

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```

    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>Convalidare le modifiche a intere righe
Convalidare i valori in intere righe gestendo <xref:System.Data.DataTable.RowChanging> l'evento . <xref:System.Data.DataTable.RowChanging>L'evento viene generato quando viene eseguito il commit dei valori in tutte le colonne. È necessario eseguire la convalida nell'evento quando il valore in una colonna si <xref:System.Data.DataTable.RowChanging> basa sul valore in un'altra colonna. Si considerino, ad esempio, OrderDate e RequiredDate nella tabella Orders di Northwind.

Quando gli ordini vengono immessi, la convalida verifica che un ordine non venga immesso con RequiredDate in o prima di OrderDate. In questo esempio, i valori per le colonne RequiredDate e OrderDate devono essere confrontati, quindi la convalida di una singola modifica di colonna non ha senso.

Creare un gestore eventi per l'evento facendo doppio clic sul nome della tabella nella barra del titolo della tabella <xref:System.Data.DataTable.RowChanging> **Progettazione DataSet**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Per aggiungere la convalida durante le modifiche a intere righe

1. Aprire il set di dati facendo doppio clic sul file *xsd* in **Esplora soluzioni**. Per altre informazioni, vedere [Procedura dettagliata: Creazione di un set di dati nel Progettazione DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Fare doppio clic sulla barra del titolo della tabella dati nella finestra di progettazione.

     Una classe parziale viene creata con un `RowChanging` gestore eventi e viene aperta nell'editor di codice.

    > [!NOTE]
    > Il Progettazione DataSet crea automaticamente un gestore eventi per <xref:System.Data.DataTable.RowChanging> l'evento nei progetti C#. È necessario creare un metodo per gestire l'evento ed eseguire il codice e quindi <xref:System.Data.DataTable.RowChanging> associare l'evento nel metodo di inizializzazione della tabella.

3. Aggiungere il codice utente all'interno della dichiarazione di classe parziale.

4. Il codice seguente illustra dove aggiungere il codice utente da convalidare durante <xref:System.Data.DataTable.RowChanging> l'evento . L'esempio C# include anche il codice per associare il metodo del gestore eventi `OrdersRowChanging` all'evento .

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```

    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>Vedi anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Convalidare i dati nei set di dati](../data-tools/validate-data-in-datasets.md)
