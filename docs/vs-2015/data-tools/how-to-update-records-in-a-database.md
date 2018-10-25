---
title: 'Procedura: aggiornare record in un Database | Microsoft Docs'
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
- records, updating
- data [Visual Studio], saving
- records, editing
- databases, updating
- TableAdapter.Update method
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b62dc86425dcbebb225c66eecd51505f674e20ec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949032"
---
# <a name="how-to-update-records-in-a-database"></a>Procedura: aggiornare record in un database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare il `TableAdapter.Update` metodo ai record di aggiornamento (modifica) in un database. Il `TableAdapter.Update` metodo fornisce diversi overload che eseguono operazioni diverse a seconda dei parametri passati. È importante comprendere i risultati della chiamata queste firme dei metodi diversi.  
  
> [!NOTE]
>  Se l'applicazione non utilizza la classe TableAdapter, quindi è possibile usare gli oggetti comando per aggiornare i record nel database (ad esempio, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>). Per altre informazioni sull'aggiornamento dei dati con gli oggetti comando, vedere "Aggiornamento record mediante gli oggetti comando" di seguito.  
  
 La tabella seguente descrive il comportamento dei vari `TableAdapter.Update` metodi:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`TableAdapter.Update(DataTable)`|Tenta di salvare tutte le modifiche nel <xref:System.Data.DataTable> al database. (Questo include la rimozione delle righe eliminate dalla tabella, aggiungere le righe inserite nella tabella e aggiornare tutte le righe nella tabella che sono state modificate).|  
|`TableAdapter.Update(DataSet)`|Anche se il parametro accetta un set di dati, il TableAdapter tenta di salvare tutte le modifiche nell'oggetto TableAdapter associato al <xref:System.Data.DataTable> al database. (Questo include la rimozione delle righe eliminate dalla tabella, aggiungere le righe inserite nella tabella e aggiornare tutte le righe nella tabella che sono state modificate). **Nota:** un oggetto TableAdapter associato <xref:System.Data.DataTable> è il <xref:System.Data.DataTable> creato quando è stato originariamente configurato TableAdapter.|  
|`TableAdapter.Update(DataRow)`|Tenta di salvare le modifiche in indicato <xref:System.Data.DataRow> al database.|  
|`TableAdapter.Update(DataRows())`|Tenta di salvare le modifiche in qualsiasi riga nella matrice di <xref:System.Data.DataRow>s per il database.|  
|`TableAdapter.Update("new column values", "original column values")`|È stato effettuato un tentativo di salvare le modifiche in una singola riga identificata dai valori della colonna originale.|  
  
 In genere si usa la `TableAdapter.Update` metodo che accetta una <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o <xref:System.Data.DataRow>(s) quando l'applicazione usa set di dati in modo esclusivo per archiviare i dati.  
  
 In genere si usa il `TableAdapter.Update` metodo che accetta i valori di colonna quando l'applicazione usa gli oggetti per archiviare i dati.  
  
 Se l'oggetto TableAdapter non dispone di un `Update` metodo che accetta i valori di colonna, quindi significa che il TableAdapter sia configurato per utilizzare le stored procedure o dai relativi `GenerateDBDirectMethods` è impostata su `false`. Provare a impostare dell'oggetto TableAdapter `GenerateDBDirectMethods` proprietà `true` dall'interno di [Progettazione Dataset](../data-tools/creating-and-editing-typed-datasets.md) e quindi salvare il set di dati per rigenerare il TableAdapter. Se l'oggetto TableAdapter non è ancora presente un `Update` metodo che accetta i valori di colonna, quindi la tabella probabilmente non fornisce informazioni sufficienti dello schema per distinguere tra le singole righe (ad esempio, alcuna chiave primaria non è impostata sulla tabella).  
  
## <a name="update-existing-records-using-tableadapters"></a>Aggiornare i record esistenti usando oggetti TableAdapter  
 Gli oggetti TableAdapter forniscono diversi modi per aggiornare i record in un database a seconda dei requisiti dell'applicazione.  
  
 Se l'applicazione usa set di dati per archiviare i dati, quindi è possibile limitarsi ad aggiornare i record nell'oggetto desiderato <xref:System.Data.DataTable> e quindi chiamare il `TableAdapter.Update` metodo e passare la <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, o una matrice di <xref:System.Data.DataRow>s. Nella tabella precedente vengono descritti i diversi `Update` metodi.  
  
#### <a name="to-update-records-in-a-database-with-the-tableadapterupdate-method-that-takes-dataset-datatable-datarow-or-datarows"></a>Per aggiornare i record in un database con il metodo TableAdapter che accetta i set di dati, DataTable, DataRow o DataRows)  
  
1. Modificare i record nell'oggetto desiderato <xref:System.Data.DataTable> modificando direttamente il <xref:System.Data.DataRow> nel <xref:System.Data.DataTable>. Per altre informazioni, vedere [procedura: modifica di righe in un oggetto DataTable](http://msdn.microsoft.com/library/d5eea200-9bfa-4956-bf7c-08dd6fb6663c).  
  
2. Dopo la modifica delle righe nel <xref:System.Data.DataTable>, chiamare il `TableAdapter.Update` (metodo). È possibile controllare la quantità di dati da aggiornare passando un un'intera <xref:System.Data.DataSet>, una <xref:System.Data.DataTable>, una matrice di <xref:System.Data.DataRow>s o un singolo <xref:System.Data.DataRow>.  
  
    Il codice seguente viene illustrato come modificare un record in una <xref:System.Data.DataTable> e quindi chiamare il `TableAdapter.Update` metodo per salvare le modifiche al database. (In questo esempio Usa la tabella Region del database Northwind).  
  
    [!code-csharp[VbRaddataSaving#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#17)]
    [!code-vb[VbRaddataSaving#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#17)]  
  
   Se l'applicazione usa gli oggetti per archiviare i dati nell'applicazione, è possibile usare dell'oggetto TableAdapter `DBDirect` metodi per inviare dati da oggetti direttamente al database. Questi metodi consentono di passare i singoli valori per ogni colonna come parametri del metodo. Chiamare questo metodo aggiorna un record esistente nel database con i valori della colonna passati al metodo.  
  
   La procedura seguente usa Northwind `Region` tabella come esempio.  
  
#### <a name="to-update-records-in-a-database-using-the-tableadapterupdate-method-that-takes-column-values"></a>Per aggiornare i record in un database usando il metodo TableAdapter che accetta i valori di colonna  
  
-   Chiamata dell'oggetto TableAdapter `Update` , passando i valori originale e nuovi per ogni colonna come parametri.  
  
    > [!NOTE]
    >  Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
## <a name="update-records-using-command-objects"></a>Aggiornare i record usando gli oggetti comando  
 Nell'esempio seguente aggiorna i record esistenti direttamente in un database utilizzando oggetti command. Per altre informazioni sull'utilizzo degli oggetti comando per eseguire comandi e le stored procedure, vedere [recupero di dati in Your Application](../data-tools/fetching-data-into-your-application.md).  
  
 La procedura seguente usa Northwind `Region` tabella come esempio.  
  
#### <a name="to-update-existing-records-in-a-database-using-command-objects"></a>Per aggiornare i record esistenti in un database utilizzando oggetti command  
  
-   Creare un nuovo oggetto comando; impostare relativi `Connection`, `CommandType`, e `CommandText` proprietà; e quindi aprire una connessione ed eseguire il comando.  
  
     [!code-csharp[VbRaddataSaving#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#19)]
     [!code-vb[VbRaddataSaving#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#19)]  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 È necessario avere accesso a si sta tentando di connettersi al database, nonché dell'autorizzazione per aggiornare i record della tabella desiderata.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: eliminare i record in un Database](../data-tools/how-to-delete-records-in-a-database.md)   
 [Inserire nuovi record in un database](../data-tools/insert-new-records-into-a-database.md)   
 [Salvare i dati da un oggetto in un database](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Panoramica delle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio di dati](../data-tools/saving-data.md)