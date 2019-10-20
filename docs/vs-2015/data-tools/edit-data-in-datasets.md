---
title: Modificare i dati nei set di dati | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 699ee9b6e7a68c6a79f7f7dac526127206e8aa42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672398"
---
# <a name="edit-data-in-datasets"></a>Modifica di dati nei set di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare i dati nelle tabelle dati in modo analogo a come si modificano i dati in una tabella di qualsiasi database. Il processo può includere l'inserimento, l'aggiornamento e l'eliminazione di record nella tabella. In un form con associazione a dati è possibile specificare i campi modificabili dall'utente. In questi casi, l'infrastruttura di data binding gestisce tutti i rilevamento delle modifiche in modo che le modifiche possano essere inviate nuovamente al database in un secondo momento. Se si apportano modifiche ai dati a livello di codice e si desidera inviare le modifiche al database, è necessario utilizzare gli oggetti e i metodi che eseguono il rilevamento delle modifiche.

 Oltre a modificare i dati effettivi, è anche possibile eseguire una query su un <xref:System.Data.DataTable> per restituire righe di dati specifiche. Ad esempio, è possibile eseguire una query per singole righe, versioni specifiche delle righe (originale e proposta), righe modificate o righe che contengono errori.

## <a name="to-edit-rows-in-a-dataset"></a>Per modificare le righe in un set di dati
 Per modificare una riga esistente in una <xref:System.Data.DataTable>, è necessario individuare i <xref:System.Data.DataRow> che si desidera modificare e quindi assegnare i valori aggiornati alle colonne desiderate.

 Se non si conosce l'indice della riga che si desidera modificare, utilizzare il metodo `FindBy` per eseguire la ricerca in base alla chiave primaria:

 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]

 Se si conosce l'indice di riga, è possibile accedere alle righe e modificarle come segue:

 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Per inserire nuove righe in un set di dati
 Le applicazioni che usano controlli associati a dati in genere aggiungono nuovi record tramite il pulsante **Aggiungi nuovo** in un [controllo BindingNavigator](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

 Per aggiungere manualmente nuovi record a un set di dati, creare una nuova riga di dati chiamando il metodo sull'oggetto DataTable. Aggiungere quindi la riga alla raccolta di <xref:System.Data.DataRow> (<xref:System.Data.DataTable.Rows%2A>) del <xref:System.Data.DataTable>:

 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]

 Per mantenere le informazioni necessarie al set di dati per l'invio di aggiornamenti all'origine dati, utilizzare il metodo <xref:System.Data.DataRow.Delete%2A> per rimuovere righe in una tabella di dati. Se, ad esempio, l'applicazione usa un TableAdapter (o <xref:System.Data.Common.DataAdapter>), il metodo `Update` del TableAdapter Elimina le righe del database che hanno un <xref:System.Data.DataRow.RowState%2A> di <xref:System.Data.DataRowState>.

 Se l'applicazione non deve inviare aggiornamenti a un'origine dati, è possibile rimuovere i record accedendo direttamente alla raccolta di righe di dati (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Per eliminare i record da una tabella dati

- Chiamare il metodo <xref:System.Data.DataRow.Delete%2A> di un <xref:System.Data.DataRow>.

     Questo metodo non rimuove fisicamente il record. Il record viene invece contrassegnato per l'eliminazione.

    > [!NOTE]
    > Se si ottiene la proprietà Count di un <xref:System.Data.DataRowCollection>, il conteggio risultante include i record contrassegnati per l'eliminazione. Per ottenere un conteggio accurato dei record che non sono contrassegnati per l'eliminazione, è possibile scorrere la raccolta esaminando la <xref:System.Data.DataRow.RowState%2A> proprietà di ogni record. I record contrassegnati per l'eliminazione hanno un <xref:System.Data.DataRow.RowState%2A> di <xref:System.Data.DataRowState>. In alternativa, è possibile creare una vista dati di un set di dati che filtra in base allo stato della riga e ottenere la proprietà Count da questa posizione.

     Nell'esempio seguente viene illustrato come chiamare il metodo <xref:System.Data.DataRow.Delete%2A> per contrassegnare la prima riga della `Customers` tabella come eliminata:

     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]

## <a name="determine-if-there-are-changed-rows"></a>Determinare se sono presenti righe modificate
 Quando vengono apportate modifiche ai record in un set di dati, le informazioni su tali modifiche vengono archiviate fino a quando non vengono salvate. Le modifiche vengono sottoposte a commit quando si chiama il metodo di `AcceptChanges` di un set di dati o di una tabella dati oppure quando si chiama il metodo `Update` di un TableAdapter o di un adattatore dati.

 Le modifiche vengono rilevate in due modi in ogni riga di dati:

- Ogni riga di dati contiene informazioni correlate alla <xref:System.Data.DataRow.RowState%2A> (ad esempio, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> o <xref:System.Data.DataRowState>).

- Ogni riga di dati modificata contiene più versioni di tale riga (<xref:System.Data.DataRowVersion>), la versione originale (prima delle modifiche) e la versione corrente (dopo le modifiche). Durante il periodo in cui è in sospeso una modifica (il momento in cui è possibile rispondere all'evento <xref:System.Data.DataTable.RowChanging>), è disponibile anche una terza versione, ovvero la versione proposta.

  Il metodo <xref:System.Data.DataSet.HasChanges%2A> di un set di dati restituisce `true` se sono state apportate modifiche nel set di dati. Dopo aver determinato che sono presenti righe modificate, è possibile chiamare il metodo `GetChanges` di un <xref:System.Data.DataSet> o <xref:System.Data.DataTable> per restituire un set di righe modificate. Per altre informazioni, vedere [procedura: recuperare le righe modificate](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Per determinare se sono state apportate modifiche alle righe

- Chiamare il metodo <xref:System.Data.DataSet.HasChanges%2A> di un set di dati per controllare le righe modificate.

     Nell'esempio seguente viene illustrato come controllare il valore restituito dal metodo <xref:System.Data.DataSet.HasChanges%2A> per rilevare se sono presenti righe modificate in un set di dati denominato `NorthwindDataset1`:

     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]

## <a name="determine-the-type-of-changes"></a>Determinare il tipo di modifiche
 È anche possibile verificare il tipo di modifiche apportate in un set di dati passando un valore dall'enumerazione <xref:System.Data.DataRowState> al metodo <xref:System.Data.DataSet.HasChanges%2A>.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Per determinare il tipo di modifiche apportate a una riga

- Passare un valore <xref:System.Data.DataRowState> al metodo <xref:System.Data.DataSet.HasChanges%2A>.

     Nell'esempio seguente viene illustrato come controllare un set di dati denominato `NorthwindDataset1` per determinare se sono state aggiunte nuove righe:

     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]

## <a name="to-locate-rows-that-have-errors"></a>Per individuare le righe che contengono errori
 Quando si utilizzano singole colonne e righe di dati, è possibile che si verifichino errori. È possibile controllare la proprietà `HasErrors` per determinare se sono presenti errori in un <xref:System.Data.DataSet>, <xref:System.Data.DataTable> o <xref:System.Data.DataRow>.

1. Controllare la proprietà `HasErrors` per verificare la presenza di errori nel set di dati.

2. Se la proprietà `HasErrors` è `true`, scorrere le raccolte di tabelle e quindi tramite le righe per trovare la riga con l'errore.

     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
