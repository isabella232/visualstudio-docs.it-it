---
title: Salvare i dati da un oggetto in un database | Microsoft Docs
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c1470c831177e74e7670d696b44fc2b0119a9a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607461"
---
# <a name="save-data-from-an-object-to-a-database"></a>Salvare dati da un oggetto in un database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile salvare i dati negli oggetti in un database passando i valori dall'oggetto a uno dei metodi DBDirect del TableAdapter, ad esempio `TableAdapter.Insert`.

 Per salvare i dati da una raccolta di oggetti, eseguire il ciclo della raccolta di oggetti (ad esempio, un ciclo for-Next) e inviare i valori per ogni oggetto al database usando uno dei metodi DBDirect del TableAdapter.

 Per impostazione predefinita, i metodi DBDirect vengono creati in un TableAdapter che può essere eseguito direttamente sul database. Questi metodi possono essere chiamati direttamente e non richiedono <xref:System.Data.DataSet> o <xref:System.Data.DataTable> oggetti per riconciliare le modifiche in modo da inviare aggiornamenti a un database.

> [!NOTE]
> Quando si configura un TableAdapter, la query principale deve fornire informazioni sufficienti per la creazione dei metodi DBDirect. Se, ad esempio, un TableAdapter è configurato per eseguire query sui dati di una tabella in cui non è definita una colonna chiave primaria, non genera metodi DBDirect.

|Metodo DBDirect di TableAdapter|Descrizione|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Aggiunge nuovi record a un database e consente di passare i singoli valori di colonna come parametri del metodo.|
|`TableAdapter.Update`|Aggiorna i record esistenti in un database. Il metodo `Update` accetta i valori di colonna originali e nuovi come parametri del metodo. I valori originali vengono usati per individuare il record originale e i nuovi valori vengono usati per aggiornare il record.<br /><br /> Il metodo `TableAdapter.Update` viene inoltre utilizzato per riconciliare le modifiche in un set di dati al database di utilizzando una <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> o una matrice di <xref:System.Data.DataRow>s come parametri del metodo.|
|`TableAdapter.Delete`|Elimina i record esistenti dal database in base ai valori di colonna originali passati come parametri del metodo.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Per salvare nuovi record da un oggetto in un database

- Creare i record passando i valori al metodo `TableAdapter.Insert`.

     Nell'esempio seguente viene creato un nuovo record del cliente nella tabella `Customers` passando i valori nell'oggetto `currentCustomer` al metodo `TableAdapter.Insert`.

     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Per aggiornare i record esistenti da un oggetto a un database

- Modificare i record chiamando il metodo `TableAdapter.Update`, passando i nuovi valori per aggiornare il record e passando i valori originali per individuare il record.

    > [!NOTE]
    > L'oggetto deve mantenere i valori originali per passarli al metodo `Update`. In questo esempio vengono utilizzate le proprietà con un prefisso `orig` per archiviare i valori originali.

     Nell'esempio seguente viene aggiornato un record esistente nella tabella `Customers` passando i valori nuovi e originali nell'oggetto `Customer` al metodo `TableAdapter.Update`.

     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]

### <a name="to-delete-existing-records-from-a-database"></a>Per eliminare i record esistenti da un database

- Eliminare i record chiamando il metodo `TableAdapter.Delete` e passando i valori originali per individuare il record.

    > [!NOTE]
    > L'oggetto deve mantenere i valori originali per passarli al metodo `Delete`. In questo esempio vengono utilizzate le proprietà con un prefisso `orig` per archiviare i valori originali.

     Nell'esempio seguente viene eliminato un record dalla tabella `Customers` passando i valori originali nell'oggetto `Customer` al metodo `TableAdapter.Delete`.

     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]

## <a name="net-framework-security"></a>Sicurezza di .NET Framework
 È necessario disporre dell'autorizzazione per eseguire l'inserimento, l'aggiornamento o l'eliminazione selezionato nella tabella del database.

## <a name="see-also"></a>Vedere anche
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
