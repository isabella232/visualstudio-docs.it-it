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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651553"
---
# <a name="insert-new-records-into-a-database"></a>Inserire nuovi record in un database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per inserire nuovi record in un database, è possibile usare il metodo `TableAdapter.Update` o uno dei metodi DBDirect del TableAdapter (in particolare il metodo `TableAdapter.Insert`).

 Se l'applicazione non usa TableAdapter, è possibile usare gli oggetti comando (ad esempio, <xref:System.Data.SqlClient.SqlCommand>) per inserire nuovi record nel database.

 Se l'applicazione usa set di dati per archiviare i dati, usare il metodo `TableAdapter.Update`. Il metodo `Update` Invia tutte le modifiche (aggiornamenti, inserimenti ed eliminazioni) al database.

 Se l'applicazione utilizza oggetti per archiviare i dati o se si desidera un controllo più preciso sulla creazione di nuovi record nel database, utilizzare il metodo `TableAdapter.Insert`.

 Se il TableAdapter non dispone di un metodo di `Insert`, significa che l'oggetto TableAdapter è configurato per l'utilizzo di stored procedure o la relativa proprietà `GenerateDBDirectMethods` è impostata su `false`. Provare a impostare la proprietà `GenerateDBDirectMethods` del TableAdapter su `true` all'interno del Progettazione DataSet, quindi salvare il set di dati. Il TableAdapter verrà rigenerato. Se il TableAdapter non dispone ancora di un metodo di `Insert`, è probabile che la tabella non fornisca informazioni dello schema sufficienti per distinguere le singole righe. ad esempio, nella tabella potrebbe non essere impostata alcuna chiave primaria.

## <a name="insert-new-records-by-using-tableadapters"></a>Inserire nuovi record usando oggetti TableAdapter
 Gli oggetti TableAdapter forniscono diversi modi per inserire nuovi record in un database, a seconda dei requisiti dell'applicazione.

 Se l'applicazione usa set di dati per archiviare i dati, è possibile aggiungere semplicemente nuovi record al <xref:System.Data.DataTable> desiderato nel set di dati e quindi chiamare il metodo `TableAdapter.Update`. Il metodo `TableAdapter.Update` Invia tutte le modifiche apportate al <xref:System.Data.DataTable> al database (inclusi i record modificati ed eliminati).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Per inserire nuovi record in un database utilizzando il metodo TableAdapter. Update

1. Aggiungere nuovi record alla <xref:System.Data.DataTable> desiderata creando una nuova <xref:System.Data.DataRow> e aggiungendola alla raccolta <xref:System.Data.DataTable.Rows%2A>. Per altre informazioni, vedere [procedura: aggiungere righe a un oggetto DataTable](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).

2. Quando le nuove righe vengono aggiunte alla <xref:System.Data.DataTable>, chiamare il metodo `TableAdapter.Update`. È possibile controllare la quantità di dati da aggiornare passando un intero <xref:System.Data.DataSet>, un <xref:System.Data.DataTable>, una matrice di <xref:System.Data.DataRow>s o un singolo <xref:System.Data.DataRow>.

    Nel codice seguente viene illustrato come aggiungere un nuovo record a un <xref:System.Data.DataTable> e quindi chiamare il metodo `TableAdapter.Update` per salvare la nuova riga nel database. In questo esempio viene utilizzata la tabella `Region` nel database Northwind.

    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]

   Se l'applicazione usa oggetti per archiviare i dati, è possibile usare il metodo `TableAdapter.Insert` per creare nuove righe direttamente nel database. Il metodo `Insert` accetta i singoli valori per ogni colonna come parametri. La chiamata al metodo consente di inserire un nuovo record nel database con i valori dei parametri passati.

   Nella procedura riportata di seguito viene utilizzata come esempio la tabella `Region` nel database Northwind.

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Per inserire nuovi record in un database utilizzando il metodo TableAdapter. Insert

- Chiamare il metodo `Insert` del TableAdapter, passando i valori per ogni colonna come parametri.

    > [!NOTE]
    > Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

## <a name="insert-new-records-by-using-command-objects"></a>Inserire nuovi record usando oggetti Command
 Nell'esempio seguente vengono inseriti nuovi record direttamente in un database utilizzando gli oggetti Command.

 Nella procedura riportata di seguito viene utilizzata come esempio la tabella `Region` nel database Northwind.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Per inserire nuovi record in un database tramite oggetti Command

- Creare un nuovo oggetto Command, quindi impostarne le proprietà `Connection`, `CommandType` e `CommandText`.

     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]

## <a name="net-framework-security"></a>Sicurezza di .NET Framework
 È necessario disporre dell'accesso al database a cui si sta tentando di connettersi, nonché dell'autorizzazione per l'esecuzione di inserimenti nella tabella desiderata.

## <a name="see-also"></a>Vedere anche
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
