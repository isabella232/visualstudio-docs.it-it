---
title: Set di dati di query
description: Informazioni su set di dati di query. Informazioni sulla distinzione tra maiuscole e minuscole del set di dati. Trovare una riga specifica in una tabella dati, trovare le righe in base ai valori di colonna e accedere ai record correlati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2f047f38327f0773f7b370ba721b7e88afed2b90
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631236"
---
# <a name="query-datasets"></a>Set di dati di query
Per cercare record specifici in un set di dati, usare il metodo in `FindBy` DataTable, scrivere un'istruzione [](/dotnet/framework/data/adonet/linq-to-dataset)foreach per eseguire un ciclo sulla raccolta Rows della tabella o usare LINQ to DataSet .

## <a name="dataset-case-sensitivity"></a>Distinzione tra maiuscole e minuscole del set di dati
All'interno di un set di dati, per impostazione predefinita i nomi di tabelle e colonne non sono sensibili alla distinzione tra maiuscole e minuscole, ovvero una tabella in un set di dati denominata "Clienti" può anche essere definita "clienti". Corrisponde alle convenzioni di denominazione in molti database, tra cui SQL Server. In SQL Server comportamento predefinito è che i nomi degli elementi dati non possono essere distinti solo in base alla distinzione tra maiuscole e minuscole.

> [!NOTE]
> A differenza dei set di dati, nei documenti XML viene fatto distinzione tra maiuscole e minuscole, pertanto per i nomi degli elementi di dati definiti negli schemi viene fatto distinzione tra maiuscole e minuscole. Ad esempio, il protocollo dello schema consente allo schema di definire una tabella denominata "Customers" e una tabella diversa denominata "customers". Ciò può causare conflitti di nome quando uno schema che contiene elementi che differiscono solo per la distinzione tra maiuscole e minuscole viene usato per generare una classe del set di dati.

La distinzione tra maiuscole e minuscole, tuttavia, può essere un fattore nella modalità di interpretazione dei dati all'interno del set di dati. Ad esempio, se si filtrano i dati in una tabella del set di dati, i criteri di ricerca potrebbero restituire risultati diversi a seconda che il confronto fa distinzione tra maiuscole e minuscole. È possibile controllare la distinzione tra maiuscole e minuscole di filtro, ricerca e ordinamento impostando la proprietà del set di <xref:System.Data.DataSet.CaseSensitive%2A> dati. Tutte le tabelle nel set di dati ereditano il valore di questa proprietà per impostazione predefinita. È possibile eseguire l'override di questa proprietà per ogni singola tabella impostando la proprietà della <xref:System.Data.DataTable.CaseSensitive%2A> tabella.

## <a name="locate-a-specific-row-in-a-data-table"></a>Individuare una riga specifica in una tabella dati

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Per trovare una riga in un set di dati tipizzato con un valore di chiave primaria

- Per individuare una riga, chiamare il metodo fortemente `FindBy` tipizzato che usa la chiave primaria della tabella.

     Nell'esempio seguente la `CustomerID` colonna è la chiave primaria della tabella `Customers` . Ciò significa che il metodo `FindBy` generato è `FindByCustomerID` . Nell'esempio viene illustrato come assegnare un <xref:System.Data.DataRow> oggetto specifico a una variabile usando il metodo `FindBy` generato.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet18":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet18":::

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Per trovare una riga in un set di dati non tipizzato con un valore di chiave primaria

- Chiamare il <xref:System.Data.DataRowCollection.Find%2A> metodo di una <xref:System.Data.DataRowCollection> raccolta, passando la chiave primaria come parametro.

     Nell'esempio seguente viene illustrato come dichiarare una nuova riga denominata `foundRow` e assegnarle il valore restituito del <xref:System.Data.DataRowCollection.Find%2A> metodo . Se viene trovata la chiave primaria, il contenuto dell'indice di colonna 1 viene visualizzato in una finestra di messaggio.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet19":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet19":::

## <a name="find-rows-by-column-values"></a>Trovare righe per valori di colonna

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Per trovare righe in base ai valori in qualsiasi colonna

- Le tabelle di dati vengono create <xref:System.Data.DataTable.Select%2A> con il metodo , che restituisce una matrice di oggetti in base <xref:System.Data.DataRow> all'espressione passata al <xref:System.Data.DataTable.Select%2A> metodo. Per altre informazioni sulla creazione di espressioni valide, vedere la sezione "Sintassi delle espressioni" della pagina relativa alla <xref:System.Data.DataColumn.Expression%2A> proprietà .

     Nell'esempio seguente viene illustrato come utilizzare il <xref:System.Data.DataTable.Select%2A> metodo di per individuare righe <xref:System.Data.DataTable> specifiche.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet20":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet20":::

## <a name="access-related-records"></a>Accedere ai record correlati
Quando le tabelle in un set di dati sono correlate, <xref:System.Data.DataRelation> un oggetto può rendere disponibili i record correlati in un'altra tabella. Ad esempio, un set di dati `Customers` contenente le tabelle e può essere reso `Orders` disponibile.

È possibile utilizzare un <xref:System.Data.DataRelation> oggetto per individuare i record correlati chiamando il metodo di un oggetto nella tabella <xref:System.Data.DataRow.GetChildRows%2A> <xref:System.Data.DataRow> padre. Questo metodo restituisce una matrice di record figlio correlati. In caso contrario, è possibile <xref:System.Data.DataRow.GetParentRow%2A> chiamare il metodo di un oggetto nella tabella <xref:System.Data.DataRow> figlio. Questo metodo restituisce un singolo <xref:System.Data.DataRow> oggetto dalla tabella padre.

In questa pagina vengono forniti esempi di utilizzo di set di dati tipizzati. Per informazioni sull'esplorazione delle relazioni nei set di dati non tipizzati, vedere [Esplorazione di datarelation.](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations)

> [!NOTE]
> Se si lavora in un'applicazione Windows Forms e si usano le funzionalità di associazione dati per visualizzare i dati, il modulo generato dalla finestra di progettazione potrebbe fornire funzionalità sufficienti per l'applicazione. Per altre informazioni, vedere [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). In particolare, vedere [Relazioni nei set di dati.](relationships-in-datasets.md)

Gli esempi di codice seguenti illustrano come spostarsi tra le relazioni verso l'alto e verso il basso nei set di dati tipizzati. Negli esempi di codice vengono utilizzati i metodi tipizzati ( ) e i metodi <xref:System.Data.DataRow> `NorthwindDataSet.OrdersRow` FindBy *PrimaryKey* ( ) generati per individuare una riga desiderata `FindByCustomerID` e restituire i record correlati. Gli esempi vengono compilati ed eseguiti correttamente solo se si dispone di:

- Istanza di un set di dati denominato `NorthwindDataSet` con una `Customers` tabella.

- `Orders`Tabella.

- Relazione denominata che `FK_Orders_Customers` riguarda le due tabelle.

Inoltre, entrambe le tabelle devono essere riempite con i dati per i record da restituire.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Per restituire i record figlio di un record padre selezionato

- Chiamare il <xref:System.Data.DataRow.GetChildRows%2A> metodo di una riga di dati specifica e restituire una matrice di righe dalla `Customers` `Orders` tabella:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet6":::

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Per restituire il record padre di un record figlio selezionato

- Chiamare il <xref:System.Data.DataRow.GetParentRow%2A> metodo di una riga di dati specifica e restituire una singola riga dalla `Orders` `Customers` tabella:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>Vedi anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
