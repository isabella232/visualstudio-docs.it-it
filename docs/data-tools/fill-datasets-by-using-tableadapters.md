---
title: Compilare i set di dati usando oggetti TableAdapter
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 888e2ac47348d7e61d115f51e3ea52d15ea9f447
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282436"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Compilare i set di dati usando oggetti TableAdapter

Un componente TableAdapter compila un set di dati con i dati del database, in base a una o più query o stored procedure specificate. Gli oggetti TableAdapter consentono inoltre di eseguire aggiunte, aggiornamenti ed eliminazioni nel database per rendere permanente le modifiche apportate al set di dati. È anche possibile emettere comandi globali non correlati a una tabella specifica.

> [!NOTE]
> Gli oggetti TableAdapter vengono generati dalle finestre di progettazione di Visual Studio. Se si creano set di impostazioni a livello di codice, usare DataAdapter, che è una classe .NET.

Per informazioni dettagliate sulle operazioni TableAdapter, è possibile passare direttamente a uno degli argomenti seguenti:

|Argomento|Description|
|-----------|-----------------|
|[Creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)|Come utilizzare le finestre di progettazione per creare e configurare TableAdapter|
|[Creare query TableAdapter con parametri](../data-tools/create-parameterized-tableadapter-queries.md)|Come consentire agli utenti di fornire argomenti per le query o le procedure TableAdapter|
|[Accedere direttamente al database mediante un oggetto TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Come usare i metodi DBDirect degli oggetti TableAdapter|
|[Disattivare i vincoli durante il riempimento di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Come usare i vincoli di chiave esterna durante l'aggiornamento dei dati|
|[Come estendere la funzionalità di un TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Come aggiungere codice personalizzato a oggetti TableAdapter|
|[Leggere dati XML in un set di dati](../data-tools/read-xml-data-into-a-dataset.md)|Come usare XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Panoramica degli oggetti TableAdapter

Gli oggetti TableAdapter sono componenti generati dalla finestra di progettazione che si connettono a un database, eseguono query o stored procedure e riempiono la DataTable con i dati restituiti. Gli oggetti TableAdapter inviano inoltre i dati aggiornati dall'applicazione al database. È possibile eseguire tutte le query desiderate in un TableAdapter purché restituiscano dati conformi allo schema della tabella a cui è associato l'oggetto TableAdapter. Il diagramma seguente illustra il modo in cui i TableAdapter interagiscono con i database e altri oggetti in memoria:

![Flusso dei dati in un'applicazione client](../data-tools/media/clientdatadiagram.gif)

Sebbene gli oggetti TableAdapter siano progettati con la **Progettazione DataSet**, le classi TableAdapter non vengono generate come classi annidate di <xref:System.Data.DataSet> . Si trovano in spazi dei nomi distinti specifici di ogni set di dati. Se, ad esempio, si dispone di un set di dati denominato `NorthwindDataSet` , gli oggetti TableAdapter associati a in si trovano <xref:System.Data.DataTable> `NorthwindDataSet` nello `NorthwindDataSetTableAdapters` spazio dei nomi. Per accedere a un determinato TableAdapter a livello di codice, è necessario dichiarare una nuova istanza del TableAdapter. Ad esempio:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Schema DataTable associato

Quando si crea un TableAdapter, si usa la query iniziale o stored procedure per definire lo schema dell'oggetto associato del TableAdapter <xref:System.Data.DataTable> . Questa query iniziale o stored procedure viene eseguita chiamando il metodo del TableAdapter, `Fill` che riempie l'oggetto del TableAdapter associato <xref:System.Data.DataTable> . Tutte le modifiche apportate alla query principale del TableAdapter vengono riflesse nello schema della tabella di dati associata. Se, ad esempio, si rimuove una colonna dalla query principale, viene rimossa anche la colonna dalla tabella di dati associata. Se query aggiuntive sul TableAdapter utilizzano istruzioni SQL che restituiscono colonne che non sono incluse nella query principale, la finestra di progettazione tenta di sincronizzare le modifiche delle colonne tra la query principale e le query aggiuntive.

## <a name="tableadapter-update-commands"></a>Comandi di aggiornamento TableAdapter

La funzionalità di aggiornamento di un TableAdapter dipende dalla quantità di informazioni disponibili nella query principale della **procedura guidata TableAdapter**. Ad esempio, gli oggetti TableAdapter configurati per il recupero di valori da più tabelle (utilizzando un oggetto `JOIN` ), valori scalari, viste o risultati di funzioni di aggregazione non vengono inizialmente creati con la possibilità di inviare aggiornamenti al database sottostante. Tuttavia, è possibile configurare `INSERT` manualmente i `UPDATE` comandi, e `DELETE` nella finestra **Proprietà** .

## <a name="tableadapter-queries"></a>TableAdapter (query)

![TableAdapter con più query](../data-tools/media/tableadapter.gif)

Gli oggetti TableAdapter possono contenere più query per riempire le tabelle di dati associate. È possibile definire il numero di query per un TableAdapter come richiesto dall'applicazione, purché ogni query restituisca dati conformi allo stesso schema della tabella di dati associata. Questa funzionalità consente a un TableAdapter di caricare risultati diversi in base a criteri diversi.

Se, ad esempio, l'applicazione contiene una tabella con i nomi dei clienti, è possibile creare una query che riempie la tabella con ogni nome di cliente che inizia con una determinata lettera e un altro che riempie la tabella con tutti i clienti che si trovano nello stesso stato. Per riempire una `Customers` tabella con i clienti in un determinato stato, è possibile creare una `FillByState` query che accetta un parametro per il valore di stato come segue: `SELECT * FROM Customers WHERE State = @State` . Per eseguire la query, chiamare il `FillByState` metodo e passare il valore del parametro come segue: `CustomerTableAdapter.FillByState("WA")` .

Oltre ad aggiungere query che restituiscono dati dello stesso schema della tabella dati del TableAdapter, è possibile aggiungere query che restituiscono valori scalari (singoli). Ad esempio, una query che restituisce un conteggio di Customers ( `SELECT Count(*) From Customers` ) è valida per un oggetto `CustomersTableAdapter,` anche se i dati restituiti non sono conformi allo schema della tabella.

## <a name="clearbeforefill-property"></a>Proprietà ClearBeforeFill

Per impostazione predefinita, ogni volta che si esegue una query per riempire la tabella dati di un TableAdapter, i dati esistenti vengono cancellati e solo i risultati della query vengono caricati nella tabella. Impostare la proprietà del TableAdapter `ClearBeforeFill` su `false` se si desidera aggiungere o unire i dati restituiti da una query ai dati esistenti in una tabella di dati. Indipendentemente dal fatto che i dati vengano cancellati, è necessario inviare in modo esplicito gli aggiornamenti al database, se si desidera renderli permanente. Quindi, ricordarsi di salvare le modifiche apportate ai dati nella tabella prima di eseguire un'altra query che riempie la tabella. Per altre informazioni, vedere [aggiornare i dati tramite un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Ereditarietà TableAdapter

Gli oggetti TableAdapter estendono la funzionalità degli adattatori dati standard incapsulando una classe configurata <xref:System.Data.Common.DataAdapter> . Per impostazione predefinita, il TableAdapter eredita dalla <xref:System.ComponentModel.Component> classe e non è possibile eseguirne il cast alla <xref:System.Data.Common.DataAdapter> classe. Il cast di un TableAdapter alla <xref:System.Data.Common.DataAdapter> classe genera un <xref:System.InvalidCastException> errore. Per modificare la classe di base di un TableAdapter, è possibile specificare una classe che deriva dalla <xref:System.ComponentModel.Component> proprietà della **classe base** del TableAdapter nell' **Progettazione DataSet**.

## <a name="tableadapter-methods-and-properties"></a>Metodi e proprietà di TableAdapter

La classe TableAdapter non è un tipo .NET. Ciò significa che non è possibile cercarlo nella documentazione o nel **Visualizzatore oggetti**. Viene creato in fase di progettazione quando si usa una delle procedure guidate descritte in precedenza. Il nome assegnato a un TableAdapter quando lo si crea si basa sul nome della tabella che si sta utilizzando. Ad esempio, quando si crea un TableAdapter in base a una tabella in un database denominato `Orders` , il TableAdapter viene denominato `OrdersTableAdapter` . Il nome della classe del TableAdapter può essere modificato usando la proprietà **Name** nel **Progettazione DataSet**.

Di seguito sono riportati i metodi e le proprietà di uso comune degli oggetti TableAdapter:

|Membro|Description|
|------------|-----------------|
|`TableAdapter.Fill`|Popola la tabella dati associata del TableAdapter con i risultati del comando del TableAdapter `SELECT` .|
|`TableAdapter.Update`|Invia nuovamente le modifiche al database e restituisce un Integer che rappresenta il numero di righe interessate dall'aggiornamento. Per altre informazioni, vedere [aggiornare i dati tramite un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Restituisce un nuovo oggetto <xref:System.Data.DataTable> riempito con i dati.|
|`TableAdapter.Insert`|Crea una nuova riga nella tabella dati. Per ulteriori informazioni, vedere [inserimento di nuovi record in un database](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Determina se una tabella di dati viene svuotata prima di chiamare uno dei `Fill` metodi.|

## <a name="tableadapter-update-method"></a>Metodo di aggiornamento TableAdapter

I TableAdapter utilizzano i comandi di dati per leggere e scrivere dal database. Utilizzare la `Fill` query iniziale (Main) del TableAdapter come base per la creazione dello schema della tabella di dati associata, nonché i `InsertCommand` `UpdateCommand` comandi, e associati al `DeleteCommand` `TableAdapter.Update` metodo. La chiamata al metodo di un TableAdapter `Update` esegue le istruzioni create durante la configurazione originale del TableAdapter, non una delle query aggiuntive aggiunte con la **Configurazione guidata query TableAdapter**.

Quando si usa un TableAdapter, esegue efficacemente le stesse operazioni con i comandi che si eseguono in genere. Ad esempio, quando si chiama il metodo dell'adapter `Fill` , l'adapter esegue il comando dati nella relativa `SelectCommand` proprietà e utilizza un lettore dati (ad esempio, <xref:System.Data.SqlClient.SqlDataReader> ) per caricare il set di risultati nella tabella dati. Analogamente, quando si chiama il metodo dell'adapter `Update` , viene eseguito il comando appropriato (nelle `UpdateCommand` `InsertCommand` proprietà, e `DeleteCommand` ) per ogni record modificato nella tabella dati.

> [!NOTE]
> Se nella query principale sono presenti informazioni sufficienti, i `InsertCommand` comandi, `UpdateCommand` e `DeleteCommand` vengono creati per impostazione predefinita quando viene generato il TableAdapter. Se la query principale del TableAdapter è più di una singola `SELECT` istruzione Table, è possibile che la finestra di progettazione non sia in grado di generare `InsertCommand` , `UpdateCommand` e `DeleteCommand` . Se questi comandi non vengono generati, è possibile che venga visualizzato un errore durante l'esecuzione del `TableAdapter.Update` metodo.

## <a name="tableadapter-generatedbdirectmethods"></a>GenerateDbDirectMethods TableAdapter

Oltre a `InsertCommand` , `UpdateCommand` e `DeleteCommand` , gli oggetti TableAdapter vengono creati con i metodi che è possibile eseguire direttamente sul database. È possibile chiamare direttamente questi metodi ( `TableAdapter.Insert` , `TableAdapter.Update` e `TableAdapter.Delete` ) per modificare i dati nel database. Ciò significa che è possibile chiamare questi singoli metodi dal codice anziché chiamare `TableAdapter.Update` per gestire gli inserimenti, gli aggiornamenti e le eliminazioni in sospeso per la tabella di dati associata.

Se non si desidera creare questi metodi diretti, impostare la proprietà **GenerateDBDirectMethods** del TableAdapter su `false` (nella finestra **proprietà** ). Le query aggiuntive aggiunte al TableAdapter sono query autonome, che non generano questi metodi.

## <a name="tableadapter-support-for-nullable-types"></a>Supporto di TableAdapter per i tipi Nullable

Gli oggetti TableAdapter supportano i tipi Nullable `Nullable(Of T)` e `T?` . Per altre informazioni sui tipi nullable in Visual Basic, vedere [Tipi di valori Nullable](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Per altre informazioni sui tipi nullable in C#, vedere [usare i tipi nullable](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Riferimento a TableAdapterManager

Per impostazione predefinita, una classe TableAdapterManager genera quando si crea un set di dati contenente tabelle correlate. Per impedire la generazione della classe, modificare il valore della `Hierarchical Update` proprietà del set di dati in false. Quando si trascina una tabella con una relazione nell'area di progettazione di una pagina Windows Form o WPF, Visual Studio dichiara una variabile membro della classe. Se non si usa l'associazione dati, è necessario dichiarare manualmente la variabile.

La classe TableAdapterManager non è un tipo .NET. Pertanto, non è possibile cercarlo nella documentazione. Viene creato in fase di progettazione come parte del processo di creazione del set di dati.

Di seguito sono riportati i metodi e le proprietà di uso frequente della `TableAdapterManager` classe:

|Membro|Description|
|------------|-----------------|
|Metodo `UpdateAll`|Salva tutti i dati di tutte le tabelle di dati.|
|Proprietà `BackUpDataSetBeforeUpdate`|Determina se creare una copia di backup del set di dati prima di eseguire il `TableAdapterManager.UpdateAll` metodo. Boolean.|
|*TableName* `TableAdapter` Proprietà|Rappresenta un TableAdapter. Il TableAdapterManager generato contiene una proprietà per ogni oggetto `TableAdapter` gestito. Ad esempio, un set di dati con una tabella Customers e Orders genera con un TableAdapterManager che contiene `CustomersTableAdapter` le `OrdersTableAdapter` proprietà e.|
|Proprietà `UpdateOrder`|Controlla l'ordine dei singoli comandi INSERT, Update e DELETE. Impostare questa impostazione su uno dei valori dell' `TableAdapterManager.UpdateOrderOption` enumerazione.<br /><br /> Per impostazione predefinita, la `UpdateOrder` è impostata su **InsertUpdateDelete**. Ciò significa che gli inserimenti, gli aggiornamenti e le eliminazioni vengono eseguiti per tutte le tabelle nel set di dati.|

## <a name="security"></a>Security

Quando si usano i comandi dati con una proprietà CommandType impostata su <xref:System.Data.CommandType.Text> , controllare attentamente le informazioni inviate da un client prima di passarle al database. Qualche utente malintenzionato potrebbe tentare di inviare (inserire) istruzioni SQL modificate o aggiuntive, allo scopo di ottenere un accesso non autorizzato o di danneggiare il database. Prima di trasferire l'input dell'utente in un database, verificare sempre che le informazioni siano valide. Una procedura consigliata consiste nell'utilizzare sempre query con parametri o stored procedure, quando possibile.

## <a name="see-also"></a>Vedi anche

- [Strumenti DataSet](../data-tools/dataset-tools-in-visual-studio.md)
