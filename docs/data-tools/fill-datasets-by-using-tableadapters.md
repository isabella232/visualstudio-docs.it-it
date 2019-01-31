---
title: Compilare i set di dati usando oggetti TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: b069e1ed40c4bd110cba87886ea21ea90a96774b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006164"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Compilare i set di dati usando oggetti TableAdapter

Un componente di TableAdapter inserisce un set di dati con i dati dal database, in base a uno o più query o stored procedure specificato. Gli oggetti TableAdapter possono anche eseguire aggiunte, aggiornamenti ed eliminazioni sul database per rendere persistenti le modifiche apportate al set di dati. È inoltre possibile emettere comandi globali che sono correlati a qualsiasi tabella specifica.

> [!NOTE]
> La classe TableAdapter generati dalle finestre di progettazione di Visual Studio. Se si sta creando i set di dati a livello di codice, quindi usare DataAdapter, ovvero una classe .NET Framework.

Per informazioni dettagliate sulle operazioni del TableAdapter, è possibile passare direttamente a uno degli argomenti seguenti:

|Argomento|Description|
|-----------|-----------------|
|[Creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)|Come usare le finestre di progettazione per creare e configurare oggetti TableAdapter|
|[Creare query TableAdapter con parametri](../data-tools/create-parameterized-tableadapter-queries.md)|Come consentire agli utenti di fornire argomenti all'oggetto TableAdapter procedure o query|
|[Accedere direttamente al database mediante un oggetto TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Come usare i metodi Dbdirect di TableAdapter|
|[Disattivare i vincoli durante il riempimento di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Come usare i vincoli foreign key durante l'aggiornamento dati|
|[Come estendere la funzionalità di un TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Come aggiungere codice personalizzato per gli oggetti TableAdapter|
|[Leggere dati XML in un set di dati](../data-tools/read-xml-data-into-a-dataset.md)|Come lavorare con XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Panoramica degli oggetti TableAdapter

Gli oggetti TableAdapter sono generato da Progettazione componenti che si connettono a un database, eseguire query o stored procedure e compilare il DataTable con i dati restituiti. Gli oggetti TableAdapter anche inviare i dati aggiornati dall'applicazione nel database. È possibile eseguire tante di query su un oggetto TableAdapter, purché restituiscono dati conformi allo schema della tabella a cui è associato l'oggetto TableAdapter. Il diagramma seguente mostra come oggetti TableAdapter interagire con i database e altri oggetti in memoria:

![Flusso dei dati in un'applicazione client](../data-tools/media/clientdatadiagram.gif)

Anche se gli oggetti TableAdapter sono progettati con la **Progettazione Dataset**, le classi TableAdapter non vengono generate come classi annidate di <xref:System.Data.DataSet>. Si trovano in spazi dei nomi distinti che sono specifiche per ogni set di dati. Ad esempio, se si dispone di un set di dati denominato `NorthwindDataSet`, gli oggetti TableAdapter associate <xref:System.Data.DataTable>s nel `NorthwindDataSet` sarebbe nel `NorthwindDataSetTableAdapters` dello spazio dei nomi. Per accedere a un oggetto TableAdapter particolare a livello di codice, è necessario dichiarare una nuova istanza dell'oggetto TableAdapter. Ad esempio:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Schema di DataTable associati

Quando si crea un oggetto TableAdapter, si usa la query iniziale o associato alla stored procedure per definire lo schema dell'oggetto TableAdapter <xref:System.Data.DataTable>. Si esegue questa query iniziale o una stored procedure mediante la chiamata dell'oggetto TableAdapter `Fill` metodo (che riempie l'oggetto TableAdapter associato del <xref:System.Data.DataTable>). Tutte le modifiche apportate alla query principale dell'oggetto TableAdapter vengono riflesse nello schema della tabella dati associata. Ad esempio, la rimozione di una colonna dalla query principale rimuove la colonna dalla tabella dati associata. Se eventuali query aggiuntive sul TableAdapter Usa istruzioni SQL che restituiscono le colonne che non sono presenti nella query principali, la finestra di progettazione prova a sincronizzare le modifiche di colonna tra la query principale e le query aggiuntive.

## <a name="tableadapter-update-commands"></a>Comandi di aggiornamento di TableAdapter

La funzionalità di aggiornamento di un oggetto TableAdapter è dipende dalla quantità di informazioni è disponibile nella query principali nel **configurazione guidata TableAdapter**. Ad esempio, la classe TableAdapter che sono configurati per recuperare i valori da più tabelle (utilizzando un `JOIN`), i valori scalari, viste o i risultati di funzioni di aggregazione non sono inizialmente creati con la possibilità di inviare aggiornamenti al database sottostante. Tuttavia, è possibile configurare il `INSERT`, `UPDATE`, e `DELETE` comandi manualmente nel **proprietà** finestra.

## <a name="tableadapter-queries"></a>TableAdapter (query)

![TableAdapter con più query](../data-tools/media/tableadapter.gif)

Gli oggetti TableAdapter possono contenere più query fino a riempire le tabelle dati associate. È possibile definire tutte le query per un oggetto TableAdapter come l'applicazione richiede, purché ogni query restituisce dati conformi allo stesso schema della tabella dati associata. Questa funzionalità consente a un oggetto TableAdapter caricare i risultati diversi in base a criteri diversi.

Ad esempio, se l'applicazione contiene una tabella con i nomi dei clienti, è possibile creare una query che riempie la tabella con ogni nome del cliente che inizia con una lettera e un altro che riempie la tabella con tutti i clienti che si trovano nello stesso stato. Per riempire un `Customers` tabella con i clienti in uno stato specifico, è possibile creare un `FillByState` query che accetta un parametro per il valore di stato come segue: `SELECT * FROM Customers WHERE State = @State`. Eseguire la query chiamando il `FillByState` metodo e passando il valore del parametro come segue: `CustomerTableAdapter.FillByState("WA")`.

Oltre ad aggiungere query che restituiscono dati dello stesso schema della tabella di dati dell'oggetto TableAdapter, è possibile aggiungere query che restituiscono valori scalari (singolo). Ad esempio, una query che restituisce un conteggio di clienti (`SELECT Count(*) From Customers`) è valido per un `CustomersTableAdapter,` anche se i dati restituiti non sono conformi allo schema della tabella.

## <a name="clearbeforefill-property"></a>Proprietà ClearBeforeFill

Per impostazione predefinita, ogni volta che si esegue una query per compilare una tabella di dati TableAdapter, i dati esistenti viene cancellati e vengono caricati solo i risultati della query nella tabella. Impostare dell'oggetto TableAdapter `ClearBeforeFill` proprietà `false` se si desidera aggiungere o unire i dati restituiti da una query per i dati esistenti in una tabella dati. Indipendentemente dal fatto che si cancella i dati, è necessario inviare in modo esplicito gli aggiornamenti nel database, se si vuole renderli persistenti. Quindi, ricordarsi di salvare le modifiche ai dati nella tabella prima di eseguire un'altra query che riempie la tabella. Per altre informazioni, vedere [aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Ereditarietà di TableAdapter

Gli oggetti TableAdapter estendere le funzionalità delle schede di dati standard incapsulando configurato <xref:System.Data.Common.DataAdapter> classe. Per impostazione predefinita, l'oggetto TableAdapter eredita dal <xref:System.ComponentModel.Component> classe e non è possibile eseguire il cast di <xref:System.Data.Common.DataAdapter> classe. Esegue il cast di un oggetto TableAdapter per il <xref:System.Data.Common.DataAdapter> classe risultati in un <xref:System.InvalidCastException> errore. Per modificare la classe di base di un oggetto TableAdapter, è possibile specificare una classe che deriva da <xref:System.ComponentModel.Component> nella **della classe Base** proprietà dell'oggetto TableAdapter nel **Progettazione Dataset**.

## <a name="tableadapter-methods-and-properties"></a>Le proprietà e i metodi TableAdapter

La classe TableAdapter non è in parte il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Ciò significa che è possibile cercarla nella documentazione o la **Visualizzatore oggetti**. Viene creato in fase di progettazione quando si utilizza una delle procedure guidate indicate in precedenza. Il nome assegnato a un oggetto TableAdapter durante la creazione è basato sul nome della tabella di cui che si sta lavorando. Ad esempio, quando si crea un oggetto TableAdapter basato su una tabella in un database denominato `Orders`, denominato oggetto TableAdapter `OrdersTableAdapter`. Il nome della classe dell'oggetto TableAdapter può essere modificato usando il **Name** proprietà nel **Progettazione Dataset**.

Di seguito sono i metodi comunemente utilizzati e le proprietà degli oggetti TableAdapter:

|Member|Description|
|------------|-----------------|
|`TableAdapter.Fill`|Popola tabella dati associata dell'oggetto TableAdapter con i risultati dell'oggetto TableAdapter `SELECT` comando.|
|`TableAdapter.Update`|Invia le modifiche nel database e restituisce un intero che rappresenta il numero di righe interessate dall'aggiornamento. Per altre informazioni, vedere [aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Restituisce un nuovo <xref:System.Data.DataTable> compilato con i dati.|
|`TableAdapter.Insert`|Crea una nuova riga nella tabella dati. Per altre informazioni, vedere [inserire nuovi record in un database](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Determina se una tabella di dati viene svuotata prima di chiamare uno del `Fill` metodi.|

## <a name="tableadapter-update-method"></a>Metodo di aggiornamento di TableAdapter

TableAdapter usare comandi di dati per leggere e scrivere dal database. Usare iniziale dell'oggetto TableAdapter `Fill` query (principale) come base per la creazione dello schema della tabella dati associati, nonché il `InsertCommand`, `UpdateCommand`, e `DeleteCommand` comandi che sono associati il `TableAdapter.Update` (metodo). La chiamata a un oggetto TableAdapter `Update` metodo esegue le istruzioni che sono state create quando l'oggetto TableAdapter è stato originariamente configurato, non è uno dei aggiuntivo aggiunto con una query di **configurazione guidata Query TableAdapter**.

Quando si usa un oggetto TableAdapter, esegue in modo efficace le stesse operazioni con i comandi che si eseguono in genere. Ad esempio, quando si chiama l'adapter `Fill` metodo, l'adapter viene eseguito il comando dati relativo `SelectCommand` proprietà e Usa un lettore di dati (ad esempio, <xref:System.Data.SqlClient.SqlDataReader>) per caricare il set dei risultati nella tabella di dati. Analogamente, quando si chiama l'adapter `Update` metodo, viene eseguito il comando appropriato (nelle `UpdateCommand`, `InsertCommand`, e `DeleteCommand` proprietà) per ciascun record nella tabella di dati modificato.

> [!NOTE]
> Se non sono sufficienti informazioni della query principale, il `InsertCommand`, `UpdateCommand`, e `DeleteCommand` i comandi vengono creati per impostazione predefinita quando viene generato l'oggetto TableAdapter. Se l'oggetto TableAdapter principale del query è maggiore di una singola tabella `SELECT` istruzione, è possibile la finestra di progettazione non sia in grado di generare `InsertCommand`, `UpdateCommand`, e `DeleteCommand`. Se non vengono generati i comandi seguenti, è possibile ricevere un errore durante l'esecuzione di `TableAdapter.Update` (metodo).

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods

Oltre a `InsertCommand`, `UpdateCommand`, e `DeleteCommand`, vengono creati oggetti TableAdapter con metodi che è possibile eseguire direttamente nel database. È possibile chiamare questi metodi (`TableAdapter.Insert`, `TableAdapter.Update`, e `TableAdapter.Delete`) direttamente per manipolare i dati nel database. Ciò significa che è possibile chiamare questi metodi singoli dal codice anziché chiamare `TableAdapter.Update` per la gestione di inserimenti, aggiornamenti ed eliminazioni in sospeso per la tabella di dati associati.

Se non si desidera creare questi metodi diretti, impostare dell'oggetto TableAdapter **GenerateDbDirectMethods** proprietà `false` (nelle **proprietà** finestra). Query aggiuntive che vengono aggiunti all'oggetto TableAdapter sono query autonomo, ovvero non generano questi metodi.

## <a name="tableadapter-support-for-nullable-types"></a>Supporto di TableAdapter per i tipi nullable

Gli oggetti TableAdapter supporta i tipi nullable `Nullable(Of T)` e `T?`. Per altre informazioni sui tipi nullable in Visual Basic, vedere [Tipi di valori Nullable](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Per altre informazioni sui tipi nullable in C#, vedere [usare tipi nullable](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Riferimento a TableAdapterManager

Per impostazione predefinita, una classe di TableAdapterManager genera quando si crea un set di dati che contiene le tabelle correlate. Per evitare che la classe da generare, modificare il valore della `Hierarchical Update` proprietà del set di dati su false. Quando si trascina una tabella che dispone di una relazione nell'area di progettazione di un Windows Form o nella pagina WPF, Visual Studio viene dichiarata una variabile membro della classe. Se non si usa l'associazione dati, è necessario dichiarare manualmente la variabile.

La classe di TableAdapterManager non è in parte il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Pertanto, è possibile cercarla nella documentazione. Viene creato in fase di progettazione come parte del processo di creazione del set di dati.

Di seguito sono i metodi usati di frequente e le proprietà di `TableAdapterManager` classe:

|Member|Description|
|------------|-----------------|
|Metodo `UpdateAll`|Salva tutti i dati da tutte le tabelle di dati.|
|Proprietà`BackUpDataSetBeforeUpdate` |Determina se creare una copia di backup del set di dati prima di eseguire il `TableAdapterManager.UpdateAll` (metodo). Valore booleano.|
|*tableName* `TableAdapter` proprietà|Rappresenta un TableAdapter. Il componente TableAdapterManager generato contiene una proprietà per ogni `TableAdapter` gestisce. Ad esempio, un set di dati con una tabella Customers e Orders che genera l'errore con un componente TableAdapterManager contenente `CustomersTableAdapter` e `OrdersTableAdapter` proprietà.|
|Proprietà`UpdateOrder` |Controlla l'ordine delle singole insert, update e i comandi delete. Impostare questa proprietà su uno dei valori di `TableAdapterManager.UpdateOrderOption` enumerazione.<br /><br /> Per impostazione predefinita, il `UpdateOrder` è impostata su **InsertUpdateDelete**. Ciò significa che inserisce, aggiorna quindi Elimina quindi vengono eseguite per tutte le tabelle nel set di dati.|

## <a name="security"></a>Sicurezza

Quando si usano i comandi dei dati con la proprietà CommandType impostata su <xref:System.Data.CommandType.Text>, attentamente controllare le informazioni inviate da un client prima di passarlo al database. Qualche utente malintenzionato potrebbe tentare di inviare (inserire) istruzioni SQL modificate o aggiuntive, allo scopo di ottenere un accesso non autorizzato o di danneggiare il database. Prima di trasferire input dell'utente a un database, verificare sempre che le informazioni siano valide. Una procedura consigliata consiste nell'utilizzare sempre query con parametri o stored procedure, laddove possibile.

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati](../data-tools/dataset-tools-in-visual-studio.md)
