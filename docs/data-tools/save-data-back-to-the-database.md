---
title: Salvare i dati di nuovo nel database
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: b3bbb8b93eb4b2f0cc1078224118b41caa590df6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966959"
---
# <a name="save-data-back-to-the-database"></a>Salvare i dati di nuovo nel database

Il set di dati è una copia in memoria dei dati. Se si modificano i dati, è consigliabile salvare le modifiche nel database. È procedere in uno dei tre modi:

- Chiamando uno del `Update` metodi di un oggetto TableAdapter

- Chiamando uno dei `DBDirect` metodi dell'oggetto TableAdapter

- Chiamando il `UpdateAll` metodo del componente TableAdapterManager che Visual Studio genera automaticamente quando il set di dati contiene le tabelle correlate ad altre tabelle nel set di dati

Quando si dati associa le tabelle di set di dati a controlli in una pagina XAML o Windows Form, l'architettura di associazione di dati esegue tutte le operazioni necessarie.

Se si ha familiarità con gli oggetti TableAdapter, è possibile passare direttamente a uno degli argomenti seguenti:

|Argomento|Descrizione|
|-----------|-----------------|
|[Inserire nuovi record in un database](../data-tools/insert-new-records-into-a-database.md)|Come eseguire aggiornamenti e inserimenti usando oggetti TableAdapter o un comando|
|[Aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Come eseguire gli aggiornamenti degli oggetti TableAdapter|
|[Aggiornamento gerarchico](../data-tools/hierarchical-update.md)|Come eseguire gli aggiornamenti da un set di dati con due o più tabelle correlate|
|[Gestire un'eccezione di concorrenza](../data-tools/handle-a-concurrency-exception.md)|Come gestire le eccezioni quando due utenti tentano di modificare gli stessi dati in un database nello stesso momento|
|[Procedura: Salvare dati usando una transazione](../data-tools/save-data-by-using-a-transaction.md)|Come salvare i dati in una transazione utilizzando il sistema. Le transazioni dello spazio dei nomi e un oggetto TransactionScope|
|[Salvare i dati in una transazione](../data-tools/save-data-in-a-transaction.md)|Procedura dettagliata che consente di creare un'applicazione Windows Forms per illustrare il salvataggio dei dati a un database all'interno di una transazione|
|[Salvare dati in un database (a più tabelle)](../data-tools/save-data-to-a-database-multiple-tables.md)|Come modificare i record e salvare le modifiche in più tabelle nel database|
|[Salvare dati da un oggetto in un database](../data-tools/save-data-from-an-object-to-a-database.md)|Come passare i dati da un oggetto che non è in un set di dati a un database usando un metodo DbDirect di TableAdapter|
|[PSalvare dati con i metodi DBDirect di TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Come usare l'oggetto TableAdapter per inviare query SQL direttamente al database|
|[Salvare un set di dati come XML](../data-tools/save-a-dataset-as-xml.md)|Come salvare un set di dati in un documento XML|

## <a name="two-stage-updates"></a>Aggiornamenti in due fasi

Aggiornamento di un'origine dati è un processo in due passaggi. Il primo passaggio consiste nell'aggiornare il set di dati con i nuovi record, record modificati o i record eliminati. Se l'applicazione non invia mai le modifiche nuovamente all'origine dati, si è terminato con l'aggiornamento.

Se si inviano le modifiche nel database, un secondo passaggio è obbligatorio. Se non si usa i controlli con associazione a dati, è necessario chiamare manualmente le `Update` metodo dell'oggetto TableAdapter stesso (o adattatore dati di) usato per popolare il set di dati. Tuttavia, è possibile utilizzare anche diverse schede, ad esempio, per spostare i dati da un'origine dati a un altro o per aggiornare più origini dati. Se si non si usa l'associazione dati e si salvano le modifiche per le tabelle correlate, è necessario creare manualmente un'istanza di una variabile di generata automaticamente `TableAdapterManager` classe e quindi chiamare relativo `UpdateAll` (metodo).

![Diagramma concettuale di aggiornamenti di dataset](../data-tools/media/vbdatasetupdates.gif)

Un set di dati contiene insiemi di tabelle che contengono una raccolta di righe. Se si prevede di aggiornare un'origine dati sottostante in un secondo momento, è necessario usare i metodi su di `DataTable.DataRowCollection` proprietà durante l'aggiunta o rimozione di righe. Questi metodi eseguono il rilevamento delle modifiche che è necessario per aggiornare l'origine dati. Se si chiama il `RemoveAt` insieme alla proprietà di righe, l'eliminazione non essere comunicata al database.

## <a name="merge-datasets"></a>I set di dati di tipo merge

È possibile aggiornare il contenuto di un set di dati dal *unione* con un altro set di dati. Ciò comporta la copia il contenuto di un *origine* set di dati in set di dati di chiamata (detto il *destinazione* set di dati). Quando si uniscono i set di dati, vengono aggiunti nuovi record del set di dati di origine per il set di dati di destinazione. Inoltre, le colonne aggiuntive nel set di dati di origine vengono aggiunti al set di dati di destinazione. Unione di set di dati è utile quando si ha un set di dati locale e hanno un secondo set di dati da un'altra applicazione. È inoltre utile quando si riceve un secondo set di dati da un componente, ad esempio un servizio web XML, o quando è necessario integrare dati provenienti da più set di dati.

Quando si uniscono i set di dati, è possibile passare un argomento booleano (`preserveChanges`) che indica il <xref:System.Data.DataSet.Merge%2A> metodo se si desidera mantenere le modifiche esistenti nel set di dati di destinazione. Poiché i set di dati di gestire più versioni di record, è importante tenere presente che viene eseguita l'unione di più versioni dei record. La tabella seguente illustra le modalità di unione di un record in due set di dati:

|DataRowVersion|DataSet di destinazione|Set di dati di origine|
| - | - | - |
|Originale|James Wilson|James C. Wilson|
|Corrente|Jim Wilson|James C. Wilson|

Chiama il <xref:System.Data.DataSet.Merge%2A> metodo nella tabella precedente con `preserveChanges=false targetDataset.Merge(sourceDataset)` comporta i seguenti dati:

|DataRowVersion|DataSet di destinazione|Set di dati di origine|
| - | - | - |
|Originale|James C. Wilson|James C. Wilson|
|Corrente|James C. Wilson|James C. Wilson|

Chiama il <xref:System.Data.DataSet.Merge%2A> metodo con `preserveChanges = true targetDataset.Merge(sourceDataset, true)` comporta i seguenti dati:

|DataRowVersion|DataSet di destinazione|Set di dati di origine|
| - | - | - |
|Originale|James C. Wilson|James C. Wilson|
|Corrente|Jim Wilson|James C. Wilson|

> [!CAUTION]
> Nel `preserveChanges = true` scenario, se il <xref:System.Data.DataSet.RejectChanges%2A> metodo viene chiamato su un record nel set di dati di destinazione, quindi viene ripristinato il dati originali dalle *origine* set di dati. Ciò significa che, se si tenta di aggiornare l'origine dati originale con il set di dati di destinazione, potrebbe non essere in grado di trovare la riga originale per l'aggiornamento. È possibile evitare una violazione della concorrenza per la compilazione di un altro set di dati con i record aggiornati dall'origine dati e l'esecuzione di un'unione nell'indice per evitare una violazione della concorrenza. (Una violazione della concorrenza si verifica quando un altro utente modifica un record nell'origine dati dopo che il set di dati è stato compilato.)

## <a name="update-constraints"></a>Aggiornare i vincoli

Per apportare modifiche a una riga di dati esistente, aggiungere o aggiornare i dati in singole colonne. Se il set di dati contiene i vincoli (ad esempio le chiavi esterne o i vincoli non nullable), è possibile che il record può essere temporaneamente in uno stato di errore perché venga aggiornata. Vale a dire, può essere in stato di errore dopo aver completato l'aggiornamento di una colonna, ma prima di procedere con quello successivo.

Per impedire violazioni dei vincoli prematura è possibile sospendere temporaneamente i vincoli di aggiornamento. Ciò ha due scopi:

- Un errore impedisce che venga generata dopo aver completato l'aggiornamento di una colonna, ma non hanno avviato l'aggiornamento a un altro.

- Evita che determinati aggiornamenti gli eventi vengano generati (gli eventi che vengono spesso usati per la convalida).

> [!NOTE]
> In Windows Form, l'architettura di associazione dati è incorporata nel datagrid controllo vincoli sospeso finché lo stato attivo viene spostato all'esterno di una riga e non è necessario chiamare in modo esplicito il <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, o <xref:System.Data.DataRow.CancelEdit%2A> metodi.

I vincoli sono automaticamente disabilitata quando il <xref:System.Data.DataSet.Merge%2A> metodo viene richiamato su un set di dati. Quando il merge è completo, se sono presenti eventuali vincoli per il set di dati che non può essere abilitato, un <xref:System.Data.ConstraintException> viene generata un'eccezione. In questo caso, il <xref:System.Data.DataSet.EnforceConstraints%2A> è impostata su `false,` e tutte le violazioni di vincolo devono essere risolti prima di reimpostare le <xref:System.Data.DataSet.EnforceConstraints%2A> proprietà `true`.

Dopo aver completato un aggiornamento, è possibile riabilitare il controllo dei vincoli, che anche abilita nuovamente gli eventi di aggiornamento e li genera.

Per altre informazioni sulla sospensione di eventi, vedere [disattivare i vincoli durante il riempimento di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

## <a name="dataset-update-errors"></a>Errori di aggiornamento di set di dati

Quando si aggiorna un record in un set di dati, sussiste la possibilità di un errore. Ad esempio, si potrebbe scrivere inavvertitamente i dati di tipo non corretto a una colonna, o dati che sono troppo lunghi o dati che dispone di altri problemi di integrità. In alternativa, è possibile controlli di convalida specifiche dell'applicazione che possono generare errori personalizzati in qualsiasi fase di un evento di aggiornamento. Per altre informazioni, vedere [convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md).

## <a name="maintain-information-about-changes"></a>Gestire le informazioni relative alle modifiche

Informazioni sulle modifiche in un set di dati viene mantenute in due modi: contrassegnando le righe che indicano che vengono modificati (<xref:System.Data.DataRow.RowState%2A>) e mantenendo più copie di un record (<xref:System.Data.DataRowVersion>). Usando queste informazioni, i processi possono determinare cosa è cambiato nel set di dati e possono inviare gli aggiornamenti appropriati per l'origine dati.

### <a name="rowstate-property"></a>Proprietà di RowState

Il <xref:System.Data.DataRow.RowState%2A> proprietà di un <xref:System.Data.DataRow> oggetto è un valore che fornisce informazioni sullo stato di una particolare riga di dati.

La tabella seguente illustra i valori possibili del <xref:System.Data.DataRowState> enumerazione:

|Valore DataRowState|Descrizione|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|La riga è stata aggiunta come elemento a un <xref:System.Data.DataRowCollection>. (Una riga in questo stato è privo di una versione originale corrispondente in quanto non esisteva quando l'ultimo <xref:System.Data.DataRow.AcceptChanges%2A> metodo è stato chiamato).|
|<xref:System.Data.DataRowState.Deleted>|La riga è stata eliminata tramite il <xref:System.Data.DataRow.Delete%2A> di un <xref:System.Data.DataRow> oggetto.|
|<xref:System.Data.DataRowState.Detached>|La riga è stata creata ma non fa parte di qualsiasi <xref:System.Data.DataRowCollection>. Oggetto <xref:System.Data.DataRow> oggetto è in questo stato subito dopo che è stato creato in precedenza è stato aggiunto a una raccolta e dopo che è stato rimosso da una raccolta.|
|<xref:System.Data.DataRowState.Modified>|Un valore di colonna nella riga è stato modificato in qualche modo.|
|<xref:System.Data.DataRowState.Unchanged>|La riga è stata modificata in non <xref:System.Data.DataRow.AcceptChanges%2A> ultima chiamata al metodo.|

### <a name="datarowversion-enumeration"></a>DataRowVersion (enumerazione)

Set di dati di mantenere più versioni di record. Il <xref:System.Data.DataRowVersion> i campi vengono usati quando il recupero del valore trovato un <xref:System.Data.DataRow> usando la <xref:System.Data.DataRow.Item%2A> proprietà o il <xref:System.Data.DataRow.GetChildRows%2A> metodo del <xref:System.Data.DataRow> oggetto.

La tabella seguente illustra i valori possibili del <xref:System.Data.DataRowVersion> enumerazione:

|Valore di DataRowVersion|Descrizione|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|La versione corrente di un record contiene tutte le modifiche che sono state eseguite sul record dall'ultima volta <xref:System.Data.DataRow.AcceptChanges%2A> è stato chiamato. Se la riga è stata eliminata, non vi è alcuna versione corrente.|
|<xref:System.Data.DataRowVersion.Default>|Il valore predefinito di un record, come definito dall'origine dati o lo schema dei set di dati.|
|<xref:System.Data.DataRowVersion.Original>|La versione originale di un record è una copia del record com'era che l'ultima applicazione delle modifiche sono state salvate nel set di dati. In pratica, in genere si tratta della versione di un record come già letto da un'origine dati.|
|<xref:System.Data.DataRowVersion.Proposed>|La versione prevista di un record che è disponibile temporaneamente mentre è ancora in corso un aggiornamento, vale a dire, tra il momento in cui è stato chiamato il <xref:System.Data.DataRow.BeginEdit%2A> (metodo) e il <xref:System.Data.DataRow.EndEdit%2A> (metodo). In genere si accede alla versione proposta di un record in un gestore per un evento, ad esempio <xref:System.Data.DataTable.RowChanging>. Richiamare il <xref:System.Data.DataRow.CancelEdit%2A> metodo inverte le modifiche ed elimina la versione della riga di dati proposta.|

Le versioni originali e correnti sono utili quando le informazioni di aggiornamento viene trasmesso a un'origine dati. In genere, quando un aggiornamento viene inviato all'origine dati, le nuove informazioni per il database sono nella versione corrente di un record. Le informazioni dalla versione originale viene utilizzate per individuare il record da aggiornare.

Ad esempio, nel caso in cui è stata modificata la chiave primaria di un record, è necessario un modo per individuare il record corretto nell'origine dati per aggiornare le modifiche. Se non esistesse alcuna versione originale, quindi il record molto probabilmente verrebbe aggiunto all'origine dati, causando non solo in un record aggiuntivi indesiderato, ma in un record che sia inaccurate sia aggiornata. Le due versioni vengono anche usate nel controllo della concorrenza. È possibile confrontare la versione originale usando un record nell'origine dati per determinare se il record è stato modificato dopo il caricamento nel set di dati.

La versione prevista è utile quando devi eseguire la convalida prima effettivamente il commit delle modifiche al set di dati.

Anche se i record sono stati modificati, non esistono sempre originale o in atto le versioni di riga. Quando si inserisce una nuova riga nella tabella, è presente una versione originale, solo una versione corrente. Analogamente, se si elimina una riga chiamando la tabella `Delete` metodo, è una versione originale, ma nessuna versione corrente.

È possibile verificare l'esistenza di una versione specifica di un record eseguendo una riga di dati <xref:System.Data.DataRow.HasVersion%2A> (metodo). È possibile accedere a entrambe le versioni di un record passando un <xref:System.Data.DataRowVersion> valore di enumerazione come argomento facoltativo quando si richiede il valore di una colonna.

## <a name="get-changed-records"></a>Ottenere i record modificati

È pratica comune di non aggiornare tutti i record in un set di dati. Ad esempio, un utente lavora con un controllo Windows Form <xref:System.Windows.Forms.DataGridView> controllo che visualizza numero di record. L'utente potrebbe, tuttavia, solo alcuni record di aggiornamento, eliminarne uno e inserire una nuova. I set di dati e le tabelle dati offrono un metodo (`GetChanges`) per restituire solo le righe che sono state modificate.

È possibile creare subset di record modificati utilizzando il `GetChanges` metodo per la tabella di dati (<xref:System.Data.DataTable.GetChanges%2A>) o del set di dati (<xref:System.Data.DataSet.GetChanges%2A>) stesso. Se si chiama il metodo per la tabella di dati, restituisce una copia della tabella che contiene solo i record modificati. Analogamente, se si chiama il metodo sul set di dati, si ottiene un nuovo set di dati contenente solo i record modificati in esso.

`GetChanges` Restituisce tutti i record modificati da solo. Al contrario, passando il valore desiderato <xref:System.Data.DataRowState> come parametro per il `GetChanges` metodo, è possibile specificare quale subset di record modificati desiderato: aggiunto record, record contrassegnati per l'eliminazione, scollegare i record nuovi o modificati record.

Ottenere un subset di record modificati è utile quando si desidera inviare i record a un altro componente per l'elaborazione. Anziché inviare l'intero set di dati, è possibile ridurre l'overhead di comunicazione con l'altro componente tramite il recupero solo i record che il componente.

## <a name="commit-changes-in-the-dataset"></a>Eseguire il commit delle modifiche nel set di dati

Quando vengono apportate modifiche nel set di dati, il <xref:System.Data.DataRow.RowState%2A> delle righe modificate viene impostata. Le versioni originali e correnti dei record sono stabilite, gestite e reso disponibile al Licenziatario dal <xref:System.Data.DataRowView.RowVersion%2A> proprietà. I metadati archiviati nelle proprietà di queste righe modificate sono necessari per inviare gli aggiornamenti corretti nell'origine dati.

Se le modifiche rifletteranno lo stato corrente dell'origine dati, non è più necessario mantenere queste informazioni. In genere, sono disponibili due volte quando il set di dati e la relativa origine sono sincronizzati:

- Subito dopo aver caricato le informazioni in set di dati, ad esempio quando leggere i dati dall'origine.

- Dopo l'invio delle modifiche dal set di dati all'origine dati (ma non prima, perché verranno perse le informazioni sulle modifiche necessarie per inviare le modifiche apportate al database).

È possibile applicare le modifiche in sospeso per il set di dati chiamando il <xref:System.Data.DataSet.AcceptChanges%2A> (metodo). In genere, <xref:System.Data.DataSet.AcceptChanges%2A> viene chiamato nei momenti seguenti:

- Dopo aver caricato il set di dati. Se si carica un set di dati chiamando un oggetto TableAdapter `Fill` (metodo), quindi l'adapter eseguirà automaticamente il commit delle modifiche per l'utente. Tuttavia, se si carica un set di dati mediante l'unione di un altro set di dati al suo interno, quindi è necessario salvare le modifiche manualmente.

    > [!NOTE]
    > È possibile impedire che l'adapter automaticamente il commit delle modifiche quando si chiama il `Fill` metodo impostando il `AcceptChangesDuringFill` proprietà dell'adapter `false`. Se è impostato su `false`, il <xref:System.Data.DataRow.RowState%2A> di ogni riga viene inserita durante la compilazione è impostato su <xref:System.Data.DataRowState.Added>.

- Dopo l'invio di set di dati modifiche a un altro processo, ad esempio un servizio web XML.

    > [!CAUTION]
    > Eseguire il commit della modifica in questo modo consente di cancellare le informazioni di modifica. Eseguire operazioni non il commit delle modifiche fino a dopo aver fine esecuzione di operazioni che richiedono che l'applicazione per conoscere quali modifiche sono state apportate nel set di dati.

Questo metodo vengono effettuate le seguenti:

- Scrive il <xref:System.Data.DataRowVersion.Current> versione di un record nel relativo <xref:System.Data.DataRowVersion.Original> versione e sovrascrive la versione originale.

- Rimuove tutte le righe in cui il <xref:System.Data.DataRow.RowState%2A> è impostata su <xref:System.Data.DataRowState.Deleted>.

- Imposta il <xref:System.Data.DataRow.RowState%2A> proprietà di un record a <xref:System.Data.DataRowState.Unchanged>.

Il <xref:System.Data.DataSet.AcceptChanges%2A> metodo è disponibile in tre livelli. È possibile chiamarlo in un <xref:System.Data.DataRow> oggetto ai commit modificata solo tale riga. È possibile anche chiamare su un <xref:System.Data.DataTable> oggetto per eseguire il commit di tutte le righe in una tabella. Infine, è possibile chiamare sul <xref:System.Data.DataSet> oggetto per eseguire il commit di tutte le modifiche in sospeso in tutti i record di tutte le tabelle del set di dati.

La tabella seguente descrive quali modifiche vengono eseguito il commit in base quale oggetto che viene chiamato il metodo su:

|Metodo|Risultato|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Le modifiche vengono applicate solo la riga specifica.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Vengono eseguito il commit delle modifiche in tutte le righe della tabella specifica.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Le modifiche vengono applicate a tutte le righe in tutte le tabelle del set di dati.|

> [!NOTE]
> Se si carica un set di dati chiamando un oggetto TableAdapter `Fill` metodo, non è necessario accettare in modo esplicito le modifiche. Per impostazione predefinita, il `Fill` chiamate al metodo il `AcceptChanges` metodo al termine dell'inserimento dei dati nella tabella.

Un metodo correlato <xref:System.Data.DataSet.RejectChanges%2A>, Annulla l'effetto delle modifiche tramite la copia il <xref:System.Data.DataRowVersion.Original> versione nuovamente nel <xref:System.Data.DataRowVersion.Current> dei record versione. Imposta anche il <xref:System.Data.DataRow.RowState%2A> di ogni record ripristinandone <xref:System.Data.DataRowState.Unchanged>.

## <a name="data-validation"></a>Convalida dei dati

Per verificare che i dati nell'applicazione in uso soddisfino i requisiti dei processi che viene passata a, spesso è necessario aggiungere la convalida. Questo potrebbe comportare verificando che la voce dell'utente in un form sia corretta, la convalida dei dati che viene inviati all'applicazione da un'altra applicazione o controllare anche che le informazioni che viene calcolate all'interno del componente sia compreso nell'ambito dei vincoli dell'origine dati e i requisiti dell'applicazione.

È possibile convalidare i dati in diversi modi:

- Nel livello business, tramite l'aggiunta di codice all'applicazione per convalidare i dati. Il set di dati è un'unica posizione è possibile farlo. Il set di dati sono disponibili alcuni dei vantaggi della convalida di back-end, ad esempio la possibilità di convalidare le modifiche che stanno modificando i valori di colonna e riga. Per altre informazioni, vedere [convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md).

- Nel livello di presentazione, mediante l'aggiunta di convalida a un form. Per altre informazioni, vedere [convalida in Windows Form dell'input utente](/dotnet/framework/winforms/user-input-validation-in-windows-forms).

- Nei dati di back-end, inviando i dati all'origine dati, ad esempio, il database e in modo che possa accettare o rifiutare i dati. Se si lavora con un database che dispone di funzionalità per la convalida dei dati e fornendo informazioni sull'errore complesse, può trattarsi un pratico approccio in quanto è possibile convalidare i dati indipendentemente da dove provenga da. Tuttavia, questo approccio potrebbe non soddisfare requisiti di convalida specifiche dell'applicazione. Inoltre, che l'origine dati di convalida dei dati può comportare molti round trip all'origine dati, a seconda del modo in cui l'applicazione facilita la risoluzione degli errori di convalida generato dal back-end.

   > [!IMPORTANT]
   > Quando si usano i comandi di dati con un <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> proprietà che è impostato su <xref:System.Data.CommandType.Text>, attentamente controllare le informazioni inviate da un client prima di passarlo al database. Qualche utente malintenzionato potrebbe tentare di inviare (inserire) istruzioni SQL modificate o aggiuntive, allo scopo di ottenere un accesso non autorizzato o di danneggiare il database. Prima di trasferire input dell'utente a un database, verificare sempre che le informazioni siano valide. È consigliabile utilizzare sempre query con parametri o stored procedure, laddove possibile.

## <a name="transmit-updates-to-the-data-source"></a>Trasmettere gli aggiornamenti all'origine dati

Dopo aver apportate le modifiche in un set di dati, è possibile trasmettere le modifiche a un'origine dati. In genere, eseguire questa operazione chiamando il `Update` metodo di un oggetto TableAdapter (o un adattatore dati). Il metodo scorre ciascun record in una tabella di dati determina il tipo di aggiornamento è obbligatorio (aggiornare, inserire o eliminare), se presente, e quindi esegue il comando appropriato.

Come dimostrazione del modo in cui gli aggiornamenti vengono eseguiti, si supponga che l'applicazione usa un set di dati che contiene una singola tabella dati. L'applicazione recupera due righe dal database. Dopo il recupero, la tabella di dati in memoria è simile al seguente:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

Lo stato di Nancy Buchanan applicazione modificato in "Preferiti". In seguito a questa modifica, il valore della <xref:System.Data.DataRow.RowState%2A> proprietà per la riga viene cambiata da <xref:System.Data.DataRowState.Unchanged> a <xref:System.Data.DataRowState.Modified>. Il valore della <xref:System.Data.DataRow.RowState%2A> proprietà per la prima riga rimane <xref:System.Data.DataRowState.Unchanged>. La tabella di dati sarà simile al seguente:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

Tramite l'applicazione in uso viene ora chiamato il metodo `Update` per trasmettere il dataset al database. Il metodo esamina ogni riga, a sua volta. Per la prima riga, il metodo non trasmette nessuna istruzione SQL al database perché tale riga non è stato modificato dopo il suo recupero originariamente dal database.

Per la seconda riga, tuttavia, il `Update` metodo automaticamente richiama il comando di correggere i dati e li trasmette al database. La sintassi dell'istruzione SQL specifica dipende dal dialetto di SQL supportata dall'archivio dati sottostante. Tuttavia, le caratteristiche generali seguenti di istruzione SQL sono degni di nota:

- Istruzione SQL è un'istruzione UPDATE. L'adapter è in grado di utilizzare un'istruzione UPDATE, perché il valore della <xref:System.Data.DataRow.RowState%2A> è di proprietà <xref:System.Data.DataRowState.Modified>.

- Istruzione SQL include una clausola WHERE che indica che la destinazione dell'istruzione UPDATE è la riga in cui `CustomerID = 'c400'`. Questa parte dell'istruzione SELECT distingue la riga di destinazione da tutti gli altri, perché il `CustomerID` è la chiave primaria della tabella di destinazione. Le informazioni per la clausola WHERE è derivata dalla versione originale del record (`DataRowVersion.Original`), nel caso in cui sono stati modificati i valori necessari per identificare la riga.

- Istruzione SQL include la clausola SET per impostare i nuovi valori delle colonne modificate.

   > [!NOTE]
   > Se il TableAdapter `UpdateCommand` proprietà è stata impostata sul nome di una stored procedure, l'adapter non ne crea un'istruzione SQL. Al contrario, richiama la stored procedure con i parametri appropriati passati.

## <a name="pass-parameters"></a>Passare i parametri

È in genere usare parametri per passare i valori per i record che stanno per essere aggiornata nel database. Quando il TableAdapter `Update` metodo esegue un'istruzione UPDATE, è necessario specificare i valori di parametro. Ottiene questi valori dal `Parameters` raccolta per il comando di dati appropriato, in questo caso, il `UpdateCommand` oggetto nell'oggetto TableAdapter.

Se è stato utilizzato gli strumenti di Visual Studio per generare un adattatore di dati, il `UpdateCommand` oggetto contiene una raccolta di parametri che corrispondono a ogni segnaposto per il parametro nell'istruzione.

Il <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> proprietà di ogni parametro fa riferimento a una colonna nella tabella dati. Ad esempio, il `SourceColumn` proprietà per il `au_id` e `Original_au_id` parametri è impostato su qualsiasi colonna nella tabella di dati contiene l'id dell'autore. Quando l'adapter `Update` viene eseguito il metodo legge l'autore colonna id dal record che viene aggiornato e vengono inseriti i valori nell'istruzione.

In un'istruzione UPDATE, è necessario specificare entrambi i valori nuovi (quelli che verrà scritto il record), nonché i vecchi valori (in modo che il record può trovarsi nel database). Sono presenti, pertanto, due parametri per ogni valore: uno per la clausola SET e un altro per la clausola WHERE. Entrambi i parametri di leggere i dati del record da aggiornare, ma si rivelano problematici versioni diverse del valore della colonna in base al parametro <xref:System.Data.SqlClient.SqlParameter.SourceVersion> proprietà. Il parametro per la clausola SET Ottiene la versione corrente e il parametro per la clausola WHERE recupera la versione originale.

> [!NOTE]
> È anche possibile impostare i valori `Parameters` raccolta manualmente nel codice, che in genere si farebbe in un gestore eventi per l'adattatore dati di <xref:System.Data.DataTable.RowChanging> evento.

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Creare e configurare oggetti TableAdapter](create-and-configure-tableadapters.md)
- [Aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Convalidare i dati](validate-data-in-datasets.md)
- [Procedura: Aggiungere, modificare ed eliminare entità (WCF data services)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)