---
title: Convalidare i dati nei set di dati | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5dd01b20e84bbe39e0c082a0b598fb6742f33d9f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279019"
---
# <a name="validate-data-in-datasets"></a>Convalidare i dati nei set di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
La convalida dei dati è il processo di conferma che i valori immessi negli oggetti di data è conforme ai vincoli all'interno dello schema del set di dati. Il processo di convalida verifica anche che questi valori sono i seguenti le regole che sono state stabilite per l'applicazione. È buona norma convalidare i dati prima dell'invio degli aggiornamenti al database sottostante. In questo modo si riduce gli errori, nonché il numero potenziale di round trip tra un'applicazione e il database.  
  
 È possibile confermare che i dati che vengono salvati in un set di dati siano validi creando i controlli di convalida nel set di dati stesso. Il set di dati può controllare i dati, indipendentemente dal modo in cui viene eseguita l'aggiornamento, ovvero direttamente dai controlli in un form, all'interno di un componente o in altro modo. Poiché il set di dati fa parte dell'applicazione (a differenza del back-end di database), è una posizione logica per compilare una convalida specifiche dell'applicazione.  
  
 Il modo migliore per aggiungere la convalida per l'applicazione è nel file di classe parziale del set di dati. Nelle [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] oppure [!INCLUDE[csprcs](../includes/csprcs-md.md)], aprire il **Progettazione Dataset** e fare doppio clic la colonna o una tabella per cui si desidera creare una convalida. Questa azione crea automaticamente un' <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> gestore dell'evento. Per altre informazioni, vedere [come: convalidare i dati durante la modifica delle colonne](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5) oppure [procedura: convalidare i dati durante le modifiche riga](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc). Per un esempio completo, vedere [procedura dettagliata: aggiunta di convalida a un set di dati](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
## <a name="validate-data"></a>Convalidare i dati  
 Convalida all'interno di un set di dati può essere eseguita nei modi seguenti:  
  
-   Quando si crea il proprio convalida specifiche dell'applicazione in grado di verificare i valori in una singola colonna dati durante le modifiche.  Per altre informazioni, vedere [procedura: convalidare i dati durante la modifica delle colonne](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
-   Tramite la creazione di convalida personalizzata specifici dell'applicazione in grado di verificare i dati dei valori, mentre un intero data la modifica di riga. Per altre informazioni, vedere [procedura: convalidare i dati durante le modifiche riga](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
-   Tramite la creazione di chiavi, vincoli unique, e così via come parte della definizione effettiva dello schema del set di dati. Per altre informazioni sull'inclusione di convalida nella definizione dello schema, vedere [vincolare un oggetto DataColumn per contenere valori univoci](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
-   Impostando le proprietà del <xref:System.Data.DataColumn> dell'oggetto, ad esempio <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, e <xref:System.Data.DataColumn.Unique%2A>.  
  
 Diversi eventi generati dal <xref:System.Data.DataTable> quando viene apportata una modifica in un record dell'oggetto:  
  
-   Il <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> gli eventi vengono generati durante e dopo ogni modifica apportata a una singola colonna. Il <xref:System.Data.DataTable.ColumnChanging> evento è utile quando si desidera convalidare le modifiche in colonne specifiche. Informazioni sulla modifica di proposta viene passate come argomento all'evento. Per altre informazioni, vedere [procedura: convalidare i dati durante la modifica delle colonne](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
-   Il <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> gli eventi vengono generati durante e dopo qualsiasi modifica apportata a una riga. Il <xref:System.Data.DataTable.RowChanging> evento è più generale. Indica che viene apportata una modifica in un punto qualsiasi nella riga, ma non si sa quale colonna è stata modificata. Per altre informazioni, vedere [procedura: convalidare i dati durante le modifiche riga](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
 Per impostazione predefinita, ogni modifica apportata a una colonna genera quindi quattro eventi. Il primo è il <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> eventi per la colonna specifica da modificare. Successivamente vengono le <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> eventi. Se vengono apportate più modifiche alla riga, gli eventi verranno generati per ogni modifica.  
  
> [!NOTE]
>  La riga di dati <xref:System.Data.DataRow.BeginEdit%2A> metodo consente di disattivare il <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> eventi dopo ogni modifica di singole colonne. In tal caso, l'evento non viene generato finché il <xref:System.Data.DataRow.EndEdit%2A> metodo è stato chiamato quando il <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> gli eventi vengono generati una sola volta. Per altre informazioni, vedere [disattivare i vincoli durante il riempimento di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
 L'evento che scelto dipende il livello di granularità desiderato la convalida. Se è importante intercettare un errore immediatamente quando viene modificato una colonna, convalida della build usando il <xref:System.Data.DataTable.ColumnChanging> evento. In caso contrario, usare il <xref:System.Data.DataTable.RowChanging> evento, che potrebbe comportare l'intercettazione di diversi errori in una sola volta. Inoltre, se i dati sono strutturati in modo che il valore di una colonna viene convalidato in base al contenuto di un'altra colonna, quindi eseguire la convalida durante la <xref:System.Data.DataTable.RowChanging> evento.  
  
 Quando vengono aggiornati i record, il <xref:System.Data.DataTable> oggetto genera gli eventi che è possibile rispondere alle modifiche che si verifichino e dopo aver apportato modifiche.  
  
 Se l'applicazione usa un dataset tipizzato, è possibile creare gestori eventi fortemente tipizzati. Questo aggiungerà altri quattro eventi tipizzati che è possibile creare gestori per: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, e `dataTableNameRowDeleted`. Questi gestori eventi tipizzato passano un argomento che include i nomi delle colonne della tabella che rendono più facile leggere e scrivere codice.  
  
## <a name="data-update-events"></a>Eventi di aggiornamento dati  
  
|event|Descrizione|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|Il valore in una colonna viene modificato. L'evento passa la riga e colonna, con il nuovo valore proposto.|  
|<xref:System.Data.DataTable.ColumnChanged>|Il valore in una colonna è stato modificato. L'evento passa la riga e colonna, insieme al valore proposto.|  
|<xref:System.Data.DataTable.RowChanging>|Le modifiche apportate a un <xref:System.Data.DataRow> oggetto sta tentando di eseguire il commit nel dataset. Se non è stato chiamato il <xref:System.Data.DataRow.BeginEdit%2A> metodo, il <xref:System.Data.DataTable.RowChanging> evento viene generato per ogni modifica apportata a una colonna immediatamente dopo il <xref:System.Data.DataTable.ColumnChanging> evento è stato generato. Se è stato chiamato <xref:System.Data.DataRow.BeginEdit%2A> prima di apportare modifiche, il <xref:System.Data.DataTable.RowChanging> evento viene generato solo quando si chiama il <xref:System.Data.DataRow.EndEdit%2A> (metodo).<br /><br /> L'evento passa la riga, oltre a un valore che indica il tipo di azione (modifica, inserimento e così via) viene eseguito.|  
|<xref:System.Data.DataTable.RowChanged>|Una riga è stata modificata. L'evento passa la riga, oltre a un valore che indica il tipo di azione (modifica, inserimento e così via) viene eseguito.|  
|<xref:System.Data.DataTable.RowDeleting>|Viene eliminata una riga. L'evento passa la riga, oltre a un valore che indica il tipo di azione (delete) viene eseguito.|  
|<xref:System.Data.DataTable.RowDeleted>|Una riga è stata eliminata. L'evento passa la riga, oltre a un valore che indica il tipo di azione (delete) viene eseguito.|  
  
 Il <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, e <xref:System.Data.DataTable.RowDeleting> gli eventi vengono generati durante il processo di aggiornamento. È possibile utilizzare questi eventi per convalidare i dati o eseguire altri tipi di elaborazione. Poiché l'aggiornamento è in corso durante questi eventi, è possibile annullarlo generando un'eccezione, che impedisce l'aggiornamento da terminare.  
  
 Il <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> e <xref:System.Data.DataTable.RowDeleted> gli eventi sono eventi di notifica che sono stati generati durante l'aggiornamento è stato completato. Questi eventi sono utili quando si desidera eseguire ulteriori operazioni di base di un aggiornamento ha esito positivo.  
  
## <a name="validate-data-during-column-changes"></a>Convalidare i dati durante la modifica delle colonne  
  
> [!NOTE]
>  Il **Progettazione Dataset** crea una classe parziale in cui la convalida per la logica può essere aggiunti a un set di dati. Il set di dati generato da progettazione non eliminare o modificare il codice nella classe parziale.  
  
 È possibile convalidare dati quando cambia il valore in una colonna di dati in risposta al <xref:System.Data.DataTable.ColumnChanging> evento. Quando generato, questo evento passa un argomento di evento (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) che contiene il valore che viene viene proposto per la colonna corrente. In base al contenuto di `e.ProposedValue`, è possibile:  
  
-   Accettare il valore proposto, viene eseguita alcuna operazione.  
  
-   Rifiutare il valore proposto, impostando l'errore di colonna (<xref:System.Data.DataRow.SetColumnError%2A>) dall'interno del gestore eventi di modifica delle colonne.  
  
-   Facoltativamente, usare un <xref:System.Windows.Forms.ErrorProvider> controllo per visualizzare un messaggio di errore all'utente. Per altre informazioni, vedere [sul componente ErrorProvider](http://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6).  
  
 La convalida può essere eseguita anche durante il <xref:System.Data.DataTable.RowChanging> evento. Per altre informazioni, vedere [procedura: convalidare i dati durante le modifiche riga](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
## <a name="validate-data-during-row-changes"></a>Convalidare i dati durante la modifica delle righe  
 È possibile scrivere codice per verificare che ogni colonna che si desidera convalidare contenga dati che soddisfano i requisiti dell'applicazione. Eseguire questa operazione impostando la colonna a indicare che contiene un errore se un valore proposto è accettabile. L'esempio seguente imposta un errore di colonna quando il `Quantity` colonna è minore o uguale a 0. I gestori di eventi di modifica riga dovrebbero essere simile negli esempi seguenti.  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Per convalidare i dati quando una riga viene modificato (Visual Basic)  
  
1.  Aprire il set di dati nel **Progettazione Dataset**. Per altre informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Fare doppio clic sulla barra del titolo della tabella da convalidare. Questa azione crea automaticamente il <xref:System.Data.DataTable.RowChanging> gestore dell'evento del <xref:System.Data.DataTable> nel file di classe parziale del set di dati.  
  
    > [!TIP]
    >  Fare doppio clic a sinistra del nome della tabella per creare il gestore di eventi di modifica di riga. Se si fa doppio clic il nome della tabella, è possibile modificarlo.  
  
     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>Per convalidare i dati quando viene modificata una riga (c#)  
  
1.  Aprire il set di dati nel **Progettazione Dataset**. Per altre informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Fare doppio clic sulla barra del titolo della tabella da convalidare. Questa azione crea un file di classe parziale per il <xref:System.Data.DataTable>.  
  
    > [!NOTE]
    >  Il **Progettazione Dataset** non crea automaticamente un gestore eventi per il <xref:System.Data.DataTable.RowChanging> evento. È necessario creare un metodo per gestire il <xref:System.Data.DataTable.RowChanging> evento ed eseguire codice per associare l'evento in un metodo di inizializzazione della tabella.  
  
3.  Copiare il codice seguente nella classe parziale:  
  
    ```  
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
 Ogni riga in una tabella di dati ha un <xref:System.Data.DataRow.RowState%2A> che tiene traccia dello stato corrente della riga usando i valori nelle proprietà di <xref:System.Data.DataRowState> enumerazione. È possibile restituire le righe modificate da una tabella di dati o set di dati chiamando il `GetChanges` metodo di un <xref:System.Data.DataSet> o <xref:System.Data.DataTable>. È possibile verificare l'esistano delle modifiche prima di chiamare `GetChanges` chiamando il <xref:System.Data.DataSet.HasChanges%2A> metodo di un set di dati. Per altre informazioni sulle <xref:System.Data.DataSet.HasChanges%2A>, vedere [procedura: verificare la presenza di righe modificate](http://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653).  
  
> [!NOTE]
>  Dopo il commit delle modifiche a una tabella di dati o set di dati (chiamando il <xref:System.Data.DataSet.AcceptChanges%2A> metodo), il `GetChanges` metodo non restituisce alcun dato. Se l'applicazione deve elaborare le righe modificate, è necessario elaborare le modifiche prima di chiamare il `AcceptChanges` (metodo).  
  
 La chiamata di <xref:System.Data.DataSet.GetChanges%2A> metodo di una tabella di dati o set di dati restituisce una nuovo set di dati o una tabella dati contenente solo i record che sono stati modificati. Se si desidera ottenere record specifici, ad esempio, solo i record nuovi o modificati, è possibile passare un valore compreso il <xref:System.Data.DataRowState> enumerazione come parametro per il `GetChanges` (metodo).  
  
 Usare il <xref:System.Data.DataRowVersion> enumerazione per accedere alle versioni diverse di una riga (ad esempio, i valori originali in una riga prima della sua elaborazione).  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>Per ottenere tutti i record modificati da un set di dati  
  
-   Chiamare il <xref:System.Data.DataSet.GetChanges%2A> metodo di un set di dati.  
  
     L'esempio seguente crea un nuovo set di dati denominato `changedRecords` e lo popola con tutti i record modificati da un altro set di dati denominato `dataSet1`.  
  
     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>Per ottenere tutti i record modificati da una tabella dati  
  
-   Chiamare il <xref:System.Data.DataTable.GetChanges%2A> metodo di un oggetto DataTable.  
  
     L'esempio seguente crea una nuova tabella di dati denominata `changedRecordsTable` e lo popola con tutti i record modificati da un'altra tabella di dati denominato `dataTable1`.  
  
     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Per ottenere tutti i record che hanno uno stato di riga specifico  
  
-   Chiamare il `GetChanges` metodo di un set di dati o tabella di dati e passare un <xref:System.Data.DataRowState> valore di enumerazione come argomento.  
  
     Nell'esempio seguente viene illustrato come creare un nuovo set di dati denominato `addedRecords` e popolarla solo con i record che sono state aggiunte ad il `dataSet1` set di dati.  
  
     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]  
  
-   Nell'esempio seguente viene illustrato come restituire tutti i record che sono stati aggiunti di recente per il `Customers` tabella:  
  
     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>Accedere alla versione originale di un DataRow  
 Quando vengono apportate modifiche alle righe di dati, il set di dati consente di mantenere entrambi originale (<xref:System.Data.DataRowVersion>) e dell'operatore new (<xref:System.Data.DataRowVersion>) le versioni di riga. Ad esempio, prima di chiamare il `AcceptChanges` metodo, l'applicazione possa accedere a diverse versioni di un record (come definito nel <xref:System.Data.DataRowVersion> enumerazione) ed elaborarli di conseguenza le modifiche.  
  
> [!NOTE]
>  Versioni diverse di una riga esistono solo dopo che è stata modificata e prima che il `AcceptChanges` chiamata al metodo. Dopo il `AcceptChanges` chiamata al metodo, le versioni correnti e originali sono uguali.  
  
 Passando il <xref:System.Data.DataRowVersion> valore con l'indice di colonna (o nome della colonna sotto forma di stringa) restituisce il valore di particolare versione di riga tale colonna. La colonna modificata è identificata durante la <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> eventi. Questo è il momento giusto per controllare le versioni di riga diverse ai fini della convalida. Tuttavia, se è stata sospesa temporaneamente i vincoli, questi eventi non verranno generati e sarà necessario a livello di programmazione di identificare le colonne che sono stati modificati. È possibile farlo eseguendo l'iterazione tramite il <xref:System.Data.DataTable.Columns%2A> raccolta e confrontare i diversi <xref:System.Data.DataRowVersion> valori.  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Per ottenere la versione originale di un record  
  
-   Accedere al valore di una colonna, passando il <xref:System.Data.DataRowVersion> della riga di cui si desidera restituire.  
  
     Nell'esempio seguente viene illustrato come utilizzare un <xref:System.Data.DataRowVersion> valore da ottenere il valore originale di una `CompanyName` campo un <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>Accedere alla versione corrente di un DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Per ottenere la versione corrente di un record  
  
-   Accedere al valore di una colonna e quindi aggiungere un parametro per l'indice che indica quale versione di una riga a cui si desidera restituire.  
  
     Nell'esempio seguente viene illustrato come utilizzare un <xref:System.Data.DataRowVersion> valore da ottenere il valore corrente di un `CompanyName` campo un <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Procedura: Connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Procedura: convalidare dati nel controllo DataGridView Windows Form](http://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)   
 [Procedura: Visualizzare le icone di errori per la convalida dei form con il componente ErrorProvider di Windows Form](http://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)

