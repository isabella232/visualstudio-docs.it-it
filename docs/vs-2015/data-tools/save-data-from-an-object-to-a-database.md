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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6980ecc7676afd978f8dfd243ef8f383413ad83d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074883"
---
# <a name="save-data-from-an-object-to-a-database"></a>Salvare dati da un oggetto in un database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile salvare i dati dagli oggetti in un database passando i valori dall'oggetto a uno dei metodi DBDirect di TableAdapter (ad esempio, `TableAdapter.Insert`).
  
 Per salvare i dati da una raccolta di oggetti, scorrere la raccolta di oggetti (ad esempio, un ciclo for next) e inviare i valori per ogni oggetto nel database utilizzando uno dei metodi DBDirect di TableAdapter.  
  
 Per impostazione predefinita, i metodi DBDirect di vengono creati in un oggetto TableAdapter che può essere eseguito direttamente nel database. Questi metodi possono essere chiamati direttamente e non richiedono <xref:System.Data.DataSet> o <xref:System.Data.DataTable> oggetti da riconciliare le modifiche per inviare aggiornamenti a un database.  
  
> [!NOTE]
>  Quando si configura un oggetto TableAdapter, la query principale deve fornire informazioni sufficienti per i metodi DBDirect da creare. Ad esempio, se un oggetto TableAdapter è configurato per eseguire query sui dati da una tabella che non dispone di una colonna chiave primaria definita, non genera metodi DBDirect di.  
  
|Metodo DBDirect di TableAdapter|Descrizione|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|Aggiunge nuovi record a un database e consente di passare i valori di singole colonne come parametri del metodo.|  
|`TableAdapter.Update`|Aggiorna i record in un database esistenti. Il `Update` metodo accetta i valori originale e della nuova colonna come parametri del metodo. I valori originali vengono usati per individuare il record originale e i nuovi valori vengono usati per aggiornare record in questione.<br /><br /> Il `TableAdapter.Update` metodo viene usato anche per risolvere le modifiche in un set di dati nel database eseguendo un' <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, o una matrice di <xref:System.Data.DataRow>s come parametri del metodo.|  
|`TableAdapter.Delete`|Elimina i record dal database in base ai valori di colonna originali passati come parametri del metodo esistenti.|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>Per salvare i nuovi record da un oggetto in un database  
  
- Creare i record passando i valori per il `TableAdapter.Insert` (metodo).  
  
     L'esempio seguente crea un nuovo record del cliente nel `Customers` passando i valori nella tabella di `currentCustomer` dell'oggetto per il `TableAdapter.Insert` (metodo).  
  
     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Per aggiornare i record esistenti da un oggetto a un database  
  
- Modificare i record chiamando il `TableAdapter.Update` (metodo), passando i nuovi valori per aggiornare il record e i valori originali per individuare il record.  
  
    > [!NOTE]
    >  L'oggetto deve mantenere i valori originali per passarli al `Update` (metodo). Questo esempio Usa le proprietà con un `orig` prefisso per archiviare i valori originali.  
  
     L'esempio seguente aggiorna un record esistente nel `Customers` tabella passando i valori nuovi e originali nel `Customer` dell'oggetto per il `TableAdapter.Update` (metodo).  
  
     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>Per eliminare i record esistenti da un database  
  
- Eliminare i record chiamando il `TableAdapter.Delete` metodo e passando i valori originali per individuare il record.  
  
    > [!NOTE]
    >  L'oggetto deve mantenere i valori originali per passarli al `Delete` (metodo). Questo esempio Usa le proprietà con un `orig` prefisso per archiviare i valori originali.  
  
     L'esempio seguente elimina un record dal `Customers` passando i valori originali nella tabella di `Customer` dell'oggetto per il `TableAdapter.Delete` (metodo).  
  
     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 È necessario disporre dell'autorizzazione per eseguire l'istruzione INSERT selezionata, UPDATE o DELETE sulla tabella nel database.  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
