---
title: Set di impostazioni di query | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ccd5deffb0127769e2cd9dff3bf2accf75617eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607443"
---
# <a name="query-datasets"></a>Set di dati di query
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per cercare record specifici in un set di dati, usare il metodo FindBy sulla DataTable, scrivere un ciclo Foreach personalizzato sulla raccolta Rows della tabella o usare [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17). LINQ to DataSet.

## <a name="dataset-case-sensitivity"></a>Distinzione maiuscole/minuscole DataSet
 All'interno di un set di dati, i nomi delle tabelle e delle colonne non fanno distinzione tra maiuscole e minuscole per impostazione predefinita, ovvero una tabella in un set di dati denominato "Customers" può essere definita anche "Customers". Questo corrisponde alle convenzioni di denominazione in molti database, tra cui SQL Server.In SQL Server, il comportamento predefinito è che i nomi degli elementi dati non possono essere distinti solo per caso.

> [!NOTE]
> A differenza dei set di dati, i documenti XML fanno distinzione tra maiuscole e minuscole, pertanto i nomi degli elementi dati definiti negli schemi fanno distinzione tra maiuscole e minuscole. Il protocollo schema consente, ad esempio, allo schema di definire una tabella denominata "Customers" e una tabella diversa denominata "Customers". Questo può causare conflitti di nomi quando uno schema che contiene elementi che differiscono solo per caso viene usato per generare una classe DataSet.

 La distinzione tra maiuscole e minuscole, tuttavia, può essere un fattore determinante per interpretare i dati all'interno del DataSet. Se ad esempio si filtrano i dati in una tabella del set di dati, i criteri di ricerca potrebbero restituire risultati diversi a seconda che il confronto richieda la distinzione tra maiuscole e minuscole. È possibile controllare la distinzione tra maiuscole e minuscole del filtro, della ricerca e dell'ordinamento impostando la proprietà <xref:System.Data.DataSet.CaseSensitive%2A> del set di dati. Per impostazione predefinita, tutte le tabelle nel set di dati ereditano il valore di questa proprietà. È possibile eseguire l'override di questa proprietà per ogni singola tabella impostando la proprietà <xref:System.Data.DataTable.CaseSensitive%2A> della tabella.

## <a name="locate-a-specific-row-in-a-data-table"></a>Individuare una riga specifica in una tabella dati

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Per trovare una riga in un DataSet tipizzato con un valore di chiave primaria

- Per individuare una riga, chiamare il metodo `FindBy` fortemente tipizzato che utilizza la chiave primaria della tabella.

     Nell'esempio seguente la colonna `CustomerID` è la chiave primaria della tabella `Customers`. Questo significa che il metodo di `FindBy` generato è `FindByCustomerID`. Nell'esempio viene illustrato come assegnare un <xref:System.Data.DataRow> specifico a una variabile utilizzando il metodo `FindBy` generato.

     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Per trovare una riga in un set di dati non tipizzato con un valore di chiave primaria

- Chiamare il metodo <xref:System.Data.DataRowCollection.Find%2A> di una raccolta di <xref:System.Data.DataRowCollection>, passando la chiave primaria come parametro.

     Nell'esempio seguente viene illustrato come dichiarare una nuova riga denominata `foundRow` e assegnarle il valore restituito del metodo <xref:System.Data.DataRowCollection.Find%2A>. Se viene trovata la chiave primaria, il contenuto dell'indice di colonna 1 viene visualizzato in una finestra di messaggio.

     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]

## <a name="findrows-by-column-values"></a>FindRows per valori di colonna

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Per trovare le righe in base ai valori in una colonna

- Le tabelle di dati vengono create con il metodo <xref:System.Data.DataTable.Select%2A>, che restituisce una matrice di <xref:System.Data.DataRow>s in base all'espressione passata al metodo <xref:System.Data.DataTable.Select%2A>. Per ulteriori informazioni sulla creazione di espressioni valide, vedere la sezione "sintassi delle espressioni" della pagina relativa alla proprietà <xref:System.Data.DataColumn.Expression%2A>.

     Nell'esempio seguente viene illustrato come utilizzare il metodo <xref:System.Data.DataTable.Select%2A> della <xref:System.Data.DataTable> per individuare righe specifiche.

     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]

## <a name="access-related-records"></a>Accedere ai record correlati
 Quando le tabelle in un set di dati sono correlate, un oggetto <xref:System.Data.DataRelation> può rendere disponibili i record correlati in un'altra tabella. Ad esempio, è possibile rendere disponibile un set di dati contenente le tabelle `Customers` e `Orders`.

 È possibile utilizzare un oggetto <xref:System.Data.DataRelation> per individuare i record correlati chiamando il metodo <xref:System.Data.DataRow.GetChildRows%2A> di un <xref:System.Data.DataRow> nella tabella padre. Questo metodo restituisce una matrice di record figlio correlati. In alternativa, è possibile chiamare il metodo <xref:System.Data.DataRow.GetParentRow%2A> di un <xref:System.Data.DataRow> nella tabella figlio. Questo metodo restituisce un singolo <xref:System.Data.DataRow> dalla tabella padre.

 In questa pagina vengono forniti esempi di utilizzo di DataSet tipizzati. Per informazioni sull'esplorazione delle relazioni nei set di dati non tipizzati, vedere esplorazione di oggetti [DataRelation](https://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).

> [!NOTE]
> Se si lavora in una Windows Forms Application e si usano le funzionalità di data binding per visualizzare i dati, il form generato dalla finestra di progettazione potrebbe fornire una funzionalità sufficiente per l'applicazione. Per altre informazioni, vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

 Negli esempi di codice seguenti viene illustrato come spostarsi in alto e in basso nelle relazioni nei dataset tipizzati. Gli esempi di codice usano <xref:System.Data.DataRow>s tipizzati (`NorthwindDataSet.OrdersRow`) e i metodi generati `FindBy`*PrimaryKey* (`FindByCustomerID`) per individuare una riga desiderata e restituire i record correlati. Gli esempi vengono compilati ed eseguiti correttamente solo se si dispone di:

- Istanza di un set di dati denominata `NorthwindDataSet` con una tabella `Customers`.

- Tabella `Orders`.

- Una relazione denominata `FK_Orders_Customers`relating le due tabelle disponibili per l'ambito del codice

Inoltre, entrambe le tabelle devono essere riempite con i dati per i record da restituire.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Per restituire i record figlio di un record padre selezionato

- Chiamare il metodo <xref:System.Data.DataRow.GetChildRows%2A> di una riga di dati `Customers` specifica e restituire una matrice di righe dalla tabella `Orders`:

     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Per restituire il record padre di un record figlio selezionato

- Chiamare il metodo <xref:System.Data.DataRow.GetParentRow%2A> di una riga di dati `Orders` specifica e restituire una singola riga dalla tabella `Customers`:

     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]
