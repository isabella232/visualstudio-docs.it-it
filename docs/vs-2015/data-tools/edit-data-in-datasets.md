---
title: Modificare i dati in set di dati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0fa25e0bf7742420e21ac75883f9927478ee2c23
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656609"
---
# <a name="edit-data-in-datasets"></a>Modifica di dati nei set di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si modificano i dati in tabelle di dati proprio come si modificano i dati in una tabella in qualsiasi database. Può includere il processo di inserimento, aggiornamento ed eliminazione di record nella tabella. In un form con associazione a dati, è possibile specificare quali campi sono modificabili dall'utente. In questi casi, l'infrastruttura di associazione dati gestisce tutto il rilevamento delle modifiche in modo che le modifiche possano essere inviate nuovamente al database in un secondo momento. Se si apportano modifiche ai dati a livello di codice e si desidera inviare tali modifiche nel database, è necessario utilizzare gli oggetti e metodi che eseguono il rilevamento delle modifiche per l'utente.  
  
 Oltre a modificare i dati effettivi, è possibile anche eseguire una query un <xref:System.Data.DataTable> per restituire righe specifiche di dati. Ad esempio, potrebbe eseguire una query per singole righe, versioni specifiche di righe (originale e proposte), le righe che sono stati modificati o righe che contengono errori.  
  
## <a name="to-edit-rows-in-a-dataset"></a>Per modificare le righe in un set di dati  
 Per modificare una riga esistente in un <xref:System.Data.DataTable>, è necessario individuare il <xref:System.Data.DataRow> si desidera modificare e quindi assegnare i valori aggiornati per le colonne desiderate.  
  
 Se non si conosce l'indice della riga si desidera modificare, usare il `FindBy` metodo effettuare la ricerca della chiave primaria:  
  
 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]  
  
 Se si conosce l'indice di riga, è possibile accedere e consente di modificare le righe come indicato di seguito:  
  
 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]  
  
## <a name="to-insert-new-rows-into-a-dataset"></a>Per inserire nuove righe in un set di dati  
 Le applicazioni che usano controlli associati a dati in genere aggiungono nuovi record tramite il **Aggiungi nuovo** pulsante in un [controllo BindingNavigator](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).  
  
 Per aggiungere manualmente i nuovi record a un set di dati, creare una nuova riga di dati chiamando il metodo nella DataTable. Quindi aggiungere la riga per il <xref:System.Data.DataRow> collection (<xref:System.Data.DataTable.Rows%2A>) del <xref:System.Data.DataTable>:  
  
 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]  
  
 Per conservare le informazioni necessarie per inviare gli aggiornamenti all'origine dei dati di set di dati, usare il <xref:System.Data.DataRow.Delete%2A> metodo per rimuovere le righe in una tabella dati. Ad esempio, se l'applicazione usa un oggetto TableAdapter (o <xref:System.Data.Common.DataAdapter>), dell'oggetto TableAdapter `Update` metodo consente di eliminare righe nel database con un <xref:System.Data.DataRow.RowState%2A> di <xref:System.Data.DataRowState>.  
  
 Se l'applicazione non è necessario inviare aggiornamenti a un'origine dati, quindi è possibile rimuovere i record accedendo direttamente la raccolta di righe di dati (<xref:System.Data.DataRowCollection.Remove%2A>).  
  
#### <a name="to-delete-records-from-a-data-table"></a>Per eliminare i record da una tabella dati  
  
-   Chiamare il <xref:System.Data.DataRow.Delete%2A> metodo di un <xref:System.Data.DataRow>.  
  
     Questo metodo non rimuove fisicamente il record. Al contrario, li contrassegna per l'eliminazione.  
  
    > [!NOTE]
    >  Se si verifica la proprietà count di un <xref:System.Data.DataRowCollection>, il numero risultante include i record che sono stati contrassegnati per l'eliminazione. Per ottenere un conteggio accurato di record che non sono contrassegnati per l'eliminazione, è possibile scorrere in ciclo raccolta esaminando il <xref:System.Data.DataRow.RowState%2A> proprietà di ogni record. (Record contrassegnati per l'eliminazione è un' <xref:System.Data.DataRow.RowState%2A> di <xref:System.Data.DataRowState>.) In alternativa, è possibile creare una visualizzazione di dati di un set di dati che i filtri in base allo stato della riga e ottenere la proprietà count da tale posizione.  
  
     Nell'esempio seguente viene illustrato come chiamare il <xref:System.Data.DataRow.Delete%2A> metodo per contrassegnare la prima riga il `Customers` tabella come eliminato:  
  
     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]  
  
## <a name="determine-if-there-are-changed-rows"></a>Determinare se sono presenti righe modificate  
 Quando vengono apportate modifiche ai record in un set di dati, informazioni su tali modifiche vengono archiviate fino a quando non si esegue il commit. Il commit delle modifiche quando si chiama il `AcceptChanges` metodo di una tabella di dati o set di dati o quando si chiama il `Update` metodo di un oggetto TableAdapter o un adattatore dati.  
  
 Le modifiche rilevate in due modi in ogni riga di dati:  
  
- Ogni riga di dati contiene informazioni correlate al relativo <xref:System.Data.DataRow.RowState%2A> (ad esempio <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, o <xref:System.Data.DataRowState>).  
  
- Ogni riga di dati modificati contiene più versioni di riga (<xref:System.Data.DataRowVersion>), la versione originale (prima delle modifiche) e la versione corrente (dopo le modifiche). Durante il periodo durante cui è in sospeso una modifica (l'ora di quando è possibile rispondere al <xref:System.Data.DataTable.RowChanging> eventi), una terza versione, ovvero quella proposta, è disponibile anche.
  
  Il <xref:System.Data.DataSet.HasChanges%2A> metodo di un set di dati restituisce `true` se sono state apportate modifiche nel set di dati. Dopo aver determinato l'esistano di righe modificate, è possibile chiamare il `GetChanges` metodo di un <xref:System.Data.DataSet> o <xref:System.Data.DataTable> per restituire un set di righe modificate. Per altre informazioni, vedere [Procedura: Recuperare le righe modificate](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).  
  
#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Per determinare se sono state apportate modifiche alle righe  
  
-   Chiamare il <xref:System.Data.DataSet.HasChanges%2A> metodo per verificare la presenza di un set di dati delle righe modificate.  
  
     Nell'esempio seguente viene illustrato come controllare il valore restituito dal <xref:System.Data.DataSet.HasChanges%2A> metodo per rilevare se sono presenti tutte le righe modificate in un set di dati denominato `NorthwindDataset1`:  
  
     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]  
  
## <a name="determine-the-type-of-changes"></a>Determinare il tipo di modifiche  
 È inoltre possibile controllare per verificare il tipo di modifiche sono state apportate in un set di dati passando un valore compreso il <xref:System.Data.DataRowState> dell'enumerazione di <xref:System.Data.DataSet.HasChanges%2A> (metodo).  
  
#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Per determinare il tipo di modifiche sono state apportate a una riga  
  
-   Passare un <xref:System.Data.DataRowState> valore per il <xref:System.Data.DataSet.HasChanges%2A> (metodo).  
  
     Nell'esempio seguente viene illustrato come verificare un set di dati denominato `NorthwindDataset1` per determinare se sono state aggiunte nuove righe a esso:  
  
     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]  
  
## <a name="to-locate-rows-that-have-errors"></a>Per individuare le righe con errori  
 Quando si lavora con le singole colonne e righe di dati, possono verificarsi errori. È possibile controllare la `HasErrors` proprietà per determinare se sono presenti errori un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o <xref:System.Data.DataRow>.  
  
1.  Controllare il `HasErrors` proprietà per vedere se sono presenti errori nel set di dati.  
  
2.  Se il `HasErrors` è di proprietà `true`, scorrere le raccolte di tabelle e quindi l'attraverso le righe, per trovare la riga con l'errore.  
  
     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
