---
title: Inserire nuovi record in un database | Microsoft Docs
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c686a764f42f50a3e59da3e8b37b219ddb7b11c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651553"
---
# <a name="insert-new-records-into-a-database"></a>Inserire nuovi record in un database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per inserire nuovi record in un database, è possibile usare il `TableAdapter.Update` metodo o uno dei metodi DBDirect del TableAdapter (in particolare il `TableAdapter.Insert` metodo).

 Se l'applicazione non usa TableAdapter, è possibile usare gli oggetti comando (ad esempio,  <xref:System.Data.SqlClient.SqlCommand> ) per inserire nuovi record nel database.

 Se l'applicazione usa set di dati per archiviare i dati, usare il `TableAdapter.Update` metodo. Il `Update` metodo invia tutte le modifiche (aggiornamenti, inserimenti ed eliminazioni) al database.

 Se l'applicazione utilizza oggetti per archiviare i dati o se si desidera un controllo più preciso sulla creazione di nuovi record nel database, utilizzare il `TableAdapter.Insert` metodo.

 Se il TableAdapter non dispone `Insert` di un metodo, significa che l'oggetto TableAdapter è configurato per l'utilizzo di stored procedure o la relativa `GenerateDBDirectMethods` proprietà è impostata su `false` . Provare a impostare la proprietà del TableAdapter `GenerateDBDirectMethods` su `true` dall'interno del Progettazione DataSet, quindi salvare il set di dati. Il TableAdapter verrà rigenerato. Se il TableAdapter non dispone ancora `Insert` di un metodo, la tabella probabilmente non fornisce informazioni sullo schema sufficienti per distinguere le singole righe. ad esempio, nella tabella potrebbe non essere impostata alcuna chiave primaria.

## <a name="insert-new-records-by-using-tableadapters"></a>Inserire nuovi record usando oggetti TableAdapter
 Gli oggetti TableAdapter forniscono diversi modi per inserire nuovi record in un database, a seconda dei requisiti dell'applicazione.

 Se l'applicazione usa set di dati per archiviare i dati, è sufficiente aggiungere nuovi record alla classe desiderata <xref:System.Data.DataTable> nel set di dati, quindi chiamare il `TableAdapter.Update` metodo. Il `TableAdapter.Update` metodo invia le modifiche all'oggetto <xref:System.Data.DataTable> al database (inclusi i record modificati ed eliminati).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Per inserire nuovi record in un database utilizzando il metodo TableAdapter. Update

1. Aggiungere nuovi record al desiderato <xref:System.Data.DataTable> creando un nuovo oggetto <xref:System.Data.DataRow> e aggiungendolo alla <xref:System.Data.DataTable.Rows%2A> raccolta. Per altre informazioni, vedere [procedura: aggiungere righe a un oggetto DataTable](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).

2. Una volta aggiunte le nuove righe a <xref:System.Data.DataTable> , chiamare il `TableAdapter.Update` metodo. È possibile controllare la quantità di dati da aggiornare passando un intero <xref:System.Data.DataSet> , un oggetto <xref:System.Data.DataTable> , una matrice di <xref:System.Data.DataRow> s o un singolo <xref:System.Data.DataRow> .

    Nel codice seguente viene illustrato come aggiungere un nuovo record a un oggetto <xref:System.Data.DataTable> e quindi chiamare il `TableAdapter.Update` metodo per salvare la nuova riga nel database. In questo esempio viene utilizzata la `Region` tabella nel database Northwind.

    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]

   Se l'applicazione utilizza oggetti per archiviare i dati, è possibile utilizzare il `TableAdapter.Insert` metodo per creare nuove righe direttamente nel database. Il `Insert` metodo accetta i singoli valori per ogni colonna come parametri. La chiamata al metodo consente di inserire un nuovo record nel database con i valori dei parametri passati.

   Nella procedura riportata di seguito viene utilizzata `Region` come esempio la tabella nel database Northwind.

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Per inserire nuovi record in un database utilizzando il metodo TableAdapter. Insert

- Chiamare il metodo del TableAdapter `Insert` , passando i valori per ogni colonna come parametri.

    > [!NOTE]
    > Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

## <a name="insert-new-records-by-using-command-objects"></a>Inserire nuovi record usando oggetti Command
 Nell'esempio seguente vengono inseriti nuovi record direttamente in un database utilizzando gli oggetti Command.

 Nella procedura riportata di seguito viene utilizzata `Region` come esempio la tabella nel database Northwind.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Per inserire nuovi record in un database tramite oggetti Command

- Creare un nuovo oggetto Command, quindi impostare le relative `Connection` `CommandType` proprietà, e `CommandText` .

     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]

## <a name="net-framework-security"></a>Sicurezza di .NET Framework
 È necessario disporre dell'accesso al database a cui si sta tentando di connettersi, nonché dell'autorizzazione per l'esecuzione di inserimenti nella tabella desiderata.

## <a name="see-also"></a>Vedere anche
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
