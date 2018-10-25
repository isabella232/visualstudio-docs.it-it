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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: aae5ec2197ff2a899f27df20e7199fdeb7a02d31
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949201"
---
# <a name="insert-new-records-into-a-database"></a>Inserire nuovi record in un database

Per inserire nuovi record in un database, è possibile usare la `TableAdapter.Update` metodo, o uno dei metodi DBDirect di TableAdapter (in particolare il `TableAdapter.Insert` (metodo)). Per altre informazioni, vedere [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Se l'applicazione non usa gli oggetti TableAdapter, è possibile usare gli oggetti comando (ad esempio, <xref:System.Data.SqlClient.SqlCommand>) per inserire nuovi record nel database.

Se l'applicazione usa set di dati per archiviare i dati, usare il `TableAdapter.Update` (metodo). Il `Update` metodo invia tutte le modifiche (aggiornamenti, inserimenti ed eliminazioni) nel database.

Se l'applicazione usa gli oggetti per archiviare i dati oppure, se si desidera un maggiore controllo sulla creazione di nuovi record nel database, utilizzare il `TableAdapter.Insert` (metodo).

Se l'oggetto TableAdapter non ha un `Insert` metodo, significa che il TableAdapter sia configurato per utilizzare le stored procedure o dai relativi `GenerateDBDirectMethods` è impostata su `false`. Provare a impostare dell'oggetto TableAdapter `GenerateDBDirectMethods` proprietà `true` dall'interno di **Progettazione Dataset**e quindi salvare il set di dati. Questa operazione rigenererà il TableAdapter. Se l'oggetto TableAdapter non ancora un `Insert` metodo, la tabella non vengono fornite informazioni sufficienti dello schema per distinguere tra le singole righe (ad esempio, non potrebbe esserci alcun set di chiavi primarie nella tabella).

## <a name="insert-new-records-by-using-tableadapters"></a>Inserire nuovi record usando oggetti TableAdapter

Gli oggetti TableAdapter forniscono diversi modi per inserire nuovi record in un database, a seconda dei requisiti dell'applicazione.

Se l'applicazione usa set di dati per archiviare i dati, è possibile aggiungere semplicemente i nuovi record per il valore desiderato <xref:System.Data.DataTable> nel set di dati e quindi chiamare il `TableAdapter.Update` (metodo). Il `TableAdapter.Update` metodo invia tutte le modifiche <xref:System.Data.DataTable> al database (inclusi i record modificati ed eliminati).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Per inserire nuovi record in un database usando il metodo di TableAdapter

1. Aggiungere nuovi record per il valore desiderato <xref:System.Data.DataTable> creando un nuovo <xref:System.Data.DataRow> e aggiungendolo al <xref:System.Data.DataTable.Rows%2A> raccolta.

2. Dopo aver aggiunto le nuove righe per il <xref:System.Data.DataTable>, chiamare il `TableAdapter.Update` (metodo). È possibile controllare la quantità di dati da aggiornare passando un un'intera <xref:System.Data.DataSet>, una <xref:System.Data.DataTable>, una matrice di <xref:System.Data.DataRow>s o un singolo <xref:System.Data.DataRow>.

   Il codice seguente viene illustrato come aggiungere un nuovo record a un <xref:System.Data.DataTable> e quindi chiamare il `TableAdapter.Update` metodo per salvare la nuova riga per il database. (Questo esempio viene usato il `Region` tabella nel database Northwind.)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Per inserire nuovi record in un database usando il metodo di TableAdapter

Se l'applicazione usa gli oggetti per archiviare i dati, è possibile usare il `TableAdapter.Insert` metodo per creare nuove righe direttamente nel database. Il `Insert` metodo accetta i singoli valori per ogni colonna come parametri. La chiamata al metodo inserisce un nuovo record nel database con i valori dei parametri passati.

- Chiamata dell'oggetto TableAdapter `Insert` , passando i valori per ogni colonna come parametri.

La procedura seguente illustra l'uso di `TableAdapter.Insert` metodo per inserire righe. In questo esempio inserisce dati nella `Region` tabella nel database Northwind.

> [!NOTE]
> Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Inserire nuovi record con gli oggetti comando

È possibile inserire nuovi record direttamente in un database utilizzando oggetti command.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Per inserire nuovi record in un database utilizzando oggetti comando

- Creare un nuovo oggetto comando e quindi impostare relativi `Connection`, `CommandType`, e `CommandText` proprietà.

Nell'esempio seguente viene illustrato l'inserimento di record in un database utilizzando l'oggetto comando. Inserisce i dati nel `Region` tabella nel database Northwind.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-framework-security"></a>.NET Framework (sicurezza)

È necessario avere accesso a si sta tentando di connettersi al database, nonché dell'autorizzazione per eseguire l'inserimento nella tabella desiderata.

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)