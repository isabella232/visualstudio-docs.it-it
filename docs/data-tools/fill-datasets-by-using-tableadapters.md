---
title: Compilare i set di dati usando oggetti TableAdapter
description: Compilare i set di dati usando gli oggetti TableAdapter. Un componente TableAdapter riempie un set di dati con i dati del database, in base a una o più query o stored procedure specificate.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ce4c351bb2226fb1fee5e574b7a35fa7f4d380898d99be1805dce42aed9b0226
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347273"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Compilare i set di dati usando oggetti TableAdapter

Un componente TableAdapter riempie un set di dati con i dati del database, in base a una o più query o stored procedure specificate. Gli oggetti TableAdapter possono inoltre eseguire operazioni di aggiunta, aggiornamento ed eliminazione nel database per rendere persistenti le modifiche apportate al set di dati. È anche possibile eseguire comandi globali non correlati a qualsiasi tabella specifica.

> [!NOTE]
> Gli oggetti TableAdapter vengono generati da Visual Studio finestre di progettazione. Se si creano set di dati a livello di codice, usare DataAdapter, ovvero una classe .NET.

Per informazioni dettagliate sulle operazioni tableAdapter, è possibile passare direttamente a uno di questi argomenti:

|Argomento|Descrizione|
|-----------|-----------------|
|[Creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)|Come usare le finestre di progettazione per creare e configurare oggetti TableAdapter|
|[Creare query TableAdapter con parametri](../data-tools/create-parameterized-tableadapter-queries.md)|Come consentire agli utenti di fornire argomenti a routine o query TableAdapter|
|[Accedere direttamente al database mediante un oggetto TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Come usare i metodi Dbdirect di TableAdapter|
|[Disattivare i vincoli durante il riempimento di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Come usare i vincoli di chiave esterna durante l'aggiornamento dei dati|
|[Come estendere la funzionalità di un TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Come aggiungere codice personalizzato agli oggetti TableAdapter|
|[Leggere dati XML in un set di dati](../data-tools/read-xml-data-into-a-dataset.md)|Come usare XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Panoramica degli oggetti TableAdapter

Gli oggetti TableAdapter sono componenti generati dalla finestra di progettazione che si connettono a un database, eseguono query o stored procedure e riempiono l'oggetto DataTable con i dati restituiti. Gli oggetti TableAdapter inviano anche i dati aggiornati dall'applicazione al database. È possibile eseguire tutte le query desiderate in un TableAdapter, purché restituiranno dati conformi allo schema della tabella a cui è associato l'oggetto TableAdapter. Il diagramma seguente illustra come gli oggetti TableAdapter interagiscono con i database e altri oggetti in memoria:

![Flusso dei dati in un'applicazione client](../data-tools/media/clientdatadiagram.gif)

Mentre gli oggetti TableAdapter sono progettati con **Progettazione DataSet**, le classi TableAdapter non vengono generate come classi annidate di  <xref:System.Data.DataSet> . Si trovano in spazi dei nomi separati specifici per ogni set di dati. Ad esempio, se si dispone di un set di dati denominato , gli oggetti TableAdapter associati a in saranno `NorthwindDataSet` nello spazio dei nomi  <xref:System.Data.DataTable> `NorthwindDataSet` `NorthwindDataSetTableAdapters` . Per accedere a un determinato TableAdapter a livello di codice, è necessario dichiarare una nuova istanza dell'oggetto TableAdapter. Esempio:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs" id="Snippet7":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb" id="Snippet7":::

## <a name="associated-datatable-schema"></a>Schema DataTable associato

Quando si crea un oggetto TableAdapter, si usa la query iniziale o stored procedure per definire lo schema dell'oggetto associato dell'oggetto <xref:System.Data.DataTable> TableAdapter. Per eseguire questa query iniziale o stored procedure chiamare il metodo del TableAdapter , che `Fill` riempie l'oggetto associato dell'oggetto <xref:System.Data.DataTable> TableAdapter. Tutte le modifiche apportate alla query principale del TableAdapter vengono riflesse nello schema della tabella dati associata. Ad esempio, la rimozione di una colonna dalla query principale comporta anche la rimozione della colonna dalla tabella dati associata. Se eventuali query aggiuntive sul TableAdapter utilizzano istruzioni SQL che restituiscono colonne non presenti nella query principale, la finestra di progettazione tenta di sincronizzare le modifiche delle colonne tra la query principale e le query aggiuntive.

## <a name="tableadapter-update-commands"></a>Comandi di aggiornamento tableAdapter

La funzionalità di aggiornamento di un TableAdapter dipende dalla quantità di informazioni disponibili nella query principale nella **Creazione guidata TableAdapter.** Ad esempio, gli oggetti TableAdapter configurati per recuperare i valori da più tabelle (usando ), i valori scalari, le viste o i risultati delle funzioni di aggregazione non vengono creati inizialmente con la possibilità di inviare gli aggiornamenti al `JOIN` database sottostante. È tuttavia possibile configurare manualmente `INSERT` i comandi , e nella `UPDATE` `DELETE` **finestra** Proprietà.

## <a name="tableadapter-queries"></a>TableAdapter (query)

![TableAdapter con più query](../data-tools/media/tableadapter.gif)

Gli oggetti TableAdapter possono contenere più query per riempire le tabelle dati associate. È possibile definire tutte le query necessarie per un TableAdapter nell'applicazione, purché ogni query restituisca dati conformi allo stesso schema della tabella dati associata. Questa funzionalità consente a un TableAdapter di caricare risultati diversi in base a criteri diversi.

Ad esempio, se l'applicazione contiene una tabella con i nomi dei clienti, è possibile creare una query che riempia la tabella con ogni nome di cliente che inizia con una determinata lettera e un'altra che riempie la tabella con tutti i clienti che si trovano nello stesso stato. Per riempire una tabella con i clienti in un determinato stato, è possibile creare una query che accetta un parametro per il valore `Customers` di stato nel modo `FillByState` seguente: `SELECT * FROM Customers WHERE State = @State` . Per eseguire la query, chiamare il `FillByState` metodo e passare il valore del parametro nel modo seguente: `CustomerTableAdapter.FillByState("WA")` .

Oltre ad aggiungere query che restituiscono dati dello stesso schema della tabella dati del TableAdapter, è possibile aggiungere query che restituiscono valori scalari (singoli). Ad esempio, una query che restituisce un conteggio dei clienti ( ) è valida per un oggetto anche se i dati restituiti non sono conformi allo `SELECT Count(*) From Customers` `CustomersTableAdapter,` schema della tabella.

## <a name="clearbeforefill-property"></a>ClearBeforeFill - proprietà

Per impostazione predefinita, ogni volta che si esegue una query per riempire la tabella dati di un TableAdapter, i dati esistenti vengono cancellati e nella tabella vengono caricati solo i risultati della query. Impostare la proprietà dell'oggetto TableAdapter su se si desidera aggiungere o unire i dati restituiti da una query ai `ClearBeforeFill` dati esistenti in una tabella `false` dati. Indipendentemente dalla cancellazione dei dati, è necessario inviare gli aggiornamenti al database in modo esplicito, se si desidera rendere persistenti gli aggiornamenti. Ricordarsi quindi di salvare le modifiche apportate ai dati nella tabella prima di eseguire un'altra query che riempia la tabella. Per altre informazioni, vedere [Aggiornare i dati usando un TableAdapter.](../data-tools/update-data-by-using-a-tableadapter.md)

## <a name="tableadapter-inheritance"></a>Ereditarietà di TableAdapter

Gli oggetti TableAdapter estendono le funzionalità degli adattatori dati standard incapsulando una classe <xref:System.Data.Common.DataAdapter> configurata. Per impostazione predefinita, l'oggetto TableAdapter eredita dalla <xref:System.ComponentModel.Component> classe e non è possibile eseguire il cast alla classe <xref:System.Data.Common.DataAdapter> . Il cast di un TableAdapter <xref:System.Data.Common.DataAdapter> alla classe comporta un <xref:System.InvalidCastException> errore. Per modificare la classe base di un oggetto TableAdapter, è possibile specificare una classe che deriva da nella proprietà Classe base dell'oggetto <xref:System.ComponentModel.Component> TableAdapter nel **Progettazione DataSet**. 

## <a name="tableadapter-methods-and-properties"></a>Metodi e proprietà tableAdapter

La classe TableAdapter non è un tipo .NET. Ciò significa che non è possibile cercarlo nella documentazione o nel **Visualizzatore oggetti.** Viene creato in fase di progettazione quando si usa una delle procedure guidate indicate in precedenza. Il nome assegnato a un TableAdapter al momento della creazione è basato sul nome della tabella in uso. Ad esempio, quando si crea un oggetto TableAdapter basato su una tabella in un database denominato `Orders` , l'oggetto TableAdapter viene denominato `OrdersTableAdapter` . Il nome della classe dell'oggetto TableAdapter può essere modificato usando la **proprietà Name** nel **Progettazione DataSet**.

Di seguito sono riportati i metodi e le proprietà di uso comune degli oggetti TableAdapter:

|Membro|Descrizione|
|------------|-----------------|
|`TableAdapter.Fill`|Popola la tabella dati associata del TableAdapter con i risultati del comando del `SELECT` TableAdapter.|
|`TableAdapter.Update`|Invia le modifiche al database e restituisce un numero intero che rappresenta il numero di righe interessate dall'aggiornamento. Per altre informazioni, vedere [Aggiornare i dati usando un TableAdapter.](../data-tools/update-data-by-using-a-tableadapter.md)|
|`TableAdapter.GetData`|Restituisce un <xref:System.Data.DataTable> nuovo oggetto compilato con dati.|
|`TableAdapter.Insert`|Crea una nuova riga nella tabella dati. Per altre informazioni, vedere [Inserire nuovi record in un database.](../data-tools/insert-new-records-into-a-database.md)|
|`TableAdapter.ClearBeforeFill`|Determina se una tabella di dati viene svuotata prima di chiamare uno dei `Fill` metodi .|

## <a name="tableadapter-update-method"></a>Metodo update di TableAdapter

Gli oggetti TableAdapter usano i comandi di dati per leggere e scrivere dal database. Usare la query iniziale (principale) del TableAdapter come base per la creazione dello schema della tabella dati associata, nonché per i comandi , e associati `Fill` `InsertCommand` al metodo `UpdateCommand` `DeleteCommand` `TableAdapter.Update` . La chiamata al metodo di un TableAdapter esegue le istruzioni create al momento della configurazione originale dell'oggetto TableAdapter, non una delle query aggiuntive aggiunte con la Configurazione guidata `Update` **query TableAdapter**.

Quando si usa un TableAdapter, esegue in modo efficace le stesse operazioni con i comandi che in genere si eseguono. Ad esempio, quando si chiama il metodo dell'adattatore, l'adattatore esegue il comando dati nella relativa proprietà e usa un lettore dati (ad esempio , ) per caricare il set di risultati nella tabella `Fill` `SelectCommand` <xref:System.Data.SqlClient.SqlDataReader> dati. Analogamente, quando si chiama il metodo dell'adattatore, viene eseguito il comando appropriato (nelle proprietà , e ) per ogni record modificato `Update` `UpdateCommand` nella tabella `InsertCommand` `DeleteCommand` dati.

> [!NOTE]
> Se la query principale contiene informazioni sufficienti, i comandi , e vengono creati per impostazione `InsertCommand` predefinita quando viene generato `UpdateCommand` `DeleteCommand` l'oggetto TableAdapter. Se la query principale del TableAdapter è più di una singola istruzione di tabella, è possibile che la finestra di progettazione non sia in grado di generare `SELECT` `InsertCommand` , e `UpdateCommand` `DeleteCommand` . Se questi comandi non vengono generati, è possibile che venga visualizzato un errore durante l'esecuzione del `TableAdapter.Update` metodo .

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods

Oltre a , e , gli oggetti TableAdapter vengono creati con metodi `InsertCommand` che è possibile eseguire direttamente sul `UpdateCommand` `DeleteCommand` database. È possibile chiamare questi metodi ( `TableAdapter.Insert` , e ) direttamente per modificare i dati nel `TableAdapter.Update` `TableAdapter.Delete` database. Ciò significa che è possibile chiamare questi singoli metodi dal codice anziché chiamare per gestire gli inserimenti, gli aggiornamenti e le eliminazioni in sospeso per la `TableAdapter.Update` tabella dati associata.

Se non si vogliono creare questi metodi diretti, impostare la proprietà **GenerateDbDirectMethods** del TableAdapter su `false` (nella **finestra** Proprietà). Le query aggiuntive aggiunte al TableAdapter sono query autonome, che non generano questi metodi.

## <a name="tableadapter-support-for-nullable-types"></a>Supporto tableAdapter per tipi nullable

Gli oggetti TableAdapter supportano tipi nullable `Nullable(Of T)` e `T?` . Per altre informazioni sui tipi nullable in Visual Basic, vedere [Tipi di valori Nullable](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Per altre informazioni sui tipi nullable in C#, vedere [Usare tipi nullable.](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Informazioni di riferimento su TableAdapterManager

Per impostazione predefinita, una classe TableAdapterManager viene generata quando si crea un set di dati contenente tabelle correlate. Per impedire la generazione della classe, modificare il valore della proprietà `Hierarchical Update` del set di dati su false. Quando si trascina una tabella con una relazione nell'area di progettazione di Windows Form o WPF, Visual Studio dichiara una variabile membro della classe. Se non si usa il databinding, è necessario dichiarare manualmente la variabile.

La classe TableAdapterManager non è un tipo .NET. Pertanto, non è possibile cercarlo nella documentazione. Viene creato in fase di progettazione come parte del processo di creazione del set di dati.

Di seguito sono riportati i metodi e le proprietà usati di frequente della `TableAdapterManager` classe :

|Membro|Descrizione|
|------------|-----------------|
|Metodo `UpdateAll`|Salva tutti i dati da tutte le tabelle dati.|
|Proprietà`BackUpDataSetBeforeUpdate`|Determina se creare una copia di backup del set di dati prima di eseguire il `TableAdapterManager.UpdateAll` metodo . Boolean.|
|*tableName* `TableAdapter` Proprietà|Rappresenta un TableAdapter. L'oggetto TableAdapterManager generato contiene una proprietà per ogni `TableAdapter` oggetto che gestisce. Ad esempio, un set di dati con una tabella Customers e Orders genera un oggetto TableAdapterManager che contiene `CustomersTableAdapter` le proprietà e `OrdersTableAdapter` .|
|Proprietà`UpdateOrder`|Controlla l'ordine dei singoli comandi di inserimento, aggiornamento ed eliminazione. Impostare su uno dei valori `TableAdapterManager.UpdateOrderOption` dell'enumerazione .<br /><br /> Per impostazione predefinita, `UpdateOrder` è impostato su **InsertUpdateDelete.** Ciò significa che vengono eseguiti inserimenti, aggiornamenti e quindi eliminazioni per tutte le tabelle nel set di dati.|

## <a name="security"></a>Sicurezza

Quando si usano comandi dati con una proprietà CommandType impostata su , controllare attentamente le informazioni inviate da un client prima di <xref:System.Data.CommandType.Text> passarlo al database. Qualche utente malintenzionato potrebbe tentare di inviare (inserire) istruzioni SQL modificate o aggiuntive, allo scopo di ottenere un accesso non autorizzato o di danneggiare il database. Prima di trasferire l'input dell'utente in un database, verificare sempre che le informazioni siano valide. È consigliabile usare sempre query o stored procedure con parametri quando possibile.

## <a name="see-also"></a>Vedi anche

- [Strumenti del set di dati](../data-tools/dataset-tools-in-visual-studio.md)
