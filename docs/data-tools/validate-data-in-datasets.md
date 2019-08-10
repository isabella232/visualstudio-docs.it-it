---
title: Convalidare i dati nei set di dati
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 80f258e87bd7bd197460d5ff9ab29b6964347f7c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925410"
---
# <a name="validate-data-in-datasets"></a>Convalidare i dati nei set di dati
La convalida dei dati è il processo di conferma che i valori immessi negli oggetti dati sono conformi ai vincoli all'interno dello schema di un set di dati. Il processo di convalida conferma inoltre che questi valori seguono le regole stabilite per l'applicazione. È consigliabile convalidare i dati prima di inviare gli aggiornamenti al database sottostante. In questo modo si riducono gli errori, nonché il numero potenziale di round trip tra un'applicazione e il database.

È possibile verificare che i dati scritti in un set di dati siano validi compilando i controlli di convalida nel set di dati stesso. Il set di dati può controllare i dati indipendentemente dal modo in cui viene eseguito l'aggiornamento, direttamente dai controlli in un modulo, all'interno di un componente o in altro modo. Poiché il set di dati fa parte dell'applicazione (a differenza del back-end del database), si tratta di una posizione logica per compilare la convalida specifica dell'applicazione.

Il posto migliore per aggiungere la convalida all'applicazione si trova nel file di classe parziale del set di dati. In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]aprire il **Progettazione DataSet** e fare doppio clic sulla colonna o sulla tabella per cui si desidera creare la convalida. Questa azione crea automaticamente un <xref:System.Data.DataTable.ColumnChanging> gestore <xref:System.Data.DataTable.RowChanging> eventi o.

## <a name="validate-data"></a>Convalida dati
La convalida all'interno di un set di dati viene eseguita nei modi seguenti:

- Creando una convalida specifica dell'applicazione in grado di controllare i valori in una singola colonna di dati durante le modifiche. Per altre informazioni, vedere [Procedura: Convalidare i dati](validate-data-in-datasets.md)durante le modifiche alle colonne.

- Creando una convalida specifica dell'applicazione in grado di controllare i dati nei valori mentre è in corso la modifica di un'intera riga di dati. Per altre informazioni, vedere [Procedura: Convalidare i dati](validate-data-in-datasets.md)durante le modifiche alle righe.

- Creando chiavi, vincoli univoci e così via come parte della definizione dello schema effettiva del set di dati.

- Impostando <xref:System.Data.DataColumn> le proprietà dell'oggetto, <xref:System.Data.DataColumn.MaxLength%2A>ad esempio, <xref:System.Data.DataColumn.AllowDBNull%2A>e <xref:System.Data.DataColumn.Unique%2A>.

Quando si verifica una modifica in <xref:System.Data.DataTable> un record, i vari eventi vengono generati dall'oggetto:

- Gli <xref:System.Data.DataTable.ColumnChanging> eventi <xref:System.Data.DataTable.ColumnChanged> e vengono generati durante e dopo ogni modifica apportata a una singola colonna. L' <xref:System.Data.DataTable.ColumnChanging> evento è utile quando si desidera convalidare le modifiche in colonne specifiche. Le informazioni sulla modifica proposta vengono passate come argomento con l'evento.
- Gli <xref:System.Data.DataTable.RowChanging> eventi <xref:System.Data.DataTable.RowChanged> e vengono generati durante e dopo qualsiasi modifica in una riga. L' <xref:System.Data.DataTable.RowChanging> evento è più generale. Indica che si è verificata una modifica in un punto qualsiasi della riga, ma non si sa quale colonna è stata modificata.

Per impostazione predefinita, ogni modifica apportata a una colonna genera quindi quattro eventi. Il primo è l' <xref:System.Data.DataTable.ColumnChanging> evento <xref:System.Data.DataTable.ColumnChanged> e per la colonna specifica che viene modificata. Quindi gli eventi <xref:System.Data.DataTable.RowChanged>e. <xref:System.Data.DataTable.RowChanging> Se vengono apportate più modifiche alla riga, gli eventi verranno generati per ogni modifica.

> [!NOTE]
> Il metodo della riga <xref:System.Data.DataRow.BeginEdit%2A> di dati disattiva <xref:System.Data.DataTable.RowChanging> gli eventi <xref:System.Data.DataTable.RowChanged> e dopo ogni singola modifica della colonna. In tal caso, l'evento non viene generato fino a <xref:System.Data.DataRow.EndEdit%2A> quando non viene chiamato il metodo, <xref:System.Data.DataTable.RowChanging> quando <xref:System.Data.DataTable.RowChanged> gli eventi e vengono generati una sola volta. Per altre informazioni, vedere [disabilitare i vincoli durante il riempimento di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

L'evento scelto dipende dalla granularità desiderata per la convalida. Se è importante rilevare immediatamente un errore quando una colonna viene modificata, compilare la convalida usando l' <xref:System.Data.DataTable.ColumnChanging> evento. In caso contrario, <xref:System.Data.DataTable.RowChanging> utilizzare l'evento, che può comportare l'intercettazione di diversi errori contemporaneamente. Inoltre, se i dati sono strutturati in modo che il valore di una colonna venga convalidato in base al contenuto di un'altra colonna, eseguire <xref:System.Data.DataTable.RowChanging> la convalida durante l'evento.

Quando i record vengono aggiornati, <xref:System.Data.DataTable> l'oggetto genera eventi a cui è possibile rispondere quando si verificano modifiche e dopo che sono state apportate modifiche.

Se l'applicazione usa un DataSet tipizzato, è possibile creare gestori di eventi fortemente tipizzati. In questo modo vengono aggiunti quattro eventi tipizzati aggiuntivi per i quali è `dataTableNameRowChanging`possibile `dataTableNameRowChanged`creare `dataTableNameRowDeleting`gestori: `dataTableNameRowDeleted`,, e. Questi gestori di eventi tipizzati passano un argomento che include i nomi di colonna della tabella che semplificano la scrittura e la lettura del codice.

## <a name="data-update-events"></a>Eventi di aggiornamento dati

|event|Descrizione|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|È in corso la modifica del valore di una colonna. L'evento passa la riga e la colonna all'utente, insieme al nuovo valore proposto.|
|<xref:System.Data.DataTable.ColumnChanged>|Il valore in una colonna è stato modificato. L'evento passa la riga e la colonna all'utente, insieme al valore proposto.|
|<xref:System.Data.DataTable.RowChanging>|Il commit delle modifiche apportate <xref:System.Data.DataRow> a un oggetto sta per essere eseguito nuovamente nel set di dati. Se non è stato chiamato il <xref:System.Data.DataRow.BeginEdit%2A> metodo, l' <xref:System.Data.DataTable.RowChanging> evento viene generato per ogni modifica apportata a una colonna <xref:System.Data.DataTable.ColumnChanging> immediatamente dopo la generazione dell'evento. Se è stato <xref:System.Data.DataRow.BeginEdit%2A> chiamato prima di apportare modifiche <xref:System.Data.DataTable.RowChanging> , l'evento viene generato solo quando si <xref:System.Data.DataRow.EndEdit%2A> chiama il metodo.<br /><br /> L'evento passa la riga all'utente, insieme a un valore che indica il tipo di azione (modifica, inserimento e così via) da eseguire.|
|<xref:System.Data.DataTable.RowChanged>|Una riga è stata modificata. L'evento passa la riga all'utente, insieme a un valore che indica il tipo di azione (modifica, inserimento e così via) da eseguire.|
|<xref:System.Data.DataTable.RowDeleting>|È in corso l'eliminazione di una riga. L'evento passa la riga all'utente, insieme a un valore che indica il tipo di azione (Delete) eseguito.|
|<xref:System.Data.DataTable.RowDeleted>|Una riga è stata eliminata. L'evento passa la riga all'utente, insieme a un valore che indica il tipo di azione (Delete) eseguito.|

Gli <xref:System.Data.DataTable.ColumnChanging>eventi <xref:System.Data.DataTable.RowChanging>, e<xref:System.Data.DataTable.RowDeleting> vengono generati durante il processo di aggiornamento. È possibile utilizzare questi eventi per convalidare i dati o eseguire altri tipi di elaborazione. Poiché l'aggiornamento è in corso durante questi eventi, è possibile annullarlo generando un'eccezione, che impedisce il completamento dell'aggiornamento.

Gli <xref:System.Data.DataTable.ColumnChanged>eventi <xref:System.Data.DataTable.RowChanged> , e<xref:System.Data.DataTable.RowDeleted> sono eventi di notifica generati quando l'aggiornamento è stato completato correttamente. Questi eventi sono utili quando si desidera eseguire ulteriori azioni in base a un aggiornamento riuscito.

## <a name="validate-data-during-column-changes"></a>Convalida dei dati durante le modifiche alle colonne

> [!NOTE]
> Il **Progettazione DataSet** crea una classe parziale in cui è possibile aggiungere la logica di convalida a un set di dati. Il set di dati generato dalla finestra di progettazione non elimina o modifica il codice nella classe parziale.

È possibile convalidare i dati quando il valore di una colonna di dati cambia <xref:System.Data.DataTable.ColumnChanging> rispondendo all'evento. Quando viene generato, questo evento passa un argomento di<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>evento () che contiene il valore proposto per la colonna corrente. In base al contenuto di `e.ProposedValue`, è possibile:

- Accetta il valore proposto senza eseguire alcuna operazione.

- Rifiutare il valore proposto impostando la colonna Error (<xref:System.Data.DataRow.SetColumnError%2A>) dall'interno del gestore dell'evento di modifica della colonna.

- Facoltativamente, utilizzare <xref:System.Windows.Forms.ErrorProvider> un controllo per visualizzare un messaggio di errore all'utente. Per altre informazioni, vedere [Componente ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

La convalida può essere eseguita anche durante <xref:System.Data.DataTable.RowChanging> l'evento.

## <a name="validate-data-during-row-changes"></a>Convalida dei dati durante le modifiche alle righe
È possibile scrivere codice per verificare che ogni colonna che si desidera convalidare contenga dati che soddisfino i requisiti dell'applicazione. A tale scopo, impostare la colonna per indicare che contiene un errore se un valore proposto non è accettabile. Negli esempi seguenti viene impostato un errore di colonna `Quantity` quando la colonna è minore o pari a 0. I gestori eventi per la modifica della riga dovrebbero essere simili agli esempi seguenti.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Per convalidare i dati in caso di modifica di una riga (Visual Basic)

1. Aprire il set di dati in **Progettazione DataSet**. Per altre informazioni, vedere [Procedura dettagliata: Creazione di un set di dati](walkthrough-creating-a-dataset-with-the-dataset-designer.md)nel Progettazione DataSet.

2. Fare doppio clic sulla barra del titolo della tabella che si desidera convalidare. Questa azione crea automaticamente il <xref:System.Data.DataTable.RowChanging> gestore eventi <xref:System.Data.DataTable> di nel file di classe parziale del set di dati.

    > [!TIP]
    > Fare doppio clic a sinistra del nome della tabella per creare il gestore dell'evento di modifica della riga. Se si fa doppio clic sul nome della tabella, è possibile modificarlo.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>Per convalidare i dati in casoC#di modifica di una riga ()

1. Aprire il set di dati in **Progettazione DataSet**. Per altre informazioni, vedere [Procedura dettagliata: Creazione di un set di dati](walkthrough-creating-a-dataset-with-the-dataset-designer.md)nel Progettazione DataSet.

2. Fare doppio clic sulla barra del titolo della tabella che si desidera convalidare. Questa azione crea un file di classe parziale per <xref:System.Data.DataTable>.

    > [!NOTE]
    > Il **Progettazione DataSet** non crea automaticamente un gestore eventi per l' <xref:System.Data.DataTable.RowChanging> evento. È necessario creare un metodo per gestire l' <xref:System.Data.DataTable.RowChanging> evento ed eseguire il codice per associare l'evento nel metodo di inizializzazione della tabella.

3. Copiare il codice seguente nella classe parziale:

    ```csharp
    public override void EndInit()
    {
        base.EndInit();
        Order_DetailsRowChanging += TestRowChangeEvent;
    }

    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)
    {
        if ((short)e.Row.Quantity <= 0)
        {
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
        }
        else
        {
            e.Row.SetColumnError("Quantity", "");
        }
    }
    ```

## <a name="to-retrieve-changed-rows"></a>Per recuperare le righe modificate
Ogni riga di una tabella dati dispone di <xref:System.Data.DataRow.RowState%2A> una proprietà che tiene traccia dello stato corrente della riga utilizzando i valori <xref:System.Data.DataRowState> dell'enumerazione. È possibile restituire righe modificate da un set di dati o da una tabella `GetChanges` dati chiamando il <xref:System.Data.DataSet> metodo <xref:System.Data.DataTable>di un oggetto o. È possibile verificare che le modifiche siano presenti prima `GetChanges` di chiamare chiamando <xref:System.Data.DataSet.HasChanges%2A> il metodo di un set di dati.

> [!NOTE]
> Dopo aver eseguito il commit delle modifiche a un set di dati o a <xref:System.Data.DataSet.AcceptChanges%2A> una tabella di dati `GetChanges` (chiamando il metodo), il metodo non restituisce alcun dato. Se l'applicazione deve elaborare le righe modificate, è necessario elaborare le modifiche prima di chiamare `AcceptChanges` il metodo.

La chiamata <xref:System.Data.DataSet.GetChanges%2A> al metodo di un set di dati o di una tabella di dati restituisce un nuovo set di dati o una tabella di dati che contiene solo i record che sono stati modificati. Se si desidera ottenere record specifici, ad esempio solo i nuovi record o solo i record modificati, è possibile passare un valore dall' <xref:System.Data.DataRowState> enumerazione come parametro `GetChanges` al metodo.

Utilizzare l' <xref:System.Data.DataRowVersion> enumerazione per accedere alle diverse versioni di una riga, ad esempio i valori originali presenti in una riga prima dell'elaborazione.

### <a name="to-get-all-changed-records-from-a-dataset"></a>Per ottenere tutti i record modificati da un set di dati

- Chiamare il <xref:System.Data.DataSet.GetChanges%2A> metodo di un set di dati.

     Nell'esempio seguente viene creato un nuovo set `changedRecords` di dati denominato e viene popolato con tutti i record modificati da `dataSet1`un altro set di dati denominato.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>Per ottenere tutti i record modificati da una tabella dati

- Chiamare il <xref:System.Data.DataTable.GetChanges%2A> metodo di un oggetto DataTable.

     Nell'esempio seguente viene creata una nuova tabella dati `changedRecordsTable` denominata che viene popolata con tutti i record modificati di un'altra tabella `dataTable1`dati denominata.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Per ottenere tutti i record con uno stato di riga specifico

- Chiamare il `GetChanges` metodo di un set di dati o una tabella di <xref:System.Data.DataRowState> dati e passare un valore di enumerazione come argomento.

     Nell'esempio seguente viene illustrato come creare un nuovo set di `addedRecords` dati denominato e popolarlo solo con i `dataSet1` record che sono stati aggiunti al set di dati.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     Nell'esempio seguente viene illustrato come restituire tutti i record aggiunti di recente alla `Customers` tabella:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Accedere alla versione originale di un DataRow
Quando vengono apportate modifiche alle righe di dati, il set di dati conserva<xref:System.Data.DataRowVersion.Original>sia le versioni originali<xref:System.Data.DataRowVersion.Current>() che le nuove () della riga. Ad esempio, prima di chiamare `AcceptChanges` il metodo, l'applicazione può accedere alle diverse versioni di un record (come definito <xref:System.Data.DataRowVersion> nell'enumerazione) ed elaborare le modifiche di conseguenza.

> [!NOTE]
> Diverse versioni di una riga esistono solo dopo che è stata modificata e prima che il `AcceptChanges` metodo venga chiamato. Una volta `AcceptChanges` chiamato il metodo, le versioni correnti e originali sono le stesse.

Il passaggio <xref:System.Data.DataRowVersion> del valore con l'indice di colonna (o il nome della colonna come stringa) restituisce il valore della versione di riga specifica di tale colonna. La colonna modificata viene identificata durante <xref:System.Data.DataTable.ColumnChanging> gli <xref:System.Data.DataTable.ColumnChanged> eventi e. Questo è il momento giusto per esaminare le diverse versioni di riga a scopo di convalida. Tuttavia, se sono presenti vincoli temporanei sospesi, tali eventi non verranno generati e sarà necessario identificare a livello di codice le colonne che sono state modificate. Questa operazione può essere eseguita scorrendo la <xref:System.Data.DataTable.Columns%2A> raccolta e confrontando i <xref:System.Data.DataRowVersion> diversi valori.

### <a name="to-get-the-original-version-of-a-record"></a>Per ottenere la versione originale di un record

- Accedere al valore di una colonna passando l'oggetto <xref:System.Data.DataRowVersion> della riga che si desidera restituire.

     Nell'esempio seguente viene illustrato come utilizzare un <xref:System.Data.DataRowVersion> valore per ottenere il valore originale di un `CompanyName` campo in un <xref:System.Data.DataRow>oggetto:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Accedere alla versione corrente di un DataRow

### <a name="to-get-the-current-version-of-a-record"></a>Per ottenere la versione corrente di un record

- Accedere al valore di una colonna, quindi aggiungere un parametro all'indice che indica la versione di una riga che si desidera restituire.

     Nell'esempio seguente viene illustrato come utilizzare un <xref:System.Data.DataRowVersion> valore per ottenere il valore corrente di un `CompanyName` campo in un <xref:System.Data.DataRow>oggetto:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Procedura: Convalidare i dati nel controllo DataGridView Windows Forms](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Procedura: Visualizza le icone di errore per la convalida dei form con il componente Windows Forms ErrorProvider](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)