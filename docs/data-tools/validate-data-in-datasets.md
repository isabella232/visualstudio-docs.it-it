---
title: Convalidare i dati nei set di dati
description: Informazioni su come convalidare i dati nei set di dati. La convalida dei dati implica la verifica che i valori immessi negli oggetti dati siano conformi ai vincoli all'interno dello schema di un set di dati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a9f714b4e66f14e313fa53466db80c99dfbef50f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631085"
---
# <a name="validate-data-in-datasets"></a>Convalidare i dati nei set di dati
La convalida dei dati è il processo di verifica che i valori immessi negli oggetti dati siano conformi ai vincoli all'interno dello schema di un set di dati. Il processo di convalida conferma anche che questi valori stanno seguendo le regole stabilite per l'applicazione. È consigliabile convalidare i dati prima di inviare aggiornamenti al database sottostante. In questo modo si riducono gli errori e il numero potenziale di round trip tra un'applicazione e il database.

È possibile verificare che i dati scritti in un set di dati siano validi compilando controlli di convalida nel set di dati stesso. Il set di dati può controllare i dati indipendentemente dalla modalità di esecuzione dell'aggiornamento, direttamente dai controlli in un form, all'interno di un componente o in altro modo. Poiché il set di dati fa parte dell'applicazione (a differenza del back-end del database), è una posizione logica per compilare la convalida specifica dell'applicazione.

La posizione migliore per aggiungere la convalida all'applicazione è nel file di classe parziale del set di dati. In o aprire il Progettazione DataSet e fare doppio clic sulla colonna o sulla tabella [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] per cui si desidera creare la [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] convalida.  Questa azione crea automaticamente un <xref:System.Data.DataTable.ColumnChanging> gestore <xref:System.Data.DataTable.RowChanging> eventi o .

## <a name="validate-data"></a>Convalidare i dati
La convalida all'interno di un set di dati viene eseguita nei modi seguenti:

- Creando una convalida specifica dell'applicazione in grado di controllare i valori in una singola colonna di dati durante le modifiche. Per altre informazioni, vedere [Procedura: Convalidare i dati durante le modifiche alle colonne.](validate-data-in-datasets.md)

- Tramite la creazione di una convalida specifica dell'applicazione in grado di controllare i dati in base ai valori durante la modifica di un'intera riga di dati. Per altre informazioni, vedere [Procedura: Convalidare i dati durante le modifiche alle righe.](validate-data-in-datasets.md)

- Creando chiavi, vincoli univoci e così via come parte della definizione dello schema effettiva del set di dati.

- Impostando le proprietà <xref:System.Data.DataColumn> dell'oggetto , ad esempio <xref:System.Data.DataColumn.MaxLength%2A> <xref:System.Data.DataColumn.AllowDBNull%2A> , e <xref:System.Data.DataColumn.Unique%2A> .

Quando si verifica una modifica in un record, vengono generati diversi <xref:System.Data.DataTable> eventi dall'oggetto :

- Gli <xref:System.Data.DataTable.ColumnChanging> eventi e vengono generati durante e dopo ogni modifica <xref:System.Data.DataTable.ColumnChanged> apportata a una singola colonna. <xref:System.Data.DataTable.ColumnChanging>L'evento è utile quando si desidera convalidare le modifiche in colonne specifiche. Le informazioni sulla modifica proposta vengono passate come argomento con l'evento .
- Gli <xref:System.Data.DataTable.RowChanging> eventi e vengono generati durante e dopo qualsiasi modifica in una <xref:System.Data.DataTable.RowChanged> riga. <xref:System.Data.DataTable.RowChanging>L'evento è più generale. Indica che è in corso una modifica in un punto qualsiasi della riga, ma non si conosce la colonna modificata.

Per impostazione predefinita, ogni modifica apportata a una colonna genera pertanto quattro eventi. Il primo è <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> l'evento e per la colonna specifica che viene modificata. Di seguito sono disponibili <xref:System.Data.DataTable.RowChanging> gli eventi <xref:System.Data.DataTable.RowChanged> e . Se vengono apportate più modifiche alla riga, gli eventi verranno generati per ogni modifica.

> [!NOTE]
> Il metodo della riga di <xref:System.Data.DataRow.BeginEdit%2A> dati disattiva gli eventi e dopo la modifica di ogni singola <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> colonna. In tal caso, l'evento non viene generato fino a quando non viene chiamato il metodo , quando <xref:System.Data.DataRow.EndEdit%2A> gli eventi e vengono generati una sola <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> volta. Per altre informazioni, vedere [Disattivare i vincoli durante il riempimento di un set di dati.](../data-tools/turn-off-constraints-while-filling-a-dataset.md)

L'evento scelto dipende dal livello di granularità desiderato per la convalida. Se è importante rilevare immediatamente un errore quando una colonna cambia, compilare la convalida usando <xref:System.Data.DataTable.ColumnChanging> l'evento . In caso contrario, usare <xref:System.Data.DataTable.RowChanging> l'evento , che potrebbe causare il rilevamento di diversi errori contemporaneamente. Inoltre, se i dati sono strutturati in modo che il valore di una colonna sia convalidato in base al contenuto di un'altra colonna, eseguire la convalida durante <xref:System.Data.DataTable.RowChanging> l'evento .

Quando i record vengono aggiornati, l'oggetto genera eventi a cui è possibile rispondere quando si verificano modifiche e <xref:System.Data.DataTable> dopo che vengono apportate modifiche.

Se l'applicazione usa un set di dati tipizzato, è possibile creare gestori eventi fortemente tipizzati. In questo modo vengono aggiunti altri quattro eventi tipici per i quali è possibile creare gestori: `dataTableNameRowChanging` `dataTableNameRowChanged` , , e `dataTableNameRowDeleting` `dataTableNameRowDeleted` . Questi gestori eventi tipici passano un argomento che include i nomi di colonna della tabella che semplificano la scrittura e la lettura del codice.

## <a name="data-update-events"></a>Eventi di aggiornamento dei dati

|Event|Descrizione|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Il valore in una colonna viene modificato. L'evento passa la riga e la colonna all'utente, insieme al nuovo valore proposto.|
|<xref:System.Data.DataTable.ColumnChanged>|Il valore in una colonna è stato modificato. L'evento passa la riga e la colonna all'utente, insieme al valore proposto.|
|<xref:System.Data.DataTable.RowChanging>|Le modifiche apportate a un oggetto stanno per essere nuovamente <xref:System.Data.DataRow> salvate nel set di dati. Se il metodo non è stato chiamato, l'evento viene generato per ogni modifica apportata a una colonna <xref:System.Data.DataRow.BeginEdit%2A> immediatamente dopo la generazione <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.ColumnChanging> dell'evento. Se è stato chiamato <xref:System.Data.DataRow.BeginEdit%2A> prima di apportare modifiche, <xref:System.Data.DataTable.RowChanging> l'evento viene generato solo quando si chiama il <xref:System.Data.DataRow.EndEdit%2A> metodo .<br /><br /> L'evento passa la riga all'utente, insieme a un valore che indica il tipo di azione (modifica, inserimento e così via) in esecuzione.|
|<xref:System.Data.DataTable.RowChanged>|Una riga è stata modificata. L'evento passa la riga all'utente, insieme a un valore che indica il tipo di azione (modifica, inserimento e così via) in esecuzione.|
|<xref:System.Data.DataTable.RowDeleting>|È in corso l'eliminazione di una riga. L'evento passa la riga all'utente, insieme a un valore che indica il tipo di azione (eliminazione) eseguita.|
|<xref:System.Data.DataTable.RowDeleted>|Una riga è stata eliminata. L'evento passa la riga all'utente, insieme a un valore che indica il tipo di azione (eliminazione) eseguita.|

Gli <xref:System.Data.DataTable.ColumnChanging> eventi , e vengono generati durante il processo di <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowDeleting> aggiornamento. È possibile utilizzare questi eventi per convalidare i dati o eseguire altri tipi di elaborazione. Poiché l'aggiornamento è in corso durante questi eventi, è possibile annullarlo generando un'eccezione che impedisce il completamento dell'aggiornamento.

Gli <xref:System.Data.DataTable.ColumnChanged> eventi , e sono eventi di notifica generati al termine <xref:System.Data.DataTable.RowChanged> <xref:System.Data.DataTable.RowDeleted> dell'aggiornamento. Questi eventi sono utili quando si desidera eseguire ulteriori azioni in base a un aggiornamento riuscito.

## <a name="validate-data-during-column-changes"></a>Convalidare i dati durante le modifiche alle colonne

> [!NOTE]
> **L Progettazione DataSet** crea una classe parziale in cui è possibile aggiungere la logica di convalida a un set di dati. Il set di dati generato dalla finestra di progettazione non elimina o modifica il codice nella classe parziale.

È possibile convalidare i dati quando il valore in una colonna di dati cambia rispondendo <xref:System.Data.DataTable.ColumnChanging> all'evento . Quando viene generato, questo evento passa un argomento dell'evento ( ) che contiene il valore proposto <xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A> per la colonna corrente. In base al contenuto di `e.ProposedValue` , è possibile:

- Accettare il valore proposto senza eseguire alcuna operazione.

- Rifiutare il valore proposto impostando l'errore di colonna ( <xref:System.Data.DataRow.SetColumnError%2A> ) dal gestore eventi di modifica della colonna.

- Facoltativamente, usare <xref:System.Windows.Forms.ErrorProvider> un controllo per visualizzare un messaggio di errore all'utente. Per altre informazioni, vedere [Componente ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

La convalida può essere eseguita anche durante <xref:System.Data.DataTable.RowChanging> l'evento .

## <a name="validate-data-during-row-changes"></a>Convalidare i dati durante le modifiche alle righe
È possibile scrivere codice per verificare che ogni colonna da convalidare contenga dati che soddisfano i requisiti dell'applicazione. A tale scopo, impostare la colonna per indicare che contiene un errore se un valore proposto non è accettabile. Negli esempi seguenti viene impostato un errore di colonna quando `Quantity` la colonna è minore o minore di 0. I gestori dell'evento di modifica delle righe dovrebbero essere simili agli esempi seguenti.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Per convalidare i dati quando una riga viene modificata (Visual Basic)

1. Aprire il set di dati in **Progettazione DataSet**. Per altre informazioni, vedere [Procedura dettagliata: Creazione di un set di dati nel Progettazione DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Fare doppio clic sulla barra del titolo della tabella che si desidera convalidare. Questa azione crea automaticamente il gestore eventi di nel file di classe parziale <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable> del set di dati.

    > [!TIP]
    > Fare doppio clic a sinistra del nome della tabella per creare il gestore dell'evento di modifica delle righe. Se si fa doppio clic sul nome della tabella, è possibile modificarlo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb" id="Snippet3":::

### <a name="to-validate-data-when-a-row-changes-c"></a>Per convalidare i dati quando viene modificata una riga (C#)

1. Aprire il set di dati in **Progettazione DataSet**. Per altre informazioni, vedere [Procedura dettagliata: Creazione di un set di dati nel Progettazione DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Fare doppio clic sulla barra del titolo della tabella che si desidera convalidare. Questa azione crea un file di classe parziale per <xref:System.Data.DataTable> .

    > [!NOTE]
    > Il **Progettazione DataSet** non crea automaticamente un gestore eventi per l'evento <xref:System.Data.DataTable.RowChanging> . È necessario creare un metodo per gestire l'evento ed eseguire il codice <xref:System.Data.DataTable.RowChanging> per associare l'evento nel metodo di inizializzazione della tabella.

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
Ogni riga in una tabella dati ha una proprietà che tiene traccia dello stato corrente della riga usando <xref:System.Data.DataRow.RowState%2A> i valori <xref:System.Data.DataRowState> nell'enumerazione . È possibile restituire le righe modificate da un set di dati o da una tabella dati chiamando il `GetChanges` metodo di un oggetto o <xref:System.Data.DataSet> <xref:System.Data.DataTable> . È possibile verificare che le modifiche esistano prima di chiamare `GetChanges` chiamando il metodo di un set di <xref:System.Data.DataSet.HasChanges%2A> dati.

> [!NOTE]
> Dopo aver eseguito il commit delle modifiche a un set di dati o a una tabella dati (chiamando il metodo ), il <xref:System.Data.DataSet.AcceptChanges%2A> `GetChanges` metodo non restituisce dati. Se l'applicazione deve elaborare le righe modificate, è necessario elaborare le modifiche prima di chiamare il `AcceptChanges` metodo .

La chiamata al metodo di un set di dati o di una tabella di dati restituisce un nuovo set di dati o una nuova tabella di dati contenente <xref:System.Data.DataSet.GetChanges%2A> solo i record che sono stati modificati. Se si desidera ottenere record specifici, ad esempio solo nuovi record o solo record modificati, è possibile passare un valore dall'enumerazione <xref:System.Data.DataRowState> come parametro al metodo `GetChanges` .

Utilizzare l'enumerazione per accedere alle diverse versioni di una riga, ad esempio i valori originali presenti in una riga <xref:System.Data.DataRowVersion> prima dell'elaborazione.

### <a name="to-get-all-changed-records-from-a-dataset"></a>Per ottenere tutti i record modificati da un set di dati

- Chiamare il <xref:System.Data.DataSet.GetChanges%2A> metodo di un set di dati.

     Nell'esempio seguente viene creato un nuovo set di dati denominato e viene popolato con tutti i `changedRecords` record modificati di un altro set di dati denominato `dataSet1` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet14":::

### <a name="to-get-all-changed-records-from-a-data-table"></a>Per ottenere tutti i record modificati da una tabella dati

- Chiamare il <xref:System.Data.DataTable.GetChanges%2A> metodo di un oggetto DataTable.

     L'esempio seguente crea una nuova tabella dati denominata e la popola con tutti i record modificati `changedRecordsTable` di un'altra tabella di dati denominata `dataTable1` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet15":::

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Per ottenere tutti i record con uno stato di riga specifico

- Chiamare il `GetChanges` metodo di un set di dati o di una tabella dati e passare un valore di enumerazione come <xref:System.Data.DataRowState> argomento.

     L'esempio seguente illustra come creare un nuovo set di dati denominato e popolarlo solo con i record `addedRecords` aggiunti al set di `dataSet1` dati.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet16":::

     L'esempio seguente illustra come restituire tutti i record aggiunti di recente alla `Customers` tabella :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet17":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet17":::

## <a name="access-the-original-version-of-a-datarow"></a>Accedere alla versione originale di un DataRow
Quando vengono apportate modifiche alle righe di dati, il set di dati mantiene le versioni originali ( ) e <xref:System.Data.DataRowVersion.Original> nuove ( ) della <xref:System.Data.DataRowVersion.Current> riga. Ad esempio, prima di chiamare il metodo , l'applicazione può accedere alle diverse versioni di un record (come definito nell'enumerazione ) ed elaborare `AcceptChanges` <xref:System.Data.DataRowVersion> le modifiche di conseguenza.

> [!NOTE]
> Versioni diverse di una riga esistono solo dopo che è stata modificata e prima che sia stato `AcceptChanges` chiamato il metodo . Dopo la `AcceptChanges` chiamata al metodo , le versioni correnti e originali sono le stesse.

Passando il valore insieme all'indice di colonna (o al nome della colonna come stringa) viene restituito il valore dalla versione di riga <xref:System.Data.DataRowVersion> specifica della colonna. La colonna modificata viene identificata durante gli <xref:System.Data.DataTable.ColumnChanging> eventi e <xref:System.Data.DataTable.ColumnChanged> . Si tratta di un buon momento per esaminare le diverse versioni di riga ai fini della convalida. Tuttavia, se sono stati sospesi temporaneamente i vincoli, questi eventi non verranno generati e sarà necessario identificare a livello di codice le colonne modificate. A tale scopo, scorrere la raccolta e <xref:System.Data.DataTable.Columns%2A> confrontare i diversi <xref:System.Data.DataRowVersion> valori.

### <a name="to-get-the-original-version-of-a-record"></a>Per ottenere la versione originale di un record

- Accedere al valore di una colonna passando <xref:System.Data.DataRowVersion> l'oggetto della riga da restituire.

     Nell'esempio seguente viene illustrato come usare un <xref:System.Data.DataRowVersion> valore per ottenere il valore originale di un campo in un oggetto `CompanyName` <xref:System.Data.DataRow> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet21":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet21":::

## <a name="access-the-current-version-of-a-datarow"></a>Accedere alla versione corrente di un oggetto DataRow

### <a name="to-get-the-current-version-of-a-record"></a>Per ottenere la versione corrente di un record

- Accedere al valore di una colonna e quindi aggiungere un parametro all'indice che indica la versione di una riga da restituire.

     Nell'esempio seguente viene illustrato come usare un <xref:System.Data.DataRowVersion> valore per ottenere il valore corrente di un campo in un oggetto `CompanyName` <xref:System.Data.DataRow> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet22":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet22":::

## <a name="see-also"></a>Vedi anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Procedura: Convalidare i dati nel controllo DataGridView Windows Form](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Procedura: Visualizzare le icone di errore per la convalida dei moduli con il Windows Form ErrorProvider](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)
