---
title: Aggiungere la convalida a un set di dati a più livelli
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 81d929aaffb6f08e5e1cda1cf3329de81fe13bc8
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38778061"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Aggiungere la convalida a un set di dati a più livelli
Aggiunta della convalida a un set di dati è suddivisa in una soluzione a più livelli è essenzialmente uguale all'aggiunta di convalida a un singolo file dataset (un set di dati in un unico progetto). Il percorso suggerito per eseguire la convalida dei dati è durante la <xref:System.Data.DataTable.ColumnChanging> e/o <xref:System.Data.DataTable.RowChanging> gli eventi di una tabella dati.

 Il set di dati fornisce la funzionalità per creare classi parziali a cui è possibile aggiungere il codice utente per gli eventi di modifica delle colonne e righe delle tabelle di dati nel set di dati. Per altre informazioni sull'aggiunta di codice a un set di dati in una soluzione a più livelli, vedere [aggiungere codice al set di dati in applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md), e [aggiungere codice agli oggetti TableAdapter in applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Per altre informazioni sulle classi parziali, vedere [procedura: dividere una classe in classi parziali (Progettazione classi)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) oppure [classi e metodi parziali](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
>  Quando si separano i set di dati da oggetti TableAdapter (impostando il **DataSetProject** proprietà), sarà spostate automaticamente classi parziali del dataset presenti nel progetto. Le classi parziali del dataset devono essere spostate manualmente il progetto di set di dati.

> [!NOTE]
>  Finestra di progettazione del set di dati non crea automaticamente i gestori eventi in c# per il <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> eventi. È necessario creare un gestore dell'evento manualmente e associare il gestore eventi all'evento sottostante. Le procedure seguenti descrivono come creare i gestori eventi necessaria in Visual Basic e c#.

## <a name="validate-changes-to-individual-columns"></a>Convalidare le modifiche alle singole colonne
 Convalidare i valori delle singole colonne gestendo il <xref:System.Data.DataTable.ColumnChanging> evento. Il <xref:System.Data.DataTable.ColumnChanging> evento viene generato quando viene modificato un valore in una colonna. Creare un gestore eventi per il <xref:System.Data.DataTable.ColumnChanging> eventi facendo doppio clic la colonna desiderata nel **Progettazione Dataset**.

 La prima volta che si fa doppio clic su una colonna, la finestra di progettazione genera un gestore eventi per il <xref:System.Data.DataTable.ColumnChanging> evento. Un `If...Then` istruzione viene creata anche che i test per la colonna specifica. Ad esempio, il codice seguente viene generato quando si fa doppio clic il **RequiredDate** colonna nella tabella Orders di Northwind:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
>  Nei progetti c#, la finestra di progettazione set di dati crea solo le classi parziali per il set di dati e le singole tabelle nel set di dati. La finestra di progettazione set di dati non crea automaticamente i gestori eventi per il <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> eventi in c# come avviene in Visual Basic. Nei progetti c#, è necessario creare manualmente un metodo per gestire l'evento e associare il metodo dell'evento sottostante. La seguente procedura fornisce i passaggi per creare i gestori eventi necessaria in Visual Basic e c#.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Per aggiungere la convalida durante le modifiche ai valori di colonna singola

1.  Aprire il set di dati facendo doppio clic il *XSD* del file in **Esplora soluzioni**. Per altre informazioni, vedere [procedura dettagliata: creazione di un set di dati in Progettazione Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Fare doppio clic sulla colonna da convalidare. Questa azione viene creata la <xref:System.Data.DataTable.ColumnChanging> gestore dell'evento.

    > [!NOTE]
    >  La finestra di progettazione set di dati non crea automaticamente un gestore eventi per l'evento di c#. Il codice che è necessario gestire l'evento nel linguaggio c# è incluso nella sezione successiva. `SampleColumnChangingEvent` viene creato e quindi collegato al <xref:System.Data.DataTable.ColumnChanging> eventi nel <xref:System.Data.DataTable.EndInit%2A> (metodo).

3.  Aggiungere il codice per verificare che `e.ProposedValue` contiene dati che soddisfano i requisiti dell'applicazione. Se il valore proposto è inaccettabile, impostare la colonna a indicare che contiene un errore.

     Esempio di codice seguente consente di verificare che il **Quantity** colonna contiene un valore maggiore di 0. Se **Quantity** è minore o uguale a 0, la colonna è impostata su un errore. Il `Else` clausola risolve il problema se **Quantity** è maggiore di 0. Il codice nel gestore dell'evento di modifica delle colonne sarà simile al seguente:

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

## <a name="validate-changes-to-whole-rows"></a>Convalidare le modifiche alle intere righe
 Convalidare i valori nelle righe intere gestendo il <xref:System.Data.DataTable.RowChanging> evento. Il <xref:System.Data.DataTable.RowChanging> evento viene generato quando vengono applicati i valori in tutte le colonne. È necessario convalidare il <xref:System.Data.DataTable.RowChanging> evento quando il valore in una colonna si basa sul valore in un'altra colonna. Si consideri ad esempio OrderDate e RequiredDate nel tabella Orders nel database Northwind.

 Quando avviene l'immissione degli ordini, la convalida assicura che un ordine non viene immesso con una colonna RequiredDate che o prima OrderDate. In questo esempio, i valori per le colonne OrderDate sia RequiredDate necessario confrontare, in modo che la convalida di una singola modifica di colonna non ha senso.

 Creare un gestore eventi per il <xref:System.Data.DataTable.RowChanging> eventi facendo doppio clic sul nome della tabella nella barra del titolo della tabella nel **Progettazione Dataset**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Per aggiungere la convalida durante la modifica a intere righe

1.  Aprire il set di dati facendo doppio clic il *XSD* del file in **Esplora soluzioni**. Per altre informazioni, vedere [procedura dettagliata: creazione di un set di dati in Progettazione Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Fare doppio clic sulla barra del titolo della tabella di dati nella finestra di progettazione.

     Una classe parziale viene creata con un `RowChanging` gestore dell'evento e viene aperto nell'Editor del codice.

    > [!NOTE]
    >  La finestra di progettazione set di dati non crea automaticamente un gestore eventi per il <xref:System.Data.DataTable.RowChanging> eventi nei progetti c#. È necessario creare un metodo per gestire il <xref:System.Data.DataTable.RowChanging> evento e eseguire codice quindi associare l'evento in un metodo di inizializzazione della tabella.

3.  Aggiungere il codice utente all'interno della dichiarazione di classe parziale.

4.  Il codice seguente mostra dove aggiungere il codice utente da convalidare durante la <xref:System.Data.DataTable.RowChanging> evento. Nell'esempio c# include anche codice per associare il metodo del gestore eventi fino al `OrdersRowChanging` evento.

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

## <a name="see-also"></a>Vedere anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md)