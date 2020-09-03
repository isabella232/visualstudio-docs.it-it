---
title: Aggiungere la convalida a un set di dati a più livelli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b03f1e85140d62d84ae7c706a9bfee6a7c515abb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673046"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Aggiungere la convalida a un set di dati a più livelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'aggiunta della convalida a un set di dati separato in una soluzione a più livelli è fondamentalmente uguale all'aggiunta della convalida a un set di dati a file singolo (un set di dati in un singolo progetto). Il percorso suggerito per eseguire la convalida dei dati è durante gli <xref:System.Data.DataTable.ColumnChanging> eventi e/o <xref:System.Data.DataTable.RowChanging> di una tabella dati.

In Progettazione DataSet è disponibile la funzionalità per la creazione di classi parziali a cui è possibile aggiungere codice utente per gli eventi di modifica delle colonne e delle righe delle tabelle dati nel set di dati. Per altre informazioni sull'aggiunta di codice a un set di dati in una soluzione a più livelli, vedere [aggiungere codice ai set di dati in applicazioni](../data-tools/add-code-to-datasets-in-n-tier-applications.md)a più livelli e [aggiungere codice a TableAdapter in applicazioni](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)a più livelli. Per altre informazioni sulle classi parziali, vedere [procedura: suddividere una classe in classi parziali (Progettazione classi)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) o [classi e metodi parziali](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

> [!NOTE]
> Quando si separano i set di dati dagli oggetti TableAdapter (impostando la proprietà del **progetto DataSet** ), le classi del set di dati parziali esistenti nel progetto non verranno spostate automaticamente. Le classi parziali del set di dati esistenti devono essere spostate manualmente nel progetto DataSet.

> [!NOTE]
> Il Progettazione DataSet non crea automaticamente i gestori eventi in C# per gli <xref:System.Data.DataTable.ColumnChanging> eventi e <xref:System.Data.DataTable.RowChanging> . È necessario creare manualmente un gestore eventi e associare il gestore eventi all'evento sottostante. Nelle procedure seguenti viene descritto come creare i gestori eventi necessari sia in Visual Basic che in C#.

## <a name="validatechanges-to-individual-columns"></a>ValidateChanges a singole colonne
 Convalidare i valori nelle singole colonne gestendo l' <xref:System.Data.DataTable.ColumnChanging> evento. L' <xref:System.Data.DataTable.ColumnChanging> evento viene generato quando viene modificato un valore in una colonna. Creare un gestore eventi per l' <xref:System.Data.DataTable.ColumnChanging> evento facendo doppio clic sulla colonna desiderata nel set di dati.

 La prima volta che si fa doppio clic su una colonna, la finestra di progettazione genera un gestore eventi per l' <xref:System.Data.DataTable.ColumnChanging> evento. `If…Then`Viene inoltre creata un'istruzione che verifica la presenza di una colonna specifica. Il codice seguente, ad esempio, viene generato quando si fa doppio clic sulla colonna RequiredDate nella tabella Orders di Northwind:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> Nei progetti C#, il Progettazione DataSet crea solo classi parziali per il set di dati e singole tabelle nel set di dati. Il Progettazione DataSet non crea automaticamente i gestori eventi per gli <xref:System.Data.DataTable.ColumnChanging> eventi e <xref:System.Data.DataTable.RowChanging> in C#, come avviene in Visual Basic. Nei progetti C# è necessario costruire manualmente un metodo per gestire l'evento e associare il metodo all'evento sottostante. Nella procedura riportata di seguito vengono illustrati i passaggi per creare i gestori eventi necessari sia in Visual Basic che in C#.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Per aggiungere la convalida durante le modifiche apportate ai singoli valori di colonna

1. Aprire il set di dati nella finestra di progettazione facendo doppio clic sul file **xsd** in **Esplora soluzioni**. Per altre informazioni, vedere [procedura: aprire un set di dati nel Progettazione DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Fare doppio clic sulla colonna che si desidera convalidare. Questa azione crea il <xref:System.Data.DataTable.ColumnChanging> gestore eventi.

    > [!NOTE]
    > Il Progettazione DataSet non crea automaticamente un gestore eventi per l'evento C#. Il codice necessario per gestire l'evento in C# è incluso nella sezione successiva. `SampleColumnChangingEvent` viene creato e quindi associato all' <xref:System.Data.DataTable.ColumnChanging> evento nel <xref:System.Data.DataTable.EndInit%2A> metodo.

3. Aggiungere il codice per verificare che `e.ProposedValue` contenga i dati che soddisfano i requisiti dell'applicazione. Se il valore proposto non è accettabile, impostare la colonna per indicare che contiene un errore.

     Nell'esempio di codice seguente viene verificato che la colonna **Quantity** contiene più di 0. Se **Quantity** è minore o uguale a 0, la colonna viene impostata su un errore. La `Else` clausola cancella l'errore se la **quantità** è maggiore di 0. Il codice nel gestore eventi per la modifica delle colonne dovrebbe essere simile al seguente:

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
    // C#
    // Add this code to the DataTable
    // partial class.

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

## <a name="validatechanges-to-whole-rows"></a>ValidateChanges a intere righe
 Consente di convalidare i valori di intere righe gestendo l' <xref:System.Data.DataTable.RowChanging> evento. L' <xref:System.Data.DataTable.RowChanging> evento viene generato quando viene eseguito il commit dei valori di tutte le colonne. È necessario convalidare l' <xref:System.Data.DataTable.RowChanging> evento quando il valore di una colonna si basa sul valore di un'altra colonna. Si consideri, ad esempio, OrderDate e RequiredDate nella tabella Orders di Northwind.

 Quando si impostano gli ordini, la convalida verifica che non venga immesso un ordine con un RequiredDate che si trova in o prima di OrderDate. In questo esempio, è necessario confrontare i valori per entrambe le colonne RequiredDate e OrderDate, quindi la convalida di una singola modifica di colonna non ha senso.

 Creare un gestore eventi per l' <xref:System.Data.DataTable.RowChanging> evento facendo doppio clic sul nome della tabella nella barra del titolo della tabella.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Per aggiungere la convalida durante le modifiche apportate a intere righe

1. Aprire il set di dati nella finestra di progettazione facendo doppio clic sul file **xsd** in **Esplora soluzioni**. Per altre informazioni, vedere [procedura: aprire un set di dati nel Progettazione DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Fare doppio clic sulla barra del titolo della tabella dati nella finestra di progettazione.

     Una classe parziale viene creata con un `RowChanging` gestore eventi e viene aperta nell'editor di codice.

    > [!NOTE]
    > Il Progettazione DataSet non crea automaticamente un gestore eventi per l' <xref:System.Data.DataTable.RowChanging> evento nei progetti C#. È necessario creare un metodo per gestire l' <xref:System.Data.DataTable.RowChanging> evento ed eseguire il codice per associare l'evento nel metodo di inizializzazione della tabella.

3. Aggiungere il codice utente all'interno della dichiarazione di classe parziale.

4. Il codice seguente mostra dove aggiungere il codice utente da convalidare durante l' <xref:System.Data.DataTable.RowChanging> evento per Visual Basic:

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

5. Il codice seguente illustra come creare il `RowChanging` gestore eventi e dove aggiungere il codice utente da convalidare durante l' <xref:System.Data.DataTable.RowChanging> evento per C#:

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

## <a name="see-also"></a>Vedere anche
 [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md) [procedura dettagliata: creazione di un'applicazione dati](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [a più livelli convalida dei dati nei set di](../data-tools/validate-data-in-datasets.md) dati
