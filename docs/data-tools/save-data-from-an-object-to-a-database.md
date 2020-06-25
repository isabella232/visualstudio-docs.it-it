---
title: Salvare dati da un oggetto in un database
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4afa0d376366b154501e1a0e4488af57b4448a32
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281656"
---
# <a name="save-data-from-an-object-to-a-database"></a>Salvare dati da un oggetto in un database

È possibile salvare i dati negli oggetti in un database passando i valori dall'oggetto a uno dei metodi DBDirect del TableAdapter (ad esempio, `TableAdapter.Insert` ). Per ulteriori informazioni, vedere [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Per salvare i dati da una raccolta di oggetti, eseguire il ciclo della raccolta di oggetti (ad esempio, un ciclo for-Next) e inviare i valori per ogni oggetto al database usando uno dei metodi del TableAdapter `DBDirect` .

Per impostazione predefinita, i `DBDirect` metodi vengono creati in un TableAdapter che può essere eseguito direttamente sul database. Questi metodi possono essere chiamati direttamente e non richiedono <xref:System.Data.DataSet> <xref:System.Data.DataTable> oggetti o per riconciliare le modifiche per inviare aggiornamenti a un database.

> [!NOTE]
> Quando si configura un TableAdapter, la query principale deve fornire informazioni sufficienti per la `DBDirect` creazione dei metodi. Se, ad esempio, un TableAdapter è configurato per eseguire query sui dati di una tabella in cui non è definita una colonna chiave primaria, non genera `DBDirect` metodi.

|Metodo DBDirect di TableAdapter|Description|
| - |-----------------|
|`TableAdapter.Insert`|Aggiunge nuovi record a un database e consente di passare i singoli valori di colonna come parametri del metodo.|
|`TableAdapter.Update`|Aggiorna i record esistenti in un database. Il `Update` metodo accetta i valori di colonna originali e nuovi come parametri del metodo. I valori originali vengono usati per individuare il record originale e i nuovi valori vengono usati per aggiornare il record.<br /><br /> Il `TableAdapter.Update` metodo viene inoltre utilizzato per riconciliare le modifiche in un set di dati al database di utilizzando <xref:System.Data.DataSet> , <xref:System.Data.DataTable> , <xref:System.Data.DataRow> o una matrice di <xref:System.Data.DataRow> s come parametri del metodo.|
|`TableAdapter.Delete`|Elimina i record esistenti dal database in base ai valori di colonna originali passati come parametri del metodo.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Per salvare nuovi record da un oggetto in un database

- Creare i record passando i valori al `TableAdapter.Insert` metodo.

     Nell'esempio seguente viene creato un nuovo record del cliente nella `Customers` tabella passando i valori dell' `currentCustomer` oggetto al `TableAdapter.Insert` metodo.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Per aggiornare i record esistenti da un oggetto a un database

- Modificare i record chiamando il `TableAdapter.Update` metodo, passando i nuovi valori per aggiornare il record e passando i valori originali per individuare il record.

    > [!NOTE]
    > L'oggetto deve mantenere i valori originali per passarli al `Update` metodo. In questo esempio vengono utilizzate le proprietà con un `orig` prefisso per archiviare i valori originali.

     Nell'esempio seguente viene aggiornato un record esistente nella `Customers` tabella passando i valori nuovi e originali nell' `Customer` oggetto al `TableAdapter.Update` metodo.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Per eliminare i record esistenti da un database

- Eliminare i record chiamando il `TableAdapter.Delete` metodo e passando i valori originali per individuare il record.

    > [!NOTE]
    > L'oggetto deve mantenere i valori originali per passarli al `Delete` metodo. In questo esempio vengono utilizzate le proprietà con un `orig` prefisso per archiviare i valori originali.

     Nell'esempio seguente viene eliminato un record dalla `Customers` tabella passando i valori originali nell' `Customer` oggetto al `TableAdapter.Delete` metodo.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-security"></a>Protezione .NET

È necessario disporre dell'autorizzazione per eseguire l'oggetto selezionato `INSERT` , `UPDATE` o nella tabella del `DELETE` database.

## <a name="see-also"></a>Vedi anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
