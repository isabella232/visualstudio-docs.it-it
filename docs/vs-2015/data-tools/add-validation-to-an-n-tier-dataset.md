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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94a8f4f8fe0d1f93ce3467291a20377234db29f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968653"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Aggiungere la convalida a un set di dati a più livelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aggiunta della convalida a un set di dati è suddivisa in una soluzione a più livelli è essenzialmente uguale all'aggiunta di convalida a un singolo file dataset (un set di dati in un unico progetto). Il percorso suggerito per eseguire la convalida dei dati è durante la <xref:System.Data.DataTable.ColumnChanging> e/o <xref:System.Data.DataTable.RowChanging> gli eventi di una tabella dati.  
  
La finestra di progettazione set di dati fornisce la funzionalità per creare classi parziali a cui è possibile aggiungere il codice utente per colonna e riga modifica gli eventi delle tabelle di dati nel set di dati. Per altre informazioni sull'aggiunta di codice a un set di dati in una soluzione a più livelli, vedere [aggiungere codice al set di dati in applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md), e [aggiungere codice agli oggetti TableAdapter in applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Per altre informazioni sulle classi parziali, vedere [come: Dividere una classe in classi parziali (Progettazione classi)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) oppure [classi e metodi parziali](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).  
  
> [!NOTE]
>  Quando si separano i set di dati da oggetti TableAdapter (impostando il **DataSetProject** proprietà), sarà spostate automaticamente classi parziali del dataset presenti nel progetto. Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.  
  
> [!NOTE]
>  La finestra di progettazione set di dati non crea automaticamente i gestori eventi in C# per il <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> eventi. È necessario creare un gestore dell'evento manualmente e associare il gestore eventi all'evento sottostante. Le procedure seguenti descrivono come creare i gestori eventi necessaria in Visual Basic e C#.  
  
## <a name="validatechanges-to-individual-columns"></a>Validatechanges alle singole colonne  
 Convalidare i valori delle singole colonne gestendo il <xref:System.Data.DataTable.ColumnChanging> evento. Il <xref:System.Data.DataTable.ColumnChanging> evento viene generato quando viene modificato un valore in una colonna. Creare un gestore eventi per il <xref:System.Data.DataTable.ColumnChanging> eventi facendo doppio clic sul set di dati colonna desiderata.  
  
 La prima volta che si fa doppio clic su una colonna, la finestra di progettazione genera un gestore eventi per il <xref:System.Data.DataTable.ColumnChanging> evento. Un `If…Then` istruzione viene creata anche che i test per la colonna specifica. Ad esempio, il codice seguente viene generato quando si fa doppio clic sulla colonna RequiredDate nel tabella Orders di Northwind:  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  Nei progetti C#, la finestra di progettazione set di dati crea solo le classi parziali per il set di dati e le singole tabelle nel set di dati. La finestra di progettazione set di dati non crea automaticamente i gestori eventi per il <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> eventi in C# come avviene in Visual Basic. Nei progetti C#, è necessario creare manualmente un metodo per gestire l'evento e associare il metodo dell'evento sottostante. La seguente procedura fornisce i passaggi per creare i gestori eventi necessaria in Visual Basic e C#.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Per aggiungere la convalida durante le modifiche ai valori di colonna singola  
  
1.  Aprire il set di dati nella finestra di progettazione facendo doppio clic il **XSD** del file in **Esplora soluzioni**. Per altre informazioni, vedere [Procedura: Aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Fare doppio clic sulla colonna da convalidare. Questa azione viene creata la <xref:System.Data.DataTable.ColumnChanging> gestore dell'evento.  
  
    > [!NOTE]
    >  La finestra di progettazione set di dati non crea automaticamente un gestore eventi per l'evento di C#. Il codice che è necessario gestire l'evento nel linguaggio C# è incluso nella sezione successiva. `SampleColumnChangingEvent` viene creato e quindi collegato al <xref:System.Data.DataTable.ColumnChanging> eventi nel <xref:System.Data.DataTable.EndInit%2A> (metodo).  
  
3.  Aggiungere il codice per verificare che `e.ProposedValue` contiene dati che soddisfano i requisiti dell'applicazione. Se il valore proposto è inaccettabile, impostare la colonna a indicare che contiene un errore.  
  
     Esempio di codice seguente consente di verificare che il **Quantity** colonna contiene più di 0. Se **Quantity** è minore o uguale a 0, la colonna è impostata su un errore. Il `Else` clausola risolve il problema se **Quantity** è maggiore di 0. Il codice nel gestore dell'evento di modifica delle colonne sarà simile al seguente:  
  
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
  
## <a name="validatechanges-to-whole-rows"></a>Validatechanges a intere righe  
 Convalidare i valori nelle righe intere gestendo il <xref:System.Data.DataTable.RowChanging> evento. Il <xref:System.Data.DataTable.RowChanging> evento viene generato quando vengono applicati i valori in tutte le colonne. È necessario convalidare il <xref:System.Data.DataTable.RowChanging> evento quando il valore in una colonna si basa sul valore in un'altra colonna. Si consideri ad esempio OrderDate e RequiredDate nel tabella Orders nel database Northwind.  
  
 Quando avviene l'immissione degli ordini, la convalida assicura che un ordine non viene immesso con una colonna RequiredDate che o prima OrderDate. In questo esempio, i valori per le colonne OrderDate sia RequiredDate necessario confrontare, in modo che la convalida di una singola modifica di colonna non ha senso.  
  
 Creare un gestore eventi per il <xref:System.Data.DataTable.RowChanging> eventi facendo doppio clic sul nome della tabella nella barra del titolo della tabella.  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Per aggiungere la convalida durante la modifica a intere righe  
  
1.  Aprire il set di dati nella finestra di progettazione facendo doppio clic il **XSD** del file in **Esplora soluzioni**. Per altre informazioni, vedere [Procedura: Aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Fare doppio clic sulla barra del titolo della tabella di dati nella finestra di progettazione.  
  
     Una classe parziale viene creata con un `RowChanging` gestore dell'evento e viene aperto nell'Editor del codice.  
  
    > [!NOTE]
    >  La finestra di progettazione set di dati non crea automaticamente un gestore eventi per il <xref:System.Data.DataTable.RowChanging> eventi nei progetti C#. È necessario creare un metodo per gestire il <xref:System.Data.DataTable.RowChanging> evento e eseguire codice per associare l'evento in un metodo di inizializzazione della tabella.  
  
3.  Aggiungere il codice utente all'interno della dichiarazione di classe parziale.  
  
4.  Il codice seguente mostra dove aggiungere il codice utente da convalidare durante la <xref:System.Data.DataTable.RowChanging> evento per Visual Basic:  
  
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
  
5.  Il codice seguente viene illustrato come creare i `RowChanging` gestore dell'evento e dove aggiungere il codice utente da convalidare durante il <xref:System.Data.DataTable.RowChanging> evento per il linguaggio C#:  
  
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
 [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)   
 [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md)
