---
title: Modifica di dati nei set di dati
description: Informazioni su come modificare i dati nei set di dati. Sapere come modificare le righe del set di dati, inserire nuove righe in un set di dati, determinare se sono state modificate righe e individuare le righe con errori.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e547d3a6a07a7881c34462138ffbe708b8d74080
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435091"
---
# <a name="edit-data-in-datasets"></a>Modifica di dati nei set di dati
È possibile modificare i dati nelle tabelle dati in modo analogo a come si modificano i dati in una tabella di qualsiasi database. Il processo può includere l'inserimento, l'aggiornamento e l'eliminazione di record nella tabella. In un form con associazione a dati è possibile specificare i campi modificabili dall'utente. In questi casi, l'infrastruttura di data binding gestisce tutti i rilevamento delle modifiche in modo che le modifiche possano essere inviate nuovamente al database in un secondo momento. Se si apportano modifiche ai dati a livello di codice e si desidera inviare le modifiche al database, è necessario utilizzare gli oggetti e i metodi che eseguono il rilevamento delle modifiche.

Oltre a modificare i dati effettivi, è anche possibile eseguire una query <xref:System.Data.DataTable> su per restituire righe di dati specifiche. Ad esempio, è possibile eseguire una query per singole righe, versioni specifiche delle righe (originale e proposta), righe modificate o righe che contengono errori.

## <a name="to-edit-rows-in-a-dataset"></a>Per modificare le righe in un set di dati
Per modificare una riga esistente in un oggetto <xref:System.Data.DataTable> , è necessario individuare l'oggetto <xref:System.Data.DataRow> che si desidera modificare e quindi assegnare i valori aggiornati alle colonne desiderate.

Se non si conosce l'indice della riga che si desidera modificare, utilizzare il `FindBy` metodo per eseguire la ricerca in base alla chiave primaria:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Se si conosce l'indice di riga, è possibile accedere alle righe e modificarle come segue:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Per inserire nuove righe in un set di dati
Le applicazioni che usano controlli associati a dati in genere aggiungono nuovi record tramite il pulsante **Aggiungi nuovo** in un [controllo BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Per aggiungere manualmente nuovi record a un set di dati, creare una nuova riga di dati chiamando il metodo sull'oggetto DataTable. Aggiungere quindi la riga alla <xref:System.Data.DataRow> raccolta ( <xref:System.Data.DataTable.Rows%2A> ) dell'oggetto <xref:System.Data.DataTable> :

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Per mantenere le informazioni necessarie al set di dati per l'invio di aggiornamenti all'origine dati, utilizzare il <xref:System.Data.DataRow.Delete%2A> metodo per rimuovere le righe in una tabella di dati. Se, ad esempio, l'applicazione usa un TableAdapter (o <xref:System.Data.Common.DataAdapter> ), il metodo del TableAdapter `Update` Elimina le righe nel database che hanno un <xref:System.Data.DataRow.RowState%2A> di <xref:System.Data.DataRowState.Deleted> .

Se l'applicazione non deve inviare aggiornamenti a un'origine dati, è possibile rimuovere i record accedendo direttamente alla raccolta di righe di dati ( <xref:System.Data.DataRowCollection.Remove%2A> ).

#### <a name="to-delete-records-from-a-data-table"></a>Per eliminare i record da una tabella dati

- Chiamare il <xref:System.Data.DataRow.Delete%2A> metodo di un oggetto <xref:System.Data.DataRow> .

     Questo metodo non rimuove fisicamente il record. Il record viene invece contrassegnato per l'eliminazione.

    > [!NOTE]
    > Se si ottiene la proprietà Count di un <xref:System.Data.DataRowCollection> , il conteggio risultante include i record contrassegnati per l'eliminazione. Per ottenere un conteggio accurato dei record che non sono contrassegnati per l'eliminazione, è possibile scorrere la raccolta esaminando la <xref:System.Data.DataRow.RowState%2A> proprietà di ogni record. I record contrassegnati per l'eliminazione hanno un valore <xref:System.Data.DataRow.RowState%2A> di <xref:System.Data.DataRowState.Deleted> . In alternativa, è possibile creare una vista dati di un set di dati che filtra in base allo stato della riga e ottenere la proprietà Count da questa posizione.

Nell'esempio seguente viene illustrato come chiamare il <xref:System.Data.DataRow.Delete%2A> metodo per contrassegnare la prima riga della `Customers` tabella come eliminata:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Determinare se sono presenti righe modificate
Quando vengono apportate modifiche ai record in un set di dati, le informazioni su tali modifiche vengono archiviate fino a quando non vengono salvate. Le modifiche vengono sottoposte a commit quando si chiama il `AcceptChanges` metodo di un set di dati o di una tabella dati oppure quando si chiama il `Update` metodo di un TableAdapter o di un adattatore dati.

Le modifiche vengono rilevate in due modi in ogni riga di dati:

- Ogni riga di dati contiene informazioni correlate a <xref:System.Data.DataRow.RowState%2A> (ad esempio,,, <xref:System.Data.DataRowState.Added> <xref:System.Data.DataRowState.Modified> <xref:System.Data.DataRowState.Deleted> o <xref:System.Data.DataRowState.Unchanged> ).

- Ogni riga di dati modificata contiene più versioni di tale riga ( <xref:System.Data.DataRowVersion> ), la versione originale (prima delle modifiche) e la versione corrente (dopo le modifiche). Durante il periodo in cui è presente una modifica in sospeso (la data e l'ora in cui è possibile rispondere all' <xref:System.Data.DataTable.RowChanging> evento), è disponibile anche una terza versione, ovvero la versione proposta.

Il <xref:System.Data.DataSet.HasChanges%2A> metodo di un set di dati restituisce `true` se le modifiche sono state apportate nel set di dati. Dopo aver determinato che sono presenti righe modificate, è possibile chiamare il `GetChanges` metodo di un oggetto <xref:System.Data.DataSet> o <xref:System.Data.DataTable> per restituire un set di righe modificate.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Per determinare se sono state apportate modifiche alle righe

- Chiamare il <xref:System.Data.DataSet.HasChanges%2A> metodo di un set di dati per controllare le righe modificate.

Nell'esempio seguente viene illustrato come controllare il valore restituito dal <xref:System.Data.DataSet.HasChanges%2A> metodo per rilevare se sono presenti righe modificate in un set di dati denominato `NorthwindDataset1` :

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Determinare il tipo di modifiche
È anche possibile verificare il tipo di modifiche apportate in un set di dati passando un valore dall' <xref:System.Data.DataRowState> enumerazione al <xref:System.Data.DataSet.HasChanges%2A> metodo.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Per determinare il tipo di modifiche apportate a una riga

- Passare un <xref:System.Data.DataRowState> valore al <xref:System.Data.DataSet.HasChanges%2A> metodo.

Nell'esempio seguente viene illustrato come controllare un set di dati denominato `NorthwindDataset1` per determinare se sono state aggiunte nuove righe:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Per individuare le righe che contengono errori
Quando si utilizzano singole colonne e righe di dati, è possibile che si verifichino errori. È possibile controllare la `HasErrors` proprietà per determinare se sono presenti errori in un oggetto <xref:System.Data.DataSet> , <xref:System.Data.DataTable> o <xref:System.Data.DataRow> .

1. Controllare la `HasErrors` proprietà per verificare se sono presenti errori nel set di dati.

2. Se la `HasErrors` proprietà è `true` , scorrere le raccolte di tabelle e quindi attraverso le righe per trovare la riga con l'errore.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
