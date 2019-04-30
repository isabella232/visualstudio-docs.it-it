---
title: Set di dati di query
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bec1c878dce59ccb5444d74ba0255c9ceb705780
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402734"
---
# <a name="query-datasets"></a>Set di dati di query
Per cercare un record specifico in un set di dati, usare il `FindBy` metodo sull'oggetto DataTable, scrivere il proprio istruzione foreach per eseguire un ciclo in raccolta di righe della tabella oppure usare [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Set di dati distinzione maiuscole/minuscole
All'interno di un set di dati, i nomi di tabella e colonna sono tra maiuscole e minuscole per impostazione predefinita, vale a dire, una tabella in un set di dati denominato "Customers" può anche essere indicata come "customers". Ciò corrisponde alle convenzioni di denominazione in molti database, tra cui SQL Server. In SQL Server, il comportamento predefinito è che non è possibile distinguere i nomi degli elementi di dati solo di maiuscole/minuscole.

> [!NOTE]
> A differenza dei set di dati, documenti XML sono tra maiuscole e minuscole, pertanto i nomi di elementi dati definiti in schemi sono tra maiuscole e minuscole. Ad esempio, del protocollo, lo schema definire una tabella denominata "Customers" e un'altra tabella denominata "customers". Ciò può comportare conflitti di nomi quando uno schema che contiene gli elementi che differiscono solo per i casi viene utilizzato per generare una classe di set di dati.

Distinzione maiuscole/minuscole, tuttavia, può rappresentare un fattore in modalità di interpretazione dei dati all'interno del set di dati. Ad esempio, se si filtrano i dati in una tabella di set di dati, i criteri di ricerca potrebbero restituire risultati diversi a seconda che il confronto sia tra maiuscole e minuscole. È possibile controllare la distinzione maiuscole/minuscole del filtro, la ricerca e ordinamento impostando il set di dati <xref:System.Data.DataSet.CaseSensitive%2A> proprietà. Per impostazione predefinita, tutte le tabelle nel set di dati ereditano il valore di questa proprietà. (È possibile eseguire l'override di questa proprietà per ogni tabella tramite l'impostazione della tabella <xref:System.Data.DataTable.CaseSensitive%2A> proprietà.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Individuare una riga specifica in una tabella di dati

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Per trovare una riga in un dataset tipizzato con un valore di chiave primaria

- Per individuare una riga, chiamare l'oggetto fortemente tipizzato `FindBy` metodo che usa la chiave primaria della tabella.

     Nell'esempio seguente, il `CustomerID` colonna è la chiave primaria del `Customers` tabella. Ciò significa che il generato `FindBy` metodo `FindByCustomerID`. L'esempio illustra come assegnare una determinata <xref:System.Data.DataRow> a una variabile usando il generato `FindBy` (metodo).

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Per trovare una riga in un dataset non tipizzato con un valore di chiave primaria

- Chiamare il <xref:System.Data.DataRowCollection.Find%2A> metodo di un <xref:System.Data.DataRowCollection> insieme, passando la chiave primaria come parametro.

     Nell'esempio seguente viene illustrato come dichiarare una nuova riga chiamata `foundRow` e assegnare il valore restituito del <xref:System.Data.DataRowCollection.Find%2A> (metodo). Se la chiave primaria è trovata, il contenuto dell'indice di colonna 1 viene visualizzato in una finestra di messaggio.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Trovare le righe dai valori di colonna

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Per trovare le righe in base ai valori in qualsiasi colonna

- Le tabelle di dati vengono create con la <xref:System.Data.DataTable.Select%2A> metodo, che restituisce una matrice di <xref:System.Data.DataRow>s basato sull'espressione passata al <xref:System.Data.DataTable.Select%2A> (metodo). Per altre informazioni sulla creazione di espressioni valide, vedere la sezione "Sintassi di espressione" della pagina about il <xref:System.Data.DataColumn.Expression%2A> proprietà.

     Nell'esempio seguente viene illustrato come utilizzare il <xref:System.Data.DataTable.Select%2A> metodo di <xref:System.Data.DataTable> per individuare le righe specifiche.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Accesso per i record correlati.
Quando le tabelle in un set di dati sono correlate, un <xref:System.Data.DataRelation> oggetto può rendere i record correlati disponibili in un'altra tabella. Ad esempio, un set di dati che contiene `Customers` e `Orders` tabelle possono essere rese disponibili.

È possibile usare una <xref:System.Data.DataRelation> oggetto da individuare i record correlati chiamando il <xref:System.Data.DataRow.GetChildRows%2A> metodo di un <xref:System.Data.DataRow> nella tabella padre. Questo metodo restituisce una matrice di record figlio correlati. Oppure, è possibile chiamare il <xref:System.Data.DataRow.GetParentRow%2A> metodo di un <xref:System.Data.DataRow> nella tabella figlio. Questo metodo restituisce un singolo <xref:System.Data.DataRow> dalla tabella padre.

Questa pagina fornisce esempi che usano i dataset tipizzati. Per informazioni sull'esplorazione di relazioni nei dataset non tipizzati, vedere [esplorazione oggetti DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
> Se si lavora in un'applicazione Windows Form e utilizza le funzionalità di data binding per visualizzare i dati, il modulo generato da progettazione potrebbe essere fornite funzionalità sufficienti per l'applicazione. Per altre informazioni, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). In particolare, vedere [relazioni nei DataSet](relationships-in-datasets.md).

Gli esempi di codice seguenti illustrano come spostarsi su e giù relazioni nei dataset tipizzato. L'uso di esempi di codice tipizzato <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) e il generato FindBy*PrimaryKey* (`FindByCustomerID`) i metodi per individuare una riga desiderata e restituire i record correlati. Gli esempi compilati ed eseguiti correttamente solo se è necessario:

- Un'istanza di un set di dati denominato `NorthwindDataSet` con un `Customers` tabella.

- Un `Orders` tabella.

- Una relazione denominata `FK_Orders_Customers`collega le due tabelle.

Inoltre, entrambe le tabelle devono essere occupata dai dati per tutti i record da restituire.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Per restituire i record di un record padre selezionato figlio

- Chiamare il <xref:System.Data.DataRow.GetChildRows%2A> metodo di uno specifico `Customers` dei dati di riga e restituire una matrice di righe dal `Orders` tabella:

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Per restituire il record padre di un record figlio selezionato

- Chiamare il <xref:System.Data.DataRow.GetParentRow%2A> metodo di uno specifico `Orders` riga di dati e restituire una singola riga dal `Customers` tabella:

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)