---
title: Modifica di dati nei set di dati
description: Informazioni su come modificare i dati nei set di dati. Informazioni su come modificare le righe del set di dati, inserire nuove righe in un set di dati, determinare se sono presenti righe modificate e individuare le righe con errori.
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5cec6bccd2f1b2e6dd2e8250039a82cb4607b65d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052733"
---
# <a name="edit-data-in-datasets"></a>Modifica di dati nei set di dati
I dati nelle tabelle di dati vengono modificati in modo molto simile a quanto si modificano i dati in una tabella di qualsiasi database. Il processo può includere l'inserimento, l'aggiornamento e l'eliminazione di record nella tabella. In un modulo associato a dati è possibile specificare i campi modificabili dall'utente. In questi casi, l'infrastruttura di data binding gestisce tutto il rilevamento delle modifiche in modo che le modifiche possano essere inviate al database in un secondo momento. Se si apportano modifiche ai dati a livello di codice e si intende inviare tali modifiche al database, è necessario utilizzare gli oggetti e i metodi che esetendono automaticamente il rilevamento delle modifiche.

Oltre a modificare i dati effettivi, è anche possibile eseguire una query su per <xref:System.Data.DataTable> restituire righe di dati specifiche. Ad esempio, è possibile eseguire una query per singole righe, versioni specifiche di righe (originali e proposte), righe modificate o righe con errori.

## <a name="to-edit-rows-in-a-dataset"></a>Per modificare le righe in un set di dati
Per modificare una riga esistente in , è necessario individuare l'oggetto da modificare e quindi assegnare i <xref:System.Data.DataTable> valori aggiornati alle colonne <xref:System.Data.DataRow> desiderate.

Se non si conosce l'indice della riga da modificare, usare il metodo per eseguire `FindBy` la ricerca in base alla chiave primaria:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet3":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet3":::

Se si conosce l'indice di riga, è possibile accedere alle righe e modificarle come indicato di seguito:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet5":::

## <a name="to-insert-new-rows-into-a-dataset"></a>Per inserire nuove righe in un set di dati
Le applicazioni che usano controlli associati a dati in genere aggiungono nuovi record tramite il **pulsante Aggiungi** nuovo in un [controllo BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Per aggiungere manualmente nuovi record a un set di dati, creare una nuova riga di dati chiamando il metodo nell'oggetto DataTable. Aggiungere quindi la riga alla <xref:System.Data.DataRow> raccolta ( ) di <xref:System.Data.DataTable.Rows%2A> <xref:System.Data.DataTable> :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet1":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet1":::

Per conservare le informazioni necessarie al set di dati per inviare aggiornamenti all'origine dati, usare il metodo per rimuovere <xref:System.Data.DataRow.Delete%2A> le righe in una tabella dati. Ad esempio, se l'applicazione usa un TableAdapter (o ), il metodo del TableAdapter elimina le righe nel database con <xref:System.Data.Common.DataAdapter> un oggetto di tipo `Update` <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted> .

Se l'applicazione non deve inviare gli aggiornamenti a un'origine dati, è possibile rimuovere i record accedendo direttamente alla raccolta di righe di dati ( <xref:System.Data.DataRowCollection.Remove%2A> ).

#### <a name="to-delete-records-from-a-data-table"></a>Per eliminare record da una tabella dati

- Chiamare il <xref:System.Data.DataRow.Delete%2A> metodo di un oggetto <xref:System.Data.DataRow> .

     Questo metodo non rimuove fisicamente il record. Contrassegna invece il record per l'eliminazione.

    > [!NOTE]
    > Se si ottiene la proprietà count di un oggetto , il conteggio risultante include i <xref:System.Data.DataRowCollection> record contrassegnati per l'eliminazione. Per ottenere un conteggio accurato dei record non contrassegnati per l'eliminazione, è possibile eseguire un ciclo nella raccolta esaminando <xref:System.Data.DataRow.RowState%2A> la proprietà di ogni record. I record contrassegnati per l'eliminazione hanno <xref:System.Data.DataRow.RowState%2A> un valore di <xref:System.Data.DataRowState.Deleted> . In alternativa, è possibile creare una visualizzazione dati di un set di dati che filtra in base allo stato della riga e ottiene la proprietà count da tale posizione.

Nell'esempio seguente viene illustrato come chiamare il metodo per contrassegnare la <xref:System.Data.DataRow.Delete%2A> prima riga della tabella come `Customers` eliminata:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet8":::

## <a name="determine-if-there-are-changed-rows"></a>Determinare se sono presenti righe modificate
Quando vengono apportate modifiche ai record in un set di dati, le informazioni su tali modifiche vengono archiviate fino a quando non ne viene eseguito il commit. Il commit delle modifiche viene eseguito quando si chiama il metodo di un set di dati o di una tabella di dati oppure quando si chiama il metodo di un tableAdapter o `AcceptChanges` `Update` di un adattatore dati.

Le modifiche vengono rilevate in due modi in ogni riga di dati:

- Ogni riga di dati contiene informazioni correlate al <xref:System.Data.DataRow.RowState%2A> relativo (ad esempio, <xref:System.Data.DataRowState.Added> , , o <xref:System.Data.DataRowState.Modified> <xref:System.Data.DataRowState.Deleted> <xref:System.Data.DataRowState.Unchanged> ).

- Ogni riga di dati modificata contiene più versioni di tale riga ( ), la versione originale (prima delle modifiche) e <xref:System.Data.DataRowVersion> la versione corrente (dopo le modifiche). Durante il periodo in cui una modifica è in sospeso (il momento in cui è possibile rispondere all'evento), è disponibile anche una terza versione, ovvero la <xref:System.Data.DataTable.RowChanging> versione proposta.

Il <xref:System.Data.DataSet.HasChanges%2A> metodo di un set di dati restituisce se sono state apportate modifiche al set di `true` dati. Dopo aver determinato l'esistenza delle righe modificate, è possibile chiamare il metodo di un oggetto `GetChanges` o per restituire un set di righe <xref:System.Data.DataSet> <xref:System.Data.DataTable> modificate.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Per determinare se sono state apportate modifiche alle righe

- Chiamare il <xref:System.Data.DataSet.HasChanges%2A> metodo di un set di dati per verificare la presenza di righe modificate.

Nell'esempio seguente viene illustrato come controllare il valore restituito dal metodo per rilevare se sono presenti righe modificate in un set <xref:System.Data.DataSet.HasChanges%2A> di dati denominato `NorthwindDataset1` :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet12":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet12":::

## <a name="determine-the-type-of-changes"></a>Determinare il tipo di modifiche
È anche possibile verificare il tipo di modifiche apportate in un set di dati passando un valore <xref:System.Data.DataRowState> dall'enumerazione al <xref:System.Data.DataSet.HasChanges%2A> metodo .

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Per determinare il tipo di modifiche apportate a una riga

- Passare un <xref:System.Data.DataRowState> valore al <xref:System.Data.DataSet.HasChanges%2A> metodo .

Nell'esempio seguente viene illustrato come controllare un set di dati denominato per determinare se sono state `NorthwindDataset1` aggiunte nuove righe:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet13":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet13":::

## <a name="to-locate-rows-that-have-errors"></a>Per individuare le righe con errori
Quando si lavora con singole colonne e righe di dati, potrebbero verificarsi errori. È possibile controllare la `HasErrors` proprietà per determinare se esistono errori in <xref:System.Data.DataSet> un oggetto , o <xref:System.Data.DataTable> <xref:System.Data.DataRow> .

1. Controllare la `HasErrors` proprietà per verificare se sono presenti errori nel set di dati.

2. Se la proprietà è , scorrere le raccolte di tabelle e quindi scorrere le righe per trovare la `HasErrors` `true` riga con l'errore.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet23":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet23":::

## <a name="see-also"></a>Vedi anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
