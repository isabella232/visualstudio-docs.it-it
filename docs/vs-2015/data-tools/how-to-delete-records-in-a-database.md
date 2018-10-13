---
title: 'Procedura: eliminare i record in un Database | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- records, deleting
- TableAdapter.Delete method
- databases, deleting records
- deleting data
- TableAdapter.Update method
- saving data
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: aff5a67d54376488ccce2bca5dd67b84d6c73949
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210184"
---
# <a name="how-to-delete-records-in-a-database"></a>Procedura: eliminare record da un database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per eliminare i record da un database, usare il `TableAdapter.Update` metodo o il `TableAdapter.Delete` (metodo). O, se l'applicazione non usa gli oggetti TableAdapter, è possibile usare gli oggetti comando per eliminare i record da un database (ad esempio, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
 Il `TableAdapter.Update` metodo viene in genere utilizzato quando l'applicazione usa set di dati per archiviare i dati, mentre il `TableAdapter.Delete` metodo viene in genere utilizzato quando l'applicazione usa gli oggetti per archiviare i dati.  
  
 Se l'oggetto TableAdapter non dispone di un `Delete` metodo, significa che il TableAdapter è configurato per utilizzare le stored procedure, o dai relativi `GenerateDBDirectMethods` è impostata su `false`. Provare a impostare dell'oggetto TableAdapter `GenerateDBDirectMethods` proprietà `true` dall'interno di [Progettazione Dataset](../data-tools/creating-and-editing-typed-datasets.md) e quindi salvare il set di dati per rigenerare il TableAdapter. Se l'oggetto TableAdapter non è ancora presente un `Delete` (metodo), quindi la tabella non vengono fornite informazioni sufficienti dello schema per distinguere tra le singole righe (ad esempio, alcuna chiave primaria non è impostata sulla tabella).  
  
## <a name="delete-records-using-tableadapters"></a>Eliminare i record usando oggetti TableAdapter  
 Gli oggetti TableAdapter forniscono diversi modi per eliminare i record da un database a seconda dei requisiti dell'applicazione.  
  
 Se l'applicazione usa set di dati per archiviare i dati è possibile semplicemente eliminare i record da desiderato <xref:System.Data.DataTable> nella <xref:System.Data.DataSet>, quindi chiamare il `TableAdapter.Update` (metodo). Il `TableAdapter.Update` metodo accetta tutte le modifiche nella tabella di dati e invia le modifiche al database (inclusi i record inseriti, aggiornati ed eliminati).  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterupdate-method"></a>Per eliminare i record da un database utilizzando il metodo di TableAdapter  
  
-   Eliminare i record dall'oggetto desiderato <xref:System.Data.DataTable> eliminando <xref:System.Data.DataRow> oggetti dalla tabella. Per altre informazioni, vedere [procedura: eliminare righe in un oggetto DataTable](http://msdn.microsoft.com/library/add481e5-08c7-4923-9276-f036ae29d31e). Dopo che le righe vengono eliminate dal <xref:System.Data.DataTable>, chiamare il `TableAdapter.Update` (metodo). È possibile controllare la quantità di dati da aggiornare tramite il passaggio di un'intera <xref:System.Data.DataSet>, una <xref:System.Data.DataTable>, una matrice di <xref:System.Data.DataRow>s o un singolo <xref:System.Data.DataRow>. Il codice seguente viene illustrato come eliminare un record da un <xref:System.Data.DataTable> e quindi chiamare il `TableAdapter.Update` metodo per comunicare la modifica ed eliminare la riga dal database. (In questo esempio viene utilizzato il database di Northwind `Region` tabella.)  
  
     [!code-csharp[VbRaddataSaving#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#20)]
     [!code-vb[VbRaddataSaving#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#20)]  
  
 Se l'applicazione usa gli oggetti per archiviare i dati nell'applicazione, è possibile usare i metodi DBDirect di TableAdapter per eliminare i dati direttamente dal database. La chiamata di `Delete` metodo rimuove i record dal database in base ai valori di parametro passati.  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterdelete-method"></a>Per eliminare i record da un database utilizzando il metodo di TableAdapter  
  
-   Chiamata dell'oggetto TableAdapter `Delete` , passando i valori per ogni colonna come parametri del `Delete` (metodo). (In questo esempio viene utilizzato il database di Northwind `Region` tabella.)  
  
    > [!NOTE]
    >  Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="delete-records-using-command-objects"></a>Eliminare i record usando gli oggetti comando  
 Nell'esempio seguente elimina i record direttamente da un database utilizzando oggetti command. Per altre informazioni sull'utilizzo degli oggetti comando per eseguire comandi e le stored procedure, vedere [recupero di dati in Your Application](../data-tools/fetching-data-into-your-application.md).  
  
#### <a name="to-delete-records-from-a-database-using-command-objects"></a>Per eliminare i record da un database utilizzando oggetti comando  
  
-   Creare un nuovo oggetto comando, impostare relativi `Connection`, `CommandType`, e `CommandText` proprietà. (In questo esempio viene utilizzato il database di Northwind `Region` tabella.)  
  
     [!code-csharp[VbRaddataSaving#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#22)]
     [!code-vb[VbRaddataSaving#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#22)]  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 È necessario avere accesso a si sta tentando di connettersi al database, nonché dell'autorizzazione per eliminare i record dalla tabella desiderata.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Inserire nuovi record in un database](../data-tools/insert-new-records-into-a-database.md)   
 [Procedura: aggiornare record in un Database](../data-tools/how-to-update-records-in-a-database.md)   
 [Salvare i dati da un oggetto in un database](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Panoramica delle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio di dati](../data-tools/saving-data.md)