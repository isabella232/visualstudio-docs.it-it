---
title: Salvare i dati di nuovo nel database
description: Usare gli strumenti del set di dati per salvare nuovamente i dati nel database. Il set di dati è una copia in memoria dei dati che deve essere salvata di nuovo nel database, se è stata modificata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 77f6a837fcc88c7154978e8031b17febaa0fcd39
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436055"
---
# <a name="save-data-back-to-the-database"></a>Salvare i dati di nuovo nel database

Il set di dati è una copia in memoria dei dati. Se si modificano i dati, è consigliabile salvare di nuovo le modifiche nel database. Questa operazione viene eseguita in uno dei tre modi seguenti:

- Chiamando uno dei `Update` metodi di un TableAdapter

- Chiamando uno dei `DBDirect` metodi dell'oggetto TableAdapter

- Chiamando il `UpdateAll` metodo sul TableAdapterManager generato automaticamente da Visual Studio quando il set di dati contiene tabelle correlate ad altre tabelle nel set di dati

Quando si associano le tabelle del set di dati ai controlli in una pagina di Windows Form o XAML, l'architettura data binding esegue tutte le operazioni.

Se si ha familiarità con gli oggetti TableAdapter, è possibile passare direttamente a uno di questi argomenti:

|Argomento|Descrizione|
|-----------|-----------------|
|[Inserire nuovi record in un database](../data-tools/insert-new-records-into-a-database.md)|Come eseguire aggiornamenti e inserimenti usando oggetti TableAdapter o oggetti Command|
|[Aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Come eseguire gli aggiornamenti con i TableAdapter|
|[Aggiornamento gerarchico](../data-tools/hierarchical-update.md)|Come eseguire gli aggiornamenti da un set di dati con due o più tabelle correlate|
|[Gestire un'eccezione di concorrenza](../data-tools/handle-a-concurrency-exception.md)|Come gestire le eccezioni quando due utenti tentano di modificare contemporaneamente gli stessi dati in un database|
|[Procedura: salvare dati utilizzando una transazione](../data-tools/save-data-by-using-a-transaction.md)|Come salvare i dati in una transazione utilizzando il sistema. Spazio dei nomi Transactions e oggetto TransactionScope|
|[Salvare i dati in una transazione](../data-tools/save-data-in-a-transaction.md)|Procedura dettagliata che consente di creare un Windows Forms Application per illustrare il salvataggio dei dati in un database all'interno di una transazione|
|[Salvare dati in un database (a più tabelle)](../data-tools/save-data-to-a-database-multiple-tables.md)|Come modificare i record e salvare di nuovo le modifiche in più tabelle nel database|
|[Salvare dati da un oggetto in un database](../data-tools/save-data-from-an-object-to-a-database.md)|Come passare dati da un oggetto che non si trova in un DataSet a un database usando un metodo DbDirect di TableAdapter|
|[Salvare dati con i metodi DBDirect di TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Come utilizzare il TableAdapter per inviare query SQL direttamente al database|
|[Salvare un set di dati come XML](../data-tools/save-a-dataset-as-xml.md)|Come salvare un set di dati in un documento XML|

## <a name="two-stage-updates"></a>Aggiornamenti in due fasi

L'aggiornamento di un'origine dati è un processo in due passaggi. Il primo passaggio consiste nell'aggiornare il set di dati con i nuovi record, i record modificati o i record eliminati. Se l'applicazione non invia mai le modifiche all'origine dati, l'aggiornamento verrà terminato.

Se si inviano di nuovo le modifiche al database, è necessario eseguire un secondo passaggio. Se non si utilizzano controlli con associazione a dati, è necessario chiamare manualmente il `Update` metodo dello stesso TableAdapter (o adattatore dati) utilizzato per popolare il set di dati. Tuttavia, è anche possibile usare adattatori diversi, ad esempio per spostare i dati da un'origine dati a un'altra o per aggiornare più origini dati. Se non si usa data binding e si salvano le modifiche per le tabelle correlate, è necessario creare manualmente un'istanza di una variabile della classe generata automaticamente `TableAdapterManager` , quindi chiamare il relativo `UpdateAll` metodo.

![Diagramma concettuale degli aggiornamenti dei set di dati](../data-tools/media/vbdatasetupdates.gif)

Un set di dati contiene raccolte di tabelle che contengono una raccolta di righe. Se si intende aggiornare un'origine dati sottostante in un secondo momento, è necessario utilizzare i metodi della `DataTable.DataRowCollection` proprietà durante l'aggiunta o la rimozione di righe. Tali metodi eseguono il rilevamento delle modifiche necessario per l'aggiornamento dell'origine dati. Se si chiama la `RemoveAt` raccolta sulla proprietà Rows, l'eliminazione non verrà comunicata al database.

## <a name="merge-datasets"></a>Unisci set di impostazioni

È possibile aggiornare il contenuto di un *set di dati unendolo* a un altro set di dati. Ciò comporta la copia del contenuto di un set di dati di *origine* nel set di dati chiamante (denominato set di dati di *destinazione* ). Quando si uniscono i set di dati, i nuovi record nel set di dati di origine vengono aggiunti al set di dati di destinazione. Inoltre, le colonne aggiuntive nel set di dati di origine vengono aggiunte al set di dati di destinazione. L'Unione dei set di dati è utile quando si dispone di un set di dati locale e si ottiene un secondo set di dati da un'altra applicazione. È utile anche quando si ottiene un secondo set di dati da un componente, ad esempio un servizio Web XML, o quando è necessario integrare dati da più set di dati.

Quando si uniscono set di dati, è possibile passare un argomento booleano ( `preserveChanges` ) che indica al <xref:System.Data.DataSet.Merge%2A> metodo se mantenere le modifiche esistenti nel set di dati di destinazione. Poiché i set di dati gestiscono più versioni dei record, è importante tenere presente che è in corso il merge di più di una versione dei record. La tabella seguente illustra come viene eseguito il merge di un record in due set di dati:

|DataRowVersion|DataSet di destinazione|Set di dati di origine|
| - | - | - |
|Originale|James Wilson|James C. Wilson|
|Corrente|Jim Wilson|James C. Wilson|

Chiamando il <xref:System.Data.DataSet.Merge%2A> metodo nella tabella precedente con i `preserveChanges=false targetDataset.Merge(sourceDataset)` risultati seguenti:

|DataRowVersion|DataSet di destinazione|Set di dati di origine|
| - | - | - |
|Originale|James C. Wilson|James C. Wilson|
|Corrente|James C. Wilson|James C. Wilson|

La chiamata al <xref:System.Data.DataSet.Merge%2A> metodo con `preserveChanges = true targetDataset.Merge(sourceDataset, true)` genera i dati seguenti:

|DataRowVersion|DataSet di destinazione|Set di dati di origine|
| - | - | - |
|Originale|James C. Wilson|James C. Wilson|
|Corrente|Jim Wilson|James C. Wilson|

> [!CAUTION]
> Nello `preserveChanges = true` scenario, se il <xref:System.Data.DataSet.RejectChanges%2A> metodo viene chiamato su un record nel set di dati di destinazione, viene ripristinato il valore originale del set di dati di *origine* . Ciò significa che se si tenta di aggiornare l'origine dati originale con il set di dati di destinazione, potrebbe non essere possibile trovare la riga originale da aggiornare. È possibile impedire una violazione della concorrenza compilando un altro set di dati con i record aggiornati dall'origine dati e quindi eseguendo un'operazione di merge per impedire una violazione della concorrenza. Una violazione della concorrenza si verifica quando un altro utente modifica un record nell'origine dati dopo che il set di dati è stato compilato.

## <a name="update-constraints"></a>Aggiornare i vincoli

Per apportare modifiche a una riga di dati esistente, aggiungere o aggiornare i dati nelle singole colonne. Se il set di dati contiene vincoli, ad esempio chiavi esterne o vincoli non nullable, è possibile che il record possa essere temporaneamente in uno stato di errore durante l'aggiornamento. In altre termini, può trovarsi in uno stato di errore dopo aver completato l'aggiornamento di una colonna, ma prima di raggiungere quella successiva.

Per evitare violazioni dei vincoli prematuri, è possibile sospendere temporaneamente i vincoli di aggiornamento. Tale differenza viene usata per due scopi:

- Evita che venga generato un errore dopo aver completato l'aggiornamento di una colonna, ma non aver iniziato ad aggiornarne un altro.

- Impedisce la generazione di determinati eventi di aggiornamento (eventi spesso utilizzati per la convalida).

> [!NOTE]
> In Windows Forms, l'architettura data binding incorporata nel DataGrid sospende il controllo dei vincoli fino a quando lo stato attivo non viene spostato in una riga e non è necessario chiamare in modo esplicito i <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> metodi, o <xref:System.Data.DataRow.CancelEdit%2A> .

I vincoli vengono disabilitati automaticamente quando il <xref:System.Data.DataSet.Merge%2A> metodo viene richiamato su un set di dati. Al termine dell'Unione, se nel set di dati sono presenti vincoli che non possono essere abilitati, <xref:System.Data.ConstraintException> viene generata un'eccezione. In questa situazione, la <xref:System.Data.DataSet.EnforceConstraints%2A> proprietà viene impostata su `false,` e tutte le violazioni dei vincoli devono essere risolte prima di reimpostare la <xref:System.Data.DataSet.EnforceConstraints%2A> proprietà su `true` .

Al termine di un aggiornamento, è possibile riabilitare il controllo dei vincoli, che riabilita anche gli eventi di aggiornamento e li genera.

Per altre informazioni sulla sospensione degli eventi, vedere [disabilitare i vincoli durante il riempimento di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

## <a name="dataset-update-errors"></a>Errori di aggiornamento del set di dati

Quando si aggiorna un record in un set di dati, è possibile che si verifichi un errore. È possibile, ad esempio, scrivere inavvertitamente dati di tipo errato in una colonna o dati troppo lunghi oppure dati con un altro problema di integrità. In alternativa, potrebbero essere presenti controlli di convalida specifici dell'applicazione che possono generare errori personalizzati durante qualsiasi fase di un evento di aggiornamento. Per altre informazioni, vedere [convalidare i dati nei set di dati](../data-tools/validate-data-in-datasets.md).

## <a name="maintain-information-about-changes"></a>Mantenere le informazioni sulle modifiche

Le informazioni sulle modifiche apportate a un set di dati vengono mantenute in due modi: contrassegnando le righe che indicano che sono state modificate ( <xref:System.Data.DataRow.RowState%2A> ) e mantenendo più copie di un record ( <xref:System.Data.DataRowVersion> ). Utilizzando queste informazioni, i processi possono determinare le modifiche apportate al set di dati e possono inviare aggiornamenti appropriati all'origine dati.

### <a name="rowstate-property"></a>RowState (proprietà)

La <xref:System.Data.DataRow.RowState%2A> proprietà di un <xref:System.Data.DataRow> oggetto è un valore che fornisce informazioni sullo stato di una particolare riga di dati.

Nella tabella seguente vengono illustrati in dettaglio i possibili valori dell' <xref:System.Data.DataRowState> enumerazione:

|Valore DataRowState|Descrizione|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|La riga è stata aggiunta come elemento a un <xref:System.Data.DataRowCollection> . Una riga in questo stato non ha una versione originale corrispondente perché non esisteva al momento della chiamata dell'ultimo <xref:System.Data.DataRow.AcceptChanges%2A> metodo.|
|<xref:System.Data.DataRowState.Deleted>|La riga è stata eliminata utilizzando l' <xref:System.Data.DataRow.Delete%2A> oggetto di un <xref:System.Data.DataRow> oggetto.|
|<xref:System.Data.DataRowState.Detached>|La riga è stata creata ma non fa parte di alcun insieme <xref:System.Data.DataRowCollection>. Un <xref:System.Data.DataRow> oggetto si trova in questo stato subito dopo la creazione, prima che sia stato aggiunto a una raccolta e dopo che è stato rimosso da una raccolta.|
|<xref:System.Data.DataRowState.Modified>|Un valore di colonna nella riga è stato modificato in qualche modo.|
|<xref:System.Data.DataRowState.Unchanged>|La riga non è stata modificata dal momento dell'ultima chiamata del metodo <xref:System.Data.DataRow.AcceptChanges%2A>.|

### <a name="datarowversion-enumeration"></a>DataRowVersion (enumerazione)

I set di dati gestiscono più versioni di record. I <xref:System.Data.DataRowVersion> campi vengono utilizzati per recuperare il valore trovato in un <xref:System.Data.DataRow> oggetto utilizzando la <xref:System.Data.DataRow.Item%2A> proprietà o il <xref:System.Data.DataRow.GetChildRows%2A> metodo dell' <xref:System.Data.DataRow> oggetto.

Nella tabella seguente vengono illustrati in dettaglio i possibili valori dell' <xref:System.Data.DataRowVersion> enumerazione:

|Valore di DataRowVersion|Descrizione|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|La versione corrente di un record contiene tutte le modifiche apportate al record dopo la chiamata dell'ultima volta <xref:System.Data.DataRow.AcceptChanges%2A> . Se la riga è stata eliminata, non esiste alcuna versione corrente.|
|<xref:System.Data.DataRowVersion.Default>|Il valore predefinito di un record, come definito dallo schema del set di dati o dall'origine dati.|
|<xref:System.Data.DataRowVersion.Original>|La versione originale di un record è una copia del record, perché è stata completata l'ultima volta in cui è stato eseguito il commit delle modifiche nel set di dati. In pratica, si tratta in genere della versione di un record come letto da un'origine dati.|
|<xref:System.Data.DataRowVersion.Proposed>|Versione proposta di un record disponibile temporaneamente durante l'aggiornamento, ovvero tra il momento in cui è stato chiamato il <xref:System.Data.DataRow.BeginEdit%2A> metodo e il <xref:System.Data.DataRow.EndEdit%2A> metodo. In genere si accede alla versione proposta di un record in un gestore per un evento, ad esempio <xref:System.Data.DataTable.RowChanging> . La chiamata al <xref:System.Data.DataRow.CancelEdit%2A> metodo inverte le modifiche ed elimina la versione proposta della riga di dati.|

Le versioni originale e corrente sono utili quando le informazioni sugli aggiornamenti vengono trasmesse a un'origine dati. In genere, quando un aggiornamento viene inviato all'origine dati, le nuove informazioni per il database sono nella versione corrente di un record. Le informazioni della versione originale vengono usate per individuare il record da aggiornare.

Ad esempio, nel caso in cui la chiave primaria di un record venga modificata, è necessario un modo per individuare il record corretto nell'origine dati per aggiornare le modifiche. Se non esistesse alcuna versione originale, il record verrebbe probabilmente aggiunto all'origine dati, ottenendo non solo in un record indesiderato aggiuntivo, ma in un record non accurato e non aggiornato. Anche le due versioni vengono usate nel controllo della concorrenza. È possibile confrontare la versione originale con un record nell'origine dati per determinare se il record è stato modificato dopo che è stato caricato nel set di dati.

La versione proposta è utile quando è necessario eseguire la convalida prima di eseguire effettivamente il commit delle modifiche nel set di dati.

Anche se i record sono stati modificati, non sono sempre presenti versioni originali o correnti di tale riga. Quando si inserisce una nuova riga nella tabella, non esiste una versione originale, bensì solo una versione corrente. Analogamente, se si elimina una riga chiamando il metodo della tabella `Delete` , esiste una versione originale, ma nessuna versione corrente.

È possibile testare per verificare se esiste una versione specifica di un record eseguendo una query sul metodo di una riga di dati <xref:System.Data.DataRow.HasVersion%2A> . È possibile accedere a entrambe le versioni di un record passando un <xref:System.Data.DataRowVersion> valore di enumerazione come argomento facoltativo quando si richiede il valore di una colonna.

## <a name="get-changed-records"></a>Ottenere record modificati

È prassi comune non aggiornare ogni record in un set di dati. Un utente potrebbe, ad esempio, utilizzare un controllo Windows Forms <xref:System.Windows.Forms.DataGridView> che visualizza molti record. Tuttavia, l'utente potrebbe aggiornare solo alcuni record, eliminarne uno e inserirne uno nuovo. I set di dati e le tabelle di dati forniscono un metodo ( `GetChanges` ) per restituire solo le righe che sono state modificate.

È possibile creare subset di record modificati usando il `GetChanges` metodo della tabella dati ( <xref:System.Data.DataTable.GetChanges%2A> ) o del set di dati ( <xref:System.Data.DataSet.GetChanges%2A> ). Se si chiama il metodo per la tabella dati, viene restituita una copia della tabella con solo i record modificati. Analogamente, se si chiama il metodo sul set di dati, si ottiene un nuovo set di dati con solo i record modificati al suo interno.

`GetChanges` Restituisce tutti i record modificati. Al contrario, passando l'oggetto desiderato <xref:System.Data.DataRowState> come parametro al `GetChanges` metodo, è possibile specificare quale subset di record modificati si desidera: i record appena aggiunti, i record contrassegnati per l'eliminazione, i record scollegati o i record modificati.

Ottenere un subset di record modificati è utile quando si desidera inviare record a un altro componente per l'elaborazione. Anziché inviare l'intero set di dati, è possibile ridurre l'overhead di comunicazione con l'altro componente ottenendo solo i record necessari per il componente.

## <a name="commit-changes-in-the-dataset"></a>Eseguire il commit delle modifiche nel set di dati

Quando vengono apportate modifiche nel set di dati, <xref:System.Data.DataRow.RowState%2A> viene impostata la proprietà delle righe modificate. Le versioni originale e corrente dei record vengono stabilite, gestite e rese disponibili dalla <xref:System.Data.DataRowView.RowVersion%2A> Proprietà. I metadati archiviati nelle proprietà di queste righe modificate sono necessari per l'invio degli aggiornamenti corretti all'origine dati.

Se le modifiche riflettono lo stato corrente dell'origine dati, non è più necessario gestire queste informazioni. In genere, esistono due volte quando il set di dati e la relativa origine sono sincronizzati:

- Subito dopo aver caricato le informazioni nel set di dati, ad esempio quando si leggono i dati dall'origine.

- Dopo aver inviato le modifiche dal set di dati all'origine dati, ma non prima, poiché si perderanno le informazioni sulle modifiche necessarie per inviare le modifiche al database.

È possibile eseguire il commit delle modifiche in sospeso nel DataSet chiamando il <xref:System.Data.DataSet.AcceptChanges%2A> metodo. In genere, <xref:System.Data.DataSet.AcceptChanges%2A> viene chiamato negli orari seguenti:

- Dopo aver caricato il set di dati. Se si carica un set di dati chiamando il metodo di un TableAdapter `Fill` , l'adapter esegue automaticamente il commit delle modifiche. Tuttavia, se si carica un set di dati unendovi un altro set di dati, è necessario eseguire manualmente il commit delle modifiche.

    > [!NOTE]
    > È possibile impedire all'adapter di eseguire automaticamente il commit delle modifiche quando si chiama il metodo impostando `Fill` la `AcceptChangesDuringFill` proprietà dell'adapter su `false` . Se è impostato su `false` , l'oggetto <xref:System.Data.DataRow.RowState%2A> di ogni riga inserita durante il riempimento è impostato su <xref:System.Data.DataRowState.Added> .

- Dopo l'invio delle modifiche apportate al set di dati a un altro processo, ad esempio un servizio Web XML.

    > [!CAUTION]
    > Il commit della modifica in questo modo cancella tutte le informazioni sulle modifiche. Non eseguire il commit delle modifiche fino a quando non vengono completate le operazioni che richiedono che l'applicazione sappia quali modifiche sono state apportate nel set di dati.

Questo metodo consente di eseguire le operazioni seguenti:

- Scrive la versione <xref:System.Data.DataRowVersion.Current> di un record nella relativa <xref:System.Data.DataRowVersion.Original> versione e sovrascrive la versione originale.

- Rimuove tutte le righe in cui la <xref:System.Data.DataRow.RowState%2A> proprietà è impostata su <xref:System.Data.DataRowState.Deleted> .

- Imposta la <xref:System.Data.DataRow.RowState%2A> proprietà di un record su <xref:System.Data.DataRowState.Unchanged> .

Il <xref:System.Data.DataSet.AcceptChanges%2A> metodo è disponibile a tre livelli. È possibile chiamarlo su un <xref:System.Data.DataRow> oggetto per eseguire il commit delle modifiche solo per tale riga. È inoltre possibile chiamarlo su un <xref:System.Data.DataTable> oggetto per eseguire il commit di tutte le righe di una tabella. Infine, è possibile chiamarlo sull' <xref:System.Data.DataSet> oggetto per eseguire il commit di tutte le modifiche in sospeso in tutti i record di tutte le tabelle del set di dati.

Nella tabella seguente vengono descritte le modifiche di cui viene eseguito il commit in base all'oggetto su cui viene chiamato il metodo:

|Metodo|Risultato|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Viene eseguito il commit delle modifiche solo sulla riga specifica.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Viene eseguito il commit delle modifiche in tutte le righe della tabella specifica.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Viene eseguito il commit delle modifiche in tutte le righe di tutte le tabelle del set di dati.|

> [!NOTE]
> Se si carica un set di dati chiamando il metodo di un TableAdapter `Fill` , non è necessario accettare in modo esplicito le modifiche. Per impostazione predefinita, il `Fill` metodo chiama il `AcceptChanges` metodo dopo aver completato il popolamento della tabella di dati.

Un metodo correlato, <xref:System.Data.DataSet.RejectChanges%2A> , Annulla l'effetto delle modifiche copiando <xref:System.Data.DataRowVersion.Original> nuovamente la versione nella <xref:System.Data.DataRowVersion.Current> versione dei record. Viene inoltre impostato il <xref:System.Data.DataRow.RowState%2A> di ogni record di nuovo su <xref:System.Data.DataRowState.Unchanged> .

## <a name="data-validation"></a>Convalida dei dati

Per verificare che i dati nell'applicazione soddisfino i requisiti dei processi a cui viene passato, è spesso necessario aggiungere la convalida. Questo potrebbe comportare la verifica della correttezza di una voce utente in un modulo, la convalida dei dati inviati all'applicazione da un'altra applicazione o anche il controllo delle informazioni calcolate all'interno del componente entro i limiti dell'origine dati e dei requisiti dell'applicazione.

È possibile convalidare i dati in diversi modi:

- Nel livello aziendale, aggiungendo codice all'applicazione per convalidare i dati. Il set di dati è una posizione in cui è possibile eseguire questa operazione. Il set di dati offre alcuni dei vantaggi della convalida back-end, ad esempio la possibilità di convalidare le modifiche in seguito alla modifica dei valori delle colonne e delle righe. Per altre informazioni, vedere [convalidare i dati nei set di dati](../data-tools/validate-data-in-datasets.md).

- Nel livello di presentazione, aggiungendo la convalida ai moduli. Per ulteriori informazioni, vedere [convalida dell'input dell'utente in Windows Forms](/dotnet/framework/winforms/user-input-validation-in-windows-forms).

- Nel back-end dei dati, inviando i dati all'origine dati, ad esempio il database, e consentendogli di accettare o rifiutare i dati. Se si utilizza un database con funzionalità sofisticate per la convalida dei dati e la fornitura di informazioni sugli errori, questo approccio può essere pratico perché è possibile convalidare i dati indipendentemente da dove provengono. Tuttavia, questo approccio potrebbe non soddisfare i requisiti di convalida specifici dell'applicazione. Inoltre, la convalida dei dati da parte dell'origine dati può causare numerosi round trip all'origine dati, a seconda del modo in cui l'applicazione facilita la risoluzione degli errori di convalida generati dal back-end.

   > [!IMPORTANT]
   > Quando si usano i comandi dati con una <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> proprietà impostata su <xref:System.Data.CommandType.Text> , controllare attentamente le informazioni inviate da un client prima di passarle al database. Qualche utente malintenzionato potrebbe tentare di inviare (inserire) istruzioni SQL modificate o aggiuntive, allo scopo di ottenere un accesso non autorizzato o di danneggiare il database. Prima di trasferire l'input dell'utente in un database, verificare sempre che le informazioni siano valide. Quando possibile, è consigliabile utilizzare sempre query con parametri o stored procedure.

## <a name="transmit-updates-to-the-data-source"></a>Trasmettere gli aggiornamenti all'origine dati

Dopo aver apportato le modifiche in un set di dati, è possibile trasmettere le modifiche a un'origine dati. In genere, questa operazione viene eseguita chiamando il `Update` metodo di un TableAdapter (o adattatore dati). Il metodo esegue il ciclo di ogni record in una tabella di dati, determina il tipo di aggiornamento necessario (Update, INSERT o DELETE), se presente, e quindi esegue il comando appropriato.

Come illustrazione del modo in cui vengono eseguiti gli aggiornamenti, si supponga che l'applicazione utilizzi un set di dati che contiene una singola tabella di dati. L'applicazione recupera due righe dal database. Dopo il recupero, la tabella di dati in memoria è simile alla seguente:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

L'applicazione cambia lo stato di Nancy Buchanan in "preferito". In seguito a questa modifica, il valore della <xref:System.Data.DataRow.RowState%2A> proprietà per tale riga viene modificato da <xref:System.Data.DataRowState.Unchanged> a <xref:System.Data.DataRowState.Modified> . Il valore della <xref:System.Data.DataRow.RowState%2A> proprietà per la prima riga rimane <xref:System.Data.DataRowState.Unchanged> . La tabella dati ha ora un aspetto simile al seguente:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

Tramite l'applicazione in uso viene ora chiamato il metodo `Update` per trasmettere il dataset al database. Il metodo esamina ogni riga a turno. Per la prima riga, il metodo non trasmette alcuna istruzione SQL al database perché tale riga non è stata modificata dal momento in cui è stata recuperata in origine dal database.

Per la seconda riga, tuttavia, il `Update` metodo richiama automaticamente il comando dati corretto e lo trasmette al database. La sintassi specifica dell'istruzione SQL dipende dal dialetto di SQL supportato dall'archivio dati sottostante. Tuttavia, le seguenti caratteristiche generali dell'istruzione SQL trasmessa sono degne di Nota:

- L'istruzione SQL trasmessa è un'istruzione UPDATE. L'adapter sa utilizzare un'istruzione UPDATE perché il valore della <xref:System.Data.DataRow.RowState%2A> proprietà è <xref:System.Data.DataRowState.Modified> .

- L'istruzione SQL trasmessa include una clausola WHERE che indica che la destinazione dell'istruzione UPDATE è la riga in cui `CustomerID = 'c400'` . Questa parte dell'istruzione SELECT consente di distinguere la riga di destinazione da tutte le altre perché `CustomerID` è la chiave primaria della tabella di destinazione. Le informazioni per la clausola WHERE sono derivate dalla versione originale del record ( `DataRowVersion.Original` ), nel caso in cui i valori necessari per identificare la riga siano stati modificati.

- L'istruzione SQL trasmessa include la clausola SET per impostare i nuovi valori delle colonne modificate.

   > [!NOTE]
   > Se la proprietà del TableAdapter `UpdateCommand` è stata impostata sul nome di un stored procedure, l'adapter non costruisce un'istruzione SQL. Richiama invece il stored procedure con i parametri appropriati passati.

## <a name="pass-parameters"></a>Passare parametri

In genere si usano i parametri per passare i valori per i record che verranno aggiornati nel database. Quando il metodo del TableAdapter `Update` esegue un'istruzione Update, è necessario specificare i valori dei parametri. Ottiene questi valori dalla `Parameters` raccolta per il comando dati appropriato, in questo caso l' `UpdateCommand` oggetto nel TableAdapter.

Se sono stati usati gli strumenti di Visual Studio per generare un adattatore dati, l' `UpdateCommand` oggetto contiene una raccolta di parametri che corrispondono a ogni segnaposto di parametro nell'istruzione.

La <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> proprietà di ogni parametro punta a una colonna nella tabella dati. Ad esempio, la `SourceColumn` proprietà per i `au_id` `Original_au_id` parametri e viene impostata su qualsiasi colonna della tabella dati contenente l'ID autore. Quando `Update` viene eseguito il metodo dell'adapter, viene letta la colonna Author ID dal record aggiornato e vengono inseriti i valori nell'istruzione.

In un'istruzione UPDATE è necessario specificare sia i nuovi valori (quelli che verranno scritti nel record) sia i valori precedenti, in modo che il record possa trovarsi nel database. Sono pertanto disponibili due parametri per ogni valore: uno per la clausola SET e uno diverso per la clausola WHERE. Entrambi i parametri leggono i dati dal record che viene aggiornato, ma ottengono versioni diverse del valore della colonna in base alla proprietà del parametro <xref:System.Data.SqlClient.SqlParameter.SourceVersion> . Il parametro per la clausola SET ottiene la versione corrente e il parametro della clausola WHERE ottiene la versione originale.

> [!NOTE]
> È inoltre possibile impostare i valori nella `Parameters` raccolta manualmente nel codice, che in genere si esegue in un gestore eventi per l'evento dell'adattatore dati <xref:System.Data.DataTable.RowChanging> .

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Creare e configurare oggetti TableAdapter](create-and-configure-tableadapters.md)
- [Aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Convalidare i dati](validate-data-in-datasets.md)
- [Procedura: aggiunta, modifica ed eliminazione di entità (WCF Data Services)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)
