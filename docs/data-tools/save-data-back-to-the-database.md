---
title: Salvare i dati di nuovo nel database
description: Usare gli strumenti di DataSet per salvare di nuovo i dati nel database. Il set di dati è una copia in memoria dei dati che devono essere salvati di nuovo nel database se vengono modificati.
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 36140f928450cbb8ef498ae1edb490b4c2a32eae
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631229"
---
# <a name="save-data-back-to-the-database"></a>Salvare i dati di nuovo nel database

Il set di dati è una copia in memoria dei dati. Se si modificano i dati, è consigliabile salvare di nuovo le modifiche nel database. A tale scopo, è possibile procedere in uno dei tre modi seguenti:

- Chiamando uno dei metodi `Update` di un oggetto TableAdapter

- Chiamando uno dei `DBDirect` metodi del TableAdapter

- Chiamando il metodo sull'oggetto TableAdapterManager che Visual Studio genera automaticamente quando il set di dati contiene tabelle correlate ad altre `UpdateAll` tabelle nel set di dati

Quando si associano dati alle tabelle del set di dati ai controlli in un form Windows o in una pagina XAML, l'architettura data binding esegue automaticamente tutte le operazioni.

Se si ha familiarità con gli oggetti TableAdapter, è possibile passare direttamente a uno di questi argomenti:

|Argomento|Descrizione|
|-----------|-----------------|
|[Inserire nuovi record in un database](../data-tools/insert-new-records-into-a-database.md)|Come eseguire aggiornamenti e inserimenti usando oggetti TableAdapter o Command|
|[Aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Come eseguire aggiornamenti con gli oggetti TableAdapter|
|[Aggiornamento gerarchico](../data-tools/hierarchical-update.md)|Come eseguire aggiornamenti da un set di dati con due o più tabelle correlate|
|[Gestire un'eccezione di concorrenza](../data-tools/handle-a-concurrency-exception.md)|Come gestire le eccezioni quando due utenti tentano di modificare contemporaneamente gli stessi dati in un database|
|[Procedura: Salvare dati tramite una transazione](../data-tools/save-data-by-using-a-transaction.md)|Come salvare i dati in una transazione usando il sistema. Spazio dei nomi Transactions e oggetto TransactionScope|
|[Salvare i dati in una transazione](../data-tools/save-data-in-a-transaction.md)|Procedura dettagliata che crea un'applicazione Windows Forms per illustrare il salvataggio di dati in un database all'interno di una transazione|
|[Salvare dati in un database (a più tabelle)](../data-tools/save-data-to-a-database-multiple-tables.md)|Come modificare i record e salvare le modifiche in più tabelle nel database|
|[Salvare dati da un oggetto in un database](../data-tools/save-data-from-an-object-to-a-database.md)|Come passare dati da un oggetto che non si trova in un set di dati a un database usando un metodo DbDirect di TableAdapter|
|[Salvare dati con i metodi DBDirect di TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Come usare il TableAdapter per inviare SQL query direttamente al database|
|[Salvare un set di dati come XML](../data-tools/save-a-dataset-as-xml.md)|Come salvare un set di dati in un documento XML|

## <a name="two-stage-updates"></a>Aggiornamenti in due fasi

L'aggiornamento di un'origine dati è un processo in due passaggi. Il primo passaggio consiste nell'aggiornare il set di dati con nuovi record, record modificati o record eliminati. Se l'applicazione non invia mai tali modifiche all'origine dati, l'aggiornamento è terminato.

Se si inviano le modifiche al database, è necessario un secondo passaggio. Se non si usano controlli associati a dati, è necessario chiamare manualmente il metodo dello stesso TableAdapter (o adattatore dati) usato per popolare il `Update` set di dati. Tuttavia, è anche possibile usare adattatori diversi, ad esempio per spostare i dati da un'origine dati a un'altra o per aggiornare più origini dati. Se non si usa data binding e si salvano le modifiche per le tabelle correlate, è necessario creare manualmente un'istanza di una variabile della classe generata automaticamente e quindi chiamarne `TableAdapterManager` il `UpdateAll` metodo .

![Diagramma concettuale degli aggiornamenti dei set di dati](../data-tools/media/vbdatasetupdates.gif)

Un set di dati contiene raccolte di tabelle, che contengono raccolte di righe. Se si intende aggiornare un'origine dati sottostante in un secondo momento, è necessario usare i metodi nella proprietà quando si `DataTable.DataRowCollection` aggiungono o rimuovono righe. Questi metodi eseguono il rilevamento delle modifiche necessario per aggiornare l'origine dati. Se si chiama `RemoveAt` la raccolta sulla proprietà Rows, l'eliminazione non verrà comunicata al database.

## <a name="merge-datasets"></a>Unire set di dati

È possibile aggiornare il contenuto di un set di dati *unerlo* a un altro set di dati. Ciò comporta la copia del contenuto di un set *di dati* di origine nel set di dati chiamante (detto set di *dati di* destinazione). Quando si uniscono set di dati, i nuovi record nel set di dati di origine vengono aggiunti al set di dati di destinazione. Inoltre, al set di dati di destinazione vengono aggiunte colonne aggiuntive nel set di dati di origine. L'unione dei set di dati è utile quando si dispone di un set di dati locale e si ottiene un secondo set di dati da un'altra applicazione. È utile anche quando si ottiene un secondo set di dati da un componente, ad esempio un servizio Web XML, o quando è necessario integrare i dati da più set di dati.

Quando si uniscono set di dati, è possibile passare un argomento booleano ( ) che indica al metodo se mantenere le `preserveChanges` modifiche esistenti nel set di dati di <xref:System.Data.DataSet.Merge%2A> destinazione. Poiché i set di dati mantengono più versioni dei record, è importante tenere presente che è in corso il merge di più versioni dei record. La tabella seguente illustra come viene unito un record in due set di dati:

|DataRowVersion|DataSet di destinazione|Set di dati di origine|
| - | - | - |
|Originale|James Wilson|James C. Wilson|
|Corrente|Jim Wilson|James C. Wilson|

La chiamata <xref:System.Data.DataSet.Merge%2A> del metodo sulla tabella precedente con i risultati nei dati `preserveChanges=false targetDataset.Merge(sourceDataset)` seguenti:

|DataRowVersion|DataSet di destinazione|Set di dati di origine|
| - | - | - |
|Originale|James C. Wilson|James C. Wilson|
|Corrente|James C. Wilson|James C. Wilson|

La chiamata <xref:System.Data.DataSet.Merge%2A> al metodo con restituisce i dati `preserveChanges = true targetDataset.Merge(sourceDataset, true)` seguenti:

|DataRowVersion|DataSet di destinazione|Set di dati di origine|
| - | - | - |
|Originale|James C. Wilson|James C. Wilson|
|Corrente|Jim Wilson|James C. Wilson|

> [!CAUTION]
> Nello scenario, se il metodo viene chiamato su un record nel set di dati di destinazione, vengono ripristinati i dati originali del set `preserveChanges = true` <xref:System.Data.DataSet.RejectChanges%2A> di dati *di* origine. Ciò significa che se si tenta di aggiornare l'origine dati originale con il set di dati di destinazione, potrebbe non essere possibile trovare la riga originale da aggiornare. È possibile impedire una violazione della concorrenza compilando un altro set di dati con i record aggiornati dell'origine dati e quindi eseguendo un'unione per evitare una violazione della concorrenza. Una violazione della concorrenza si verifica quando un altro utente modifica un record nell'origine dati dopo il riempimento del set di dati.

## <a name="update-constraints"></a>Aggiornare i vincoli

Per apportare modifiche a una riga di dati esistente, aggiungere o aggiornare i dati nelle singole colonne. Se il set di dati contiene vincoli, ad esempio chiavi esterne o vincoli non nullable, è possibile che il record possa essere temporaneamente in uno stato di errore durante l'aggiornamento. Ciò significa che può essere in uno stato di errore dopo aver completato l'aggiornamento di una colonna, ma prima di arrivare a quella successiva.

Per evitare violazioni prematura dei vincoli, è possibile sospendere temporaneamente i vincoli di aggiornamento. Tale differenza viene usata per due scopi:

- Impedisce che venga generato un errore dopo aver completato l'aggiornamento di una colonna, ma non è stato avviato l'aggiornamento di un'altra colonna.

- Impedisce la visualizzazione di determinati eventi di aggiornamento (eventi spesso usati per la convalida).

> [!NOTE]
> In Windows Form, l'architettura data binding incorporata nella griglia di dati sospende il controllo dei vincoli fino a quando lo stato attivo non esce da una riga e non è necessario chiamare in modo esplicito i metodi <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> , o <xref:System.Data.DataRow.CancelEdit%2A> .

I vincoli vengono disabilitati automaticamente quando <xref:System.Data.DataSet.Merge%2A> il metodo viene richiamato su un set di dati. Al termine dell'unione, se nel set di dati sono presenti vincoli che non possono essere abilitati, <xref:System.Data.ConstraintException> viene generata un'eccezione . In questo caso, la proprietà è impostata su e tutte le violazioni dei vincoli devono essere risolte prima <xref:System.Data.DataSet.EnforceConstraints%2A> di reimpostare la proprietà su `false,` <xref:System.Data.DataSet.EnforceConstraints%2A> `true` .

Dopo aver completato un aggiornamento, è possibile abilitare nuovamente il controllo dei vincoli, che abilita nuovamente gli eventi di aggiornamento e li genera.

Per altre informazioni sulla sospensione degli eventi, vedere Disattivare i vincoli durante il [riempimento di un set di dati.](../data-tools/turn-off-constraints-while-filling-a-dataset.md)

## <a name="dataset-update-errors"></a>Errori di aggiornamento del set di dati

Quando si aggiorna un record in un set di dati, è possibile che si sia verificato un errore. Ad esempio, è possibile scrivere inavvertitamente dati di tipo errato in una colonna, dati troppo lunghi o dati con altri problemi di integrità. In caso contrario, potrebbero essere presenti controlli di convalida specifici dell'applicazione che possono generare errori personalizzati durante qualsiasi fase di un evento di aggiornamento. Per altre informazioni, vedere [Convalidare i dati nei set di dati.](../data-tools/validate-data-in-datasets.md)

## <a name="maintain-information-about-changes"></a>Gestire le informazioni sulle modifiche

Le informazioni sulle modifiche in un set di dati vengono mantenute in due modi: contrassegnando le righe che indicano che sono state modificate ( ) e mantenendo più copie di <xref:System.Data.DataRow.RowState%2A> un record ( <xref:System.Data.DataRowVersion> ). Usando queste informazioni, i processi possono determinare le modifiche nel set di dati e inviare gli aggiornamenti appropriati all'origine dati.

### <a name="rowstate-property"></a>RowState - proprietà

La <xref:System.Data.DataRow.RowState%2A> proprietà di un oggetto è un valore che fornisce informazioni sullo stato di una determinata riga di <xref:System.Data.DataRow> dati.

Nella tabella seguente sono elencati in dettaglio i valori possibili <xref:System.Data.DataRowState> dell'enumerazione :

|Valore DataRowState|Descrizione|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|La riga è stata aggiunta come elemento a <xref:System.Data.DataRowCollection> un oggetto . Una riga in questo stato non ha una versione originale corrispondente perché non esisteva quando è stato chiamato <xref:System.Data.DataRow.AcceptChanges%2A> l'ultimo metodo.|
|<xref:System.Data.DataRowState.Deleted>|La riga è stata eliminata utilizzando <xref:System.Data.DataRow.Delete%2A> l'oggetto di un <xref:System.Data.DataRow> oggetto .|
|<xref:System.Data.DataRowState.Detached>|La riga è stata creata ma non fa parte di alcun insieme <xref:System.Data.DataRowCollection>. Un oggetto si trova in questo stato immediatamente dopo essere stato creato, prima di essere aggiunto a una raccolta e dopo essere <xref:System.Data.DataRow> stato rimosso da una raccolta.|
|<xref:System.Data.DataRowState.Modified>|Un valore di colonna nella riga è stato modificato in qualche modo.|
|<xref:System.Data.DataRowState.Unchanged>|La riga non è stata modificata dal momento dell'ultima chiamata del metodo <xref:System.Data.DataRow.AcceptChanges%2A>.|

### <a name="datarowversion-enumeration"></a>DataRowVersion (enumerazione)

I set di dati mantengono più versioni dei record. I campi vengono usati quando si recupera il valore trovato in un <xref:System.Data.DataRowVersion> oggetto usando la proprietà o il metodo <xref:System.Data.DataRow> <xref:System.Data.DataRow.Item%2A> <xref:System.Data.DataRow.GetChildRows%2A> <xref:System.Data.DataRow> dell'oggetto .

Nella tabella seguente sono elencati in dettaglio i valori possibili <xref:System.Data.DataRowVersion> dell'enumerazione :

|Valore di DataRowVersion|Descrizione|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|La versione corrente di un record contiene tutte le modifiche apportate al record dall'ultima chiamata <xref:System.Data.DataRow.AcceptChanges%2A> a . Se la riga è stata eliminata, non è disponibile alcuna versione corrente.|
|<xref:System.Data.DataRowVersion.Default>|Valore predefinito di un record, come definito dallo schema del set di dati o dall'origine dati.|
|<xref:System.Data.DataRowVersion.Original>|La versione originale di un record è una copia del record così com'era l'ultima volta in cui è stato eseguito il commit delle modifiche nel set di dati. In pratica, si tratta in genere della versione di un record come letta da un'origine dati.|
|<xref:System.Data.DataRowVersion.Proposed>|Versione proposta di un record disponibile temporaneamente durante un aggiornamento, ovvero tra il momento in cui è stato chiamato il metodo <xref:System.Data.DataRow.BeginEdit%2A> e il <xref:System.Data.DataRow.EndEdit%2A> metodo . In genere si accede alla versione proposta di un record in un gestore per un evento, ad esempio <xref:System.Data.DataTable.RowChanging> . Se si richiama <xref:System.Data.DataRow.CancelEdit%2A> il metodo , le modifiche vengono annullate ed è possibile eliminare la versione proposta della riga di dati.|

Le versioni originale e corrente sono utili quando le informazioni sugli aggiornamenti vengono trasmesse a un'origine dati. In genere, quando un aggiornamento viene inviato all'origine dati, le nuove informazioni per il database si trovano nella versione corrente di un record. Le informazioni della versione originale vengono usate per individuare il record da aggiornare.

Ad esempio, nel caso in cui la chiave primaria di un record viene modificata, è necessario individuare il record corretto nell'origine dati per aggiornare le modifiche. Se non esistesse alcuna versione originale, molto probabilmente il record verrebbe accodato all'origine dati, risultando non solo in un record indesiderato aggiuntivo, ma in un record non accurato e non aggiornato. Le due versioni vengono usate anche nel controllo della concorrenza. È possibile confrontare la versione originale con un record nell'origine dati per determinare se il record è stato modificato dopo il caricamento nel set di dati.

La versione proposta è utile quando è necessario eseguire la convalida prima di eseguire effettivamente il commit delle modifiche al set di dati.

Anche se i record sono stati modificati, non esistono sempre versioni originali o correnti di tale riga. Quando si inserisce una nuova riga nella tabella, non esiste alcuna versione originale, ma solo una versione corrente. Analogamente, se si elimina una riga chiamando il metodo della tabella, esiste una `Delete` versione originale, ma nessuna versione corrente.

È possibile verificare se esiste una versione specifica di un record tramite una query sul metodo di una riga di <xref:System.Data.DataRow.HasVersion%2A> dati. È possibile accedere a entrambe le versioni di un record passando un valore di enumerazione come argomento facoltativo <xref:System.Data.DataRowVersion> quando si richiede il valore di una colonna.

## <a name="get-changed-records"></a>Ottenere i record modificati

È pratica comune non aggiornare ogni record in un set di dati. Ad esempio, un utente potrebbe lavorare con un controllo Windows Form <xref:System.Windows.Forms.DataGridView> che visualizza molti record. Tuttavia, l'utente potrebbe aggiornare solo alcuni record, eliminarne uno e inserirne uno nuovo. I set di dati e le tabelle di dati forniscono un metodo ( `GetChanges` ) per restituire solo le righe modificate.

È possibile creare subset di record modificati usando il metodo della tabella dati ( ) o del set di `GetChanges` <xref:System.Data.DataTable.GetChanges%2A> dati ( ) <xref:System.Data.DataSet.GetChanges%2A> stesso. Se si chiama il metodo per la tabella dati, viene restituita una copia della tabella con solo i record modificati. Analogamente, se si chiama il metodo sul set di dati, si ottiene un nuovo set di dati in cui sono presenti solo record modificati.

`GetChanges` di per sé restituisce tutti i record modificati. Al contrario, passando l'oggetto desiderato come parametro al metodo , è possibile specificare il subset di record modificati desiderato: i record appena aggiunti, i record contrassegnati per l'eliminazione, i record scollegati o i record <xref:System.Data.DataRowState> `GetChanges` modificati.

Il recupero di un subset di record modificati è utile quando si desidera inviare record a un altro componente per l'elaborazione. Anziché inviare l'intero set di dati, è possibile ridurre il sovraccarico di comunicazione con l'altro componente ottenendo solo i record di cui il componente necessita.

## <a name="commit-changes-in-the-dataset"></a>Eseguire il commit delle modifiche nel set di dati

Quando vengono apportate modifiche nel set di dati, viene <xref:System.Data.DataRow.RowState%2A> impostata la proprietà delle righe modificate. Le versioni originale e corrente dei record vengono stabilite, gestite e rese disponibili dalla <xref:System.Data.DataRowView.RowVersion%2A> proprietà . I metadati archiviati nelle proprietà di queste righe modificate sono necessari per inviare gli aggiornamenti corretti all'origine dati.

Se le modifiche riflettono lo stato corrente dell'origine dati, non è più necessario mantenere queste informazioni. In genere, il set di dati e la relativa origine sono sincronizzati due volte:

- Immediatamente dopo aver caricato le informazioni nel set di dati, ad esempio quando si leggono i dati dall'origine.

- Dopo l'invio delle modifiche dal set di dati all'origine dati (ma non prima, perché si perderebbero le informazioni sulle modifiche necessarie per inviare le modifiche al database).

È possibile eseguire il commit delle modifiche in sospeso nel set di dati chiamando il <xref:System.Data.DataSet.AcceptChanges%2A> metodo . In <xref:System.Data.DataSet.AcceptChanges%2A> genere, viene chiamato nei momenti seguenti:

- Dopo aver caricato il set di dati. Se si carica un set di dati chiamando il metodo di un TableAdapter, l'adapter esegue automaticamente `Fill` il commit delle modifiche. Tuttavia, se si carica un set di dati unendo un altro set di dati al suo interno, è necessario eseguire manualmente il commit delle modifiche.

    > [!NOTE]
    > È possibile impedire all'adattatore di eseguire automaticamente il commit delle modifiche quando si chiama il metodo impostando `Fill` la `AcceptChangesDuringFill` proprietà dell'adattatore su `false` . Se è impostato su `false` , <xref:System.Data.DataRow.RowState%2A> l'oggetto di ogni riga inserita durante il riempimento viene impostato su <xref:System.Data.DataRowState.Added> .

- Dopo aver inviato le modifiche del set di dati a un altro processo, ad esempio un servizio Web XML.

    > [!CAUTION]
    > Il commit della modifica in questo modo cancella tutte le informazioni sulle modifiche. Non eseguire il commit delle modifiche fino al termine dell'esecuzione di operazioni che richiedono all'applicazione di conoscere le modifiche apportate nel set di dati.

Questo metodo esegue le operazioni seguenti:

- Scrive la <xref:System.Data.DataRowVersion.Current> versione di un record nella relativa versione e <xref:System.Data.DataRowVersion.Original> sovrascrive la versione originale.

- Rimuove qualsiasi riga in cui la <xref:System.Data.DataRow.RowState%2A> proprietà è impostata su <xref:System.Data.DataRowState.Deleted> .

- Imposta la <xref:System.Data.DataRow.RowState%2A> proprietà di un record su <xref:System.Data.DataRowState.Unchanged> .

Il <xref:System.Data.DataSet.AcceptChanges%2A> metodo è disponibile a tre livelli. È possibile chiamarlo su un <xref:System.Data.DataRow> oggetto per eseguire il commit delle modifiche solo per tale riga. È anche possibile chiamarlo su un oggetto <xref:System.Data.DataTable> per eseguire il commit di tutte le righe di una tabella. Infine, è possibile chiamarlo sull'oggetto per eseguire il commit di tutte <xref:System.Data.DataSet> le modifiche in sospeso in tutti i record di tutte le tabelle del set di dati.

Nella tabella seguente vengono descritte le modifiche di cui viene eseguito il commit in base all'oggetto su cui viene chiamato il metodo:

|Metodo|Risultato|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Il commit delle modifiche viene eseguito solo nella riga specifica.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Viene eseguito il commit delle modifiche in tutte le righe della tabella specifica.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Viene eseguito il commit delle modifiche in tutte le righe in tutte le tabelle del set di dati.|

> [!NOTE]
> Se si carica un set di dati chiamando il metodo di un TableAdapter, non è necessario accettare in modo `Fill` esplicito le modifiche. Per impostazione predefinita, `Fill` il metodo chiama il metodo al termine del `AcceptChanges` popolamento della tabella dati.

Un metodo correlato, <xref:System.Data.DataSet.RejectChanges%2A> , annulla l'effetto delle modifiche copiando nuovamente la <xref:System.Data.DataRowVersion.Original> versione nella versione dei <xref:System.Data.DataRowVersion.Current> record. Imposta inoltre la <xref:System.Data.DataRow.RowState%2A> proprietà di ogni record su <xref:System.Data.DataRowState.Unchanged> .

## <a name="data-validation"></a>Convalida dei dati

Per verificare che i dati nell'applicazione soddisfino i requisiti dei processi a cui vengono passati, spesso è necessario aggiungere la convalida. Ciò potrebbe comportare la verifica della correttezza dell'immissione di un utente in un modulo, la convalida dei dati inviati all'applicazione da un'altra applicazione o anche il controllo delle informazioni calcolate all'interno del componente rientrano nei vincoli dell'origine dati e dei requisiti dell'applicazione.

È possibile convalidare i dati in diversi modi:

- A livello aziendale, aggiungendo codice all'applicazione per convalidare i dati. Il set di dati è una posizione in cui è possibile eseguire questa operazione. Il set di dati offre alcuni dei vantaggi della convalida back-end, ad esempio la possibilità di convalidare le modifiche quando i valori delle colonne e delle righe cambiano. Per altre informazioni, vedere [Convalidare i dati nei set di dati.](../data-tools/validate-data-in-datasets.md)

- Nel livello di presentazione, aggiungendo la convalida ai moduli. Per altre informazioni, vedere [Convalida dell'input utente in Windows Form.](/dotnet/framework/winforms/user-input-validation-in-windows-forms)

- Nel back-end dei dati, inviando dati all'origine dati, ad esempio il database , e consentendo di accettare o rifiutare i dati. Se si lavora con un database che dispone di funzionalità sofisticate per la convalida dei dati e la fornitura di informazioni sugli errori, questo può essere un approccio pratico perché è possibile convalidare i dati indipendentemente dalla loro origine. Tuttavia, questo approccio potrebbe non soddisfare i requisiti di convalida specifici dell'applicazione. Inoltre, la convalida dei dati nell'origine dati può comportare numerosi round trip all'origine dati, a seconda del modo in cui l'applicazione facilita la risoluzione degli errori di convalida generati dal back-end.

   > [!IMPORTANT]
   > Quando si usano i comandi dati con una proprietà impostata su , controllare attentamente le informazioni inviate da un client prima <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> <xref:System.Data.CommandType.Text> di passarlo al database. Qualche utente malintenzionato potrebbe tentare di inviare (inserire) istruzioni SQL modificate o aggiuntive, allo scopo di ottenere un accesso non autorizzato o di danneggiare il database. Prima di trasferire l'input utente in un database, verificare sempre che le informazioni siano valide. È consigliabile usare sempre query con parametri o stored procedure quando possibile.

## <a name="transmit-updates-to-the-data-source"></a>Trasmettere gli aggiornamenti all'origine dati

Dopo aver apportato le modifiche in un set di dati, è possibile trasmetterli a un'origine dati. In genere, a tale scopo viene chiamato il `Update` metodo di un tableAdapter (o di un adattatore dati). Il metodo esegue il ciclo di ogni record in una tabella dati, determina il tipo di aggiornamento necessario (aggiornamento, inserimento o eliminazione), se presente, e quindi esegue il comando appropriato.

Come illustrazione della modalità di esecuzione degli aggiornamenti, si supponga che l'applicazione usi un set di dati contenente una singola tabella di dati. L'applicazione recupera due righe dal database. Dopo il recupero, la tabella dati in memoria è simile alla seguente:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

L'applicazione modifica lo stato di Nancy Buchanan in "Preferred". In seguito a questa modifica, il valore della proprietà <xref:System.Data.DataRow.RowState%2A> per la riga cambia da a <xref:System.Data.DataRowState.Unchanged> <xref:System.Data.DataRowState.Modified> . Il valore della <xref:System.Data.DataRow.RowState%2A> proprietà per la prima riga rimane <xref:System.Data.DataRowState.Unchanged> . La tabella dati è ora simile alla seguente:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

Tramite l'applicazione in uso viene ora chiamato il metodo `Update` per trasmettere il dataset al database. Il metodo controlla ogni riga a turno. Per la prima riga, il metodo non trasmette alcuna istruzione SQL al database perché tale riga non è stata modificata da quando è stata originariamente recuperata dal database.

Per la seconda riga, tuttavia, il metodo richiama automaticamente il comando dati corretto e `Update` lo trasmette al database. La sintassi specifica dell'istruzione SQL dipende dal dialetto SQL supportato dall'archivio dati sottostante. Tuttavia, i tratti generali seguenti dell'istruzione SQL trasmessa sono degni di nota:

- L'istruzione SQL è un'istruzione UPDATE. L'adapter sa di usare un'istruzione UPDATE perché il valore della <xref:System.Data.DataRow.RowState%2A> proprietà è <xref:System.Data.DataRowState.Modified> .

- L'istruzione SQL include una clausola WHERE che indica che la destinazione dell'istruzione UPDATE è la riga in cui `CustomerID = 'c400'` . Questa parte dell'istruzione SELECT distingue la riga di destinazione da tutte le altre perché è `CustomerID` la chiave primaria della tabella di destinazione. Le informazioni per la clausola WHERE derivano dalla versione originale del record ( ), nel caso in cui i valori necessari per `DataRowVersion.Original` identificare la riga siano stati modificati.

- L'istruzione SQL include la clausola SET per impostare i nuovi valori delle colonne modificate.

   > [!NOTE]
   > Se la proprietà dell'oggetto TableAdapter è stata impostata sul nome di un stored procedure, l'adapter non costruisce `UpdateCommand` un'istruzione SQL tabella. Al contrario, richiama il stored procedure con i parametri appropriati passati.

## <a name="pass-parameters"></a>Passare parametri

I parametri vengono in genere utilizzati per passare i valori per i record che verranno aggiornati nel database. Quando il metodo del TableAdapter `Update` esegue un'istruzione UPDATE, deve compilare i valori dei parametri. Ottiene questi valori dalla raccolta per il comando dati appropriato, in questo `Parameters` caso `UpdateCommand` l'oggetto nell'oggetto TableAdapter.

Se sono stati usati gli strumenti Visual Studio per generare un adattatore dati, l'oggetto contiene una raccolta di parametri che corrispondono a ogni segnaposto di `UpdateCommand` parametro nell'istruzione .

La <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> proprietà di ogni parametro punta a una colonna nella tabella dati. Ad esempio, la proprietà per i parametri e è impostata su `SourceColumn` qualsiasi colonna nella tabella dati che contiene `au_id` `Original_au_id` l'ID autore. Quando viene eseguito, il metodo dell'adattatore legge la colonna author id dal record che viene aggiornato e inserisce i `Update` valori nell'istruzione .

In un'istruzione UPDATE è necessario specificare sia i nuovi valori (quelli che verranno scritti nel record) sia i valori vecchi (in modo che il record possa trovarsi nel database). Sono quindi disponibili due parametri per ogni valore: uno per la clausola SET e uno diverso per la clausola WHERE. Entrambi i parametri leggono i dati dal record che viene aggiornato, ma ottengono versioni diverse del valore della colonna in base alla proprietà del <xref:System.Data.SqlClient.SqlParameter.SourceVersion> parametro. Il parametro per la clausola SET ottiene la versione corrente e il parametro per la clausola WHERE ottiene la versione originale.

> [!NOTE]
> È anche possibile impostare manualmente i valori nella raccolta nel codice, come in genere si farebbe in un gestore eventi `Parameters` per l'evento dell'adattatore <xref:System.Data.DataTable.RowChanging> dati.

## <a name="see-also"></a>Vedi anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Creare e configurare oggetti TableAdapter](create-and-configure-tableadapters.md)
- [Aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Convalidare i dati](validate-data-in-datasets.md)
- [Procedura: Aggiungere, modificare ed eliminare entità (WCF Data Services)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)
