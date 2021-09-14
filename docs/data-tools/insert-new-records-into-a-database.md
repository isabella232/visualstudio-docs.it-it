---
title: Inserire nuovi record in un database
description: Inserire nuovi record in un database usando il metodo TableAdapter.Update, uno dei metodi DBDirect del TableAdapter o oggetti comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7b3fbea039c82210c135b26c918ca18c757816b5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631290"
---
# <a name="insert-new-records-into-a-database"></a>Inserire nuovi record in un database

Per inserire nuovi record in un database, è possibile usare il metodo o uno dei metodi DBDirect del `TableAdapter.Update` TableAdapter (in particolare il `TableAdapter.Insert` metodo ). Per altre informazioni, vedere [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Se l'applicazione non usa TableAdapter, è possibile usare oggetti comando (ad esempio , ) per inserire  <xref:System.Data.SqlClient.SqlCommand> nuovi record nel database.

Se l'applicazione usa set di dati per archiviare i dati, usare il `TableAdapter.Update` metodo . Il `Update` metodo invia tutte le modifiche (aggiornamenti, inserimenti ed eliminazioni) al database.

Se l'applicazione usa oggetti per archiviare i dati o se si vuole un controllo più fine sulla creazione di nuovi record nel database, usare il `TableAdapter.Insert` metodo .

Se l'oggetto TableAdapter non dispone di un metodo, significa che l'oggetto TableAdapter è configurato per l'uso di stored procedure o che la relativa proprietà `Insert` `GenerateDBDirectMethods` è impostata su `false` . Provare a impostare la proprietà del TableAdapter `GenerateDBDirectMethods` su `true` dall'Progettazione DataSet e quindi salvare il set di dati.  Verrà rigenerato l'oggetto TableAdapter. Se l'oggetto TableAdapter non dispone ancora di un metodo , è probabile che la tabella non fornirà informazioni di schema sufficienti per distinguere le singole righe(ad esempio, potrebbe non essere impostata alcuna chiave primaria `Insert` nella tabella).

## <a name="insert-new-records-by-using-tableadapters"></a>Inserire nuovi record tramite TableAdapter

Gli oggetti TableAdapter offrono diversi modi per inserire nuovi record in un database, a seconda dei requisiti dell'applicazione.

Se l'applicazione usa set di dati per archiviare i dati, è sufficiente aggiungere nuovi record al set di dati desiderato <xref:System.Data.DataTable> e quindi chiamare il metodo `TableAdapter.Update` . Il `TableAdapter.Update` metodo invia al database le modifiche apportate a , inclusi i record modificati ed <xref:System.Data.DataTable> eliminati.

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Per inserire nuovi record in un database tramite il metodo TableAdapter.Update

1. Aggiungere nuovi record <xref:System.Data.DataTable> all'oggetto desiderato creando un nuovo <xref:System.Data.DataRow> record e aggiungendolo alla <xref:System.Data.DataTable.Rows%2A> raccolta.

2. Dopo aver aggiunto le nuove righe a <xref:System.Data.DataTable> , chiamare il metodo `TableAdapter.Update` . È possibile controllare la quantità di dati da aggiornare passando un intero , un , una matrice di <xref:System.Data.DataSet> <xref:System.Data.DataTable> o un singolo <xref:System.Data.DataRow> <xref:System.Data.DataRow> .

   Il codice seguente illustra come aggiungere un nuovo record a e quindi chiamare il metodo per <xref:System.Data.DataTable> salvare la nuova riga nel `TableAdapter.Update` database. In questo esempio viene `Region` utilizzata la tabella nel database Northwind.

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb" id="Snippet14":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs" id="Snippet14":::

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Per inserire nuovi record in un database tramite il metodo TableAdapter.Insert

Se l'applicazione usa oggetti per archiviare i dati, è possibile usare il metodo per `TableAdapter.Insert` creare nuove righe direttamente nel database. Il `Insert` metodo accetta i singoli valori per ogni colonna come parametri. La chiamata al metodo inserisce un nuovo record nel database con i valori dei parametri passati.

- Chiamare il metodo del `Insert` TableAdapter, passando i valori per ogni colonna come parametri.

Nella procedura seguente viene illustrato l'uso `TableAdapter.Insert` del metodo per inserire righe. In questo esempio vengono inseriti dati `Region` nella tabella del database Northwind.

> [!NOTE]
> Se non è disponibile un'istanza di , creare un'istanza del TableAdapter che si vuole usare.

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

## <a name="insert-new-records-by-using-command-objects"></a>Inserire nuovi record usando oggetti comando

È possibile inserire nuovi record direttamente in un database usando oggetti comando.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Per inserire nuovi record in un database usando oggetti comando

- Creare un nuovo oggetto comando e quindi impostarne `Connection` le proprietà , e `CommandType` `CommandText` .

Nell'esempio seguente viene illustrato l'inserimento di record in un database tramite l'oggetto comando . Inserisce i dati nella `Region` tabella nel database Northwind.

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet16":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet16":::

## <a name="net-security"></a>Protezione .NET

È necessario avere accesso al database a cui si sta tentando di connettersi, nonché l'autorizzazione per eseguire inserimenti nella tabella desiderata.

## <a name="see-also"></a>Vedi anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
