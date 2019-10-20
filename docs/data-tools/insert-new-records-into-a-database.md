---
title: Inserire nuovi record in un database
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aaca23e6aa81fab958fc813fa5e2331f8906a562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648311"
---
# <a name="insert-new-records-into-a-database"></a>Inserire nuovi record in un database

Per inserire nuovi record in un database, è possibile usare il metodo `TableAdapter.Update` o uno dei metodi DBDirect del TableAdapter (in particolare il metodo `TableAdapter.Insert`). Per ulteriori informazioni, vedere [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Se l'applicazione non usa TableAdapter, è possibile usare gli oggetti comando (ad esempio, <xref:System.Data.SqlClient.SqlCommand>) per inserire nuovi record nel database.

Se l'applicazione usa set di dati per archiviare i dati, usare il metodo `TableAdapter.Update`. Il metodo `Update` Invia tutte le modifiche (aggiornamenti, inserimenti ed eliminazioni) al database.

Se l'applicazione utilizza oggetti per archiviare i dati o se si desidera un controllo più preciso sulla creazione di nuovi record nel database, utilizzare il metodo `TableAdapter.Insert`.

Se il TableAdapter non dispone di un metodo di `Insert`, significa che l'oggetto TableAdapter è configurato per l'utilizzo di stored procedure o la relativa proprietà `GenerateDBDirectMethods` è impostata su `false`. Provare a impostare la proprietà `GenerateDBDirectMethods` del TableAdapter su `true` all'interno del **Progettazione DataSet**, quindi salvare il set di dati. Il TableAdapter verrà rigenerato. Se il TableAdapter non dispone ancora di un metodo di `Insert`, è probabile che la tabella non fornisca informazioni dello schema sufficienti per distinguere le singole righe. ad esempio, nella tabella potrebbe non essere impostata alcuna chiave primaria.

## <a name="insert-new-records-by-using-tableadapters"></a>Inserire nuovi record usando oggetti TableAdapter

Gli oggetti TableAdapter forniscono diversi modi per inserire nuovi record in un database, a seconda dei requisiti dell'applicazione.

Se l'applicazione usa set di dati per archiviare i dati, è sufficiente aggiungere nuovi record ai <xref:System.Data.DataTable> desiderati nel set di dati, quindi chiamare il metodo `TableAdapter.Update`. Il metodo `TableAdapter.Update` Invia tutte le modifiche apportate al <xref:System.Data.DataTable> al database (inclusi i record modificati ed eliminati).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Per inserire nuovi record in un database utilizzando il metodo TableAdapter. Update

1. Aggiungere nuovi record alla <xref:System.Data.DataTable> desiderata creando una nuova <xref:System.Data.DataRow> e aggiungendola alla raccolta <xref:System.Data.DataTable.Rows%2A>.

2. Quando le nuove righe vengono aggiunte alla <xref:System.Data.DataTable>, chiamare il metodo `TableAdapter.Update`. È possibile controllare la quantità di dati da aggiornare passando un intero <xref:System.Data.DataSet>, un <xref:System.Data.DataTable>, una matrice di <xref:System.Data.DataRow>s o un singolo <xref:System.Data.DataRow>.

   Nel codice seguente viene illustrato come aggiungere un nuovo record a un <xref:System.Data.DataTable> e quindi chiamare il metodo `TableAdapter.Update` per salvare la nuova riga nel database. In questo esempio viene utilizzata la tabella `Region` nel database Northwind.

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Per inserire nuovi record in un database utilizzando il metodo TableAdapter. Insert

Se l'applicazione usa oggetti per archiviare i dati, è possibile usare il metodo `TableAdapter.Insert` per creare nuove righe direttamente nel database. Il metodo `Insert` accetta i singoli valori per ogni colonna come parametri. La chiamata al metodo consente di inserire un nuovo record nel database con i valori dei parametri passati.

- Chiamare il metodo `Insert` del TableAdapter, passando i valori per ogni colonna come parametri.

Nella procedura riportata di seguito viene illustrato l'utilizzo del metodo `TableAdapter.Insert` per inserire righe. In questo esempio vengono inseriti i dati nella tabella `Region` del database Northwind.

> [!NOTE]
> Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Inserire nuovi record usando oggetti Command

È possibile inserire nuovi record direttamente in un database utilizzando gli oggetti Command.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Per inserire nuovi record in un database tramite oggetti Command

- Creare un nuovo oggetto Command, quindi impostarne le proprietà `Connection`, `CommandType` e `CommandText`.

Nell'esempio seguente viene illustrato l'inserimento di record in un database utilizzando l'oggetto Command. Inserisce i dati nella tabella `Region` del database Northwind.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>Protezione .NET

È necessario disporre dell'accesso al database a cui si sta tentando di connettersi, nonché dell'autorizzazione per l'esecuzione di inserimenti nella tabella desiderata.

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)