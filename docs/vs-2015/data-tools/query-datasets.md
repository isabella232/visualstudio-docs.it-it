---
title: Eseguire query sui set di dati | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1626c9c027b12d6a8df8d3169e7d79cefba66006
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659621"
---
# <a name="query-datasets"></a>Set di dati di query
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per cercare un record specifico in un set di dati, usare il metodo FindBy in DataTable, scrivere il proprio ciclo foreach su raccolta di righe della tabella o utilizzare [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17). LINQ to DataSet.  
  
## <a name="dataset-case-sensitivity"></a>Set di dati distinzione maiuscole/minuscole  
 All'interno di un set di dati, i nomi di tabella e colonna sono tra maiuscole e minuscole per impostazione predefinita, vale a dire, una tabella in un set di dati denominato "Customers" può anche essere indicata come "customers". Ciò corrisponde alle convenzioni di denominazione in molti database, tra cui SQL corrispondenza del server di SQL Server, il comportamento predefinito prevede che i nomi degli elementi di dati non possono essere rilevati solo nel caso.  
  
> [!NOTE]
>  A differenza dei set di dati, documenti XML sono tra maiuscole e minuscole, pertanto i nomi di elementi dati definiti in schemi sono tra maiuscole e minuscole. Ad esempio, del protocollo, lo schema definire una tabella denominata "Customers" e un'altra tabella denominata "customers". Ciò può comportare conflitti di nomi quando uno schema che contiene gli elementi che differiscono solo per i casi viene utilizzato per generare una classe di set di dati.  
  
 Distinzione maiuscole/minuscole, tuttavia, può rappresentare un fattore in modalità di interpretazione dei dati all'interno del set di dati. Ad esempio, se si filtrano i dati in una tabella di set di dati, i criteri di ricerca potrebbero restituire risultati diversi a seconda che il confronto sia tra maiuscole e minuscole. È possibile controllare la distinzione maiuscole/minuscole del filtro, la ricerca e ordinamento impostando il set di dati <xref:System.Data.DataSet.CaseSensitive%2A> proprietà. Per impostazione predefinita, tutte le tabelle nel set di dati ereditano il valore di questa proprietà. (È possibile eseguire l'override di questa proprietà per ogni tabella tramite l'impostazione della tabella <xref:System.Data.DataTable.CaseSensitive%2A> proprietà.)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>Individuare una riga specifica in una tabella di dati  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Per trovare una riga in un dataset tipizzato con un valore di chiave primaria  
  
-   Per individuare una riga, chiamare l'oggetto fortemente tipizzato `FindBy` metodo che usa la chiave primaria della tabella.  
  
     Nell'esempio seguente, il `CustomerID` colonna è la chiave primaria del `Customers` tabella. Ciò significa che il generato `FindBy` metodo `FindByCustomerID`. L'esempio illustra come assegnare una determinata <xref:System.Data.DataRow> a una variabile usando il generato `FindBy` (metodo).  
  
     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Per trovare una riga in un dataset non tipizzato con un valore di chiave primaria  
  
-   Chiamare il <xref:System.Data.DataRowCollection.Find%2A> metodo di un <xref:System.Data.DataRowCollection> insieme, passando la chiave primaria come parametro.  
  
     Nell'esempio seguente viene illustrato come dichiarare una nuova riga chiamata `foundRow` e assegnare il valore restituito del <xref:System.Data.DataRowCollection.Find%2A> (metodo). Se la chiave primaria è trovata, il contenuto dell'indice di colonna 1 viene visualizzato in una finestra di messaggio.  
  
     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]  
  
## <a name="findrows-by-column-values"></a>FindRows dai valori di colonna  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Per trovare le righe in base ai valori in qualsiasi colonna  
  
-   Le tabelle di dati vengono create con la<xref:System.Data.DataTable.Select%2A> metodo, che restituisce una matrice di <xref:System.Data.DataRow>s basato sull'espressione passata al <xref:System.Data.DataTable.Select%2A> (metodo). Per altre informazioni sulla creazione di espressioni valide, vedere la sezione "Sintassi di espressione" della pagina about il <xref:System.Data.DataColumn.Expression%2A> proprietà.  
  
     Nell'esempio seguente viene illustrato come utilizzare il <xref:System.Data.DataTable.Select%2A> metodo di <xref:System.Data.DataTable> per individuare le righe specifiche.  
  
     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]  
  
## <a name="access-related-records"></a>Accesso per i record correlati.  
 Quando le tabelle in un set di dati sono correlate, un <xref:System.Data.DataRelation> oggetto può rendere i record correlati disponibili in un'altra tabella. Ad esempio, un set di dati che contiene `Customers` e `Orders` tabelle possono essere rese disponibili.  
  
 È possibile usare una <xref:System.Data.DataRelation> oggetto da individuare i record correlati chiamando il <xref:System.Data.DataRow.GetChildRows%2A> metodo di un <xref:System.Data.DataRow> nella tabella padre. Questo metodo restituisce una matrice di record figlio correlati. Oppure è possibile chiamare il <xref:System.Data.DataRow.GetParentRow%2A> metodo di un <xref:System.Data.DataRow> nella tabella figlio. Questo metodo restituisce un singolo <xref:System.Data.DataRow> dalla tabella padre.  
  
 Questa pagina fornisce esempi che usano i dataset tipizzati. Per informazioni sull'esplorazione di relazioni nei dataset non tipizzati, vedere [esplorazione oggetti DataRelation](http://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).  
  
> [!NOTE]
> Se si lavora in un'applicazione Windows Form e utilizza le funzionalità di data binding per visualizzare i dati, il modulo generato da progettazione potrebbe essere fornite funzionalità sufficienti per l'applicazione. Per altre informazioni, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Gli esempi di codice seguenti illustrano come spostarsi su e giù relazioni nei dataset tipizzato. L'uso di esempi di codice tipizzato <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) e generato `FindBy` *PrimaryKey* (`FindByCustomerID`) i metodi per individuare una riga desiderata e restituire i record correlati. Gli esempi compilati ed eseguiti correttamente solo se è necessario:  
  
- Un'istanza di un set di dati denominato `NorthwindDataSet` con un `Customers` tabella.  
  
- Un `Orders` tabella.  
  
- Una relazione denominata `FK_Orders_Customers`collega le due tabelle disponibili per l'ambito del codice  
  
Inoltre, entrambe le tabelle devono essere occupata dai dati per tutti i record da restituire.  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Per restituire i record di un record padre selezionato figlio  
  
-   Chiamare il <xref:System.Data.DataRow.GetChildRows%2A> metodo di uno specifico `Customers` dei dati di riga e restituire una matrice di righe dal `Orders` tabella:  
  
     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Per restituire il record padre di un record figlio selezionato  
  
-   Chiamare il <xref:System.Data.DataRow.GetParentRow%2A> metodo di uno specifico `Orders` riga di dati e restituire una singola riga dal `Customers` tabella:  
  
     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]
