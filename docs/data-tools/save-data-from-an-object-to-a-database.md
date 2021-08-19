---
title: Salvare dati da un oggetto in un database
description: Salvare i dati da un oggetto in un database usando gli strumenti dataset in Visual Studio. Informazioni su come salvare nuovi record, aggiornare i record esistenti ed eliminare i record esistenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 96e296be3bb5e591f3da9699fe15371659dddfc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059203"
---
# <a name="save-data-from-an-object-to-a-database"></a>Salvare dati da un oggetto in un database

È possibile salvare i dati negli oggetti in un database passando i valori dall'oggetto a uno dei metodi DBDirect del TableAdapter , ad esempio `TableAdapter.Insert` . Per altre informazioni, vedere [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Per salvare i dati da una raccolta di oggetti, scorrere la raccolta di oggetti (ad esempio, un ciclo for-next) e inviare i valori per ogni oggetto al database usando uno dei metodi del `DBDirect` TableAdapter.

Per impostazione predefinita, `DBDirect` i metodi vengono creati in un oggetto TableAdapter che può essere eseguito direttamente sul database. Questi metodi possono essere chiamati direttamente e non richiedono oggetti o per riconciliare le modifiche <xref:System.Data.DataSet> <xref:System.Data.DataTable> per inviare aggiornamenti a un database.

> [!NOTE]
> Quando si configura un oggetto TableAdapter, la query principale deve fornire informazioni sufficienti per `DBDirect` la creazione dei metodi. Ad esempio, se un oggetto TableAdapter è configurato per eseguire query sui dati di una tabella in cui non è definita una colonna chiave primaria, non genera `DBDirect` metodi.

|Metodo DBDirect di TableAdapter|Descrizione|
| - |-----------------|
|`TableAdapter.Insert`|Aggiunge nuovi record a un database e consente di passare singoli valori di colonna come parametri del metodo.|
|`TableAdapter.Update`|Aggiorna i record esistenti in un database. Il `Update` metodo accetta i valori di colonna originali e nuovi come parametri del metodo . I valori originali vengono usati per individuare il record originale e i nuovi valori vengono usati per aggiornare il record.<br /><br /> Il metodo viene usato anche per riconciliare le modifiche di un set di dati nel database tramite l'uso di , , o una matrice di `TableAdapter.Update` s come parametri del <xref:System.Data.DataSet> <xref:System.Data.DataTable> <xref:System.Data.DataRow> <xref:System.Data.DataRow> metodo.|
|`TableAdapter.Delete`|Elimina i record esistenti dal database in base ai valori di colonna originali passati come parametri del metodo .|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Per salvare nuovi record da un oggetto a un database

- Creare i record passando i valori al `TableAdapter.Insert` metodo .

     Nell'esempio seguente viene creato un nuovo record customer nella tabella passando `Customers` i valori `currentCustomer` nell'oggetto al metodo `TableAdapter.Insert` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet23":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet23":::

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Per aggiornare i record esistenti da un oggetto a un database

- Modificare i record chiamando il metodo , passando i nuovi valori per aggiornare il record e passando i `TableAdapter.Update` valori originali per individuare il record.

    > [!NOTE]
    > L'oggetto deve mantenere i valori originali per passarli al `Update` metodo . In questo esempio vengono utilizzate le proprietà con `orig` un prefisso per archiviare i valori originali.

     Nell'esempio seguente viene aggiornato un record esistente nella tabella passando i valori nuovi `Customers` e originali `Customer` nell'oggetto al metodo `TableAdapter.Update` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet24":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet24":::

## <a name="to-delete-existing-records-from-a-database"></a>Per eliminare record esistenti da un database

- Eliminare i record chiamando il `TableAdapter.Delete` metodo e passando i valori originali per individuare il record.

    > [!NOTE]
    > L'oggetto deve mantenere i valori originali per passarli al `Delete` metodo . In questo esempio vengono utilizzate le proprietà con `orig` un prefisso per archiviare i valori originali.

     Nell'esempio seguente viene eliminato un record `Customers` dalla tabella passando i valori originali nell'oggetto al metodo `Customer` `TableAdapter.Delete` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet25":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet25":::

## <a name="net-security"></a>Protezione .NET

È necessario disporre dell'autorizzazione per eseguire l'oggetto `INSERT` , o selezionato nella tabella del `UPDATE` `DELETE` database.

## <a name="see-also"></a>Vedi anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
