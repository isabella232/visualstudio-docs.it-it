---
title: Aggiornare i dati mediante un TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 88d4da868174396bfed148fc6088e5675e1198b2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37116893"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aggiornare i dati mediante un TableAdapter

Dopo aver modificati i dati nel set di dati e convalidati, è possibile inviare i dati aggiornati in un database chiamando il `Update` metodo di un [TableAdapter](../data-tools/create-and-configure-tableadapters.md). Il `Update` metodo aggiorna una singola tabella di dati ed esegue il comando corretto (INSERT, UPDATE o DELETE) in base il <xref:System.Data.DataRow.RowState%2A> di ogni riga di dati nella tabella. Quando un set di dati dispone di tabelle correlate, Visual Studio genera una classe di TableAdapterManager utilizzabili per eseguire gli aggiornamenti. La classe di TableAdapterManager assicura che gli aggiornamenti vengono eseguiti nell'ordine corretto in base ai vincoli di chiave esterna che sono definiti nel database. Quando si usano controlli associati a dati, l'architettura di Data Binding crea una variabile membro della classe TableAdapterManager chiamata tableAdapterManager.

> [!NOTE]
> Quando si tenta di aggiornare un'origine dati con il contenuto di un set di dati, è possibile ottenere gli errori. Per evitare errori, è consigliabile inserire il codice che chiama l'adapter `Update` metodo all'interno di un `try` / `catch` blocco.

 La procedura esatta per l'aggiornamento di un'origine dati può variare a seconda delle esigenze aziendali, ma i passaggi seguenti:

1.  Chiamare l'adattatore `Update` metodo in un `try` / `catch` blocco.

2.  Se viene rilevata un'eccezione, individuare la riga di dati che ha causato l'errore.

3.  Risolvere il problema nei dati di riga (a livello di codice se possibile, o presentando la riga non valida per l'utente per la modifica) e quindi ripetere l'operazione di aggiornamento (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Salvare i dati in un database

Chiamare il `Update` metodo di un oggetto TableAdapter. Passare il nome della tabella dati contenente i valori da scrivere nel database.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Per aggiornare un database mediante un TableAdapter

-   Racchiudere dell'oggetto TableAdapter`Update` metodo in un `try` / `catch` blocco. Nell'esempio seguente viene illustrato come aggiornare il contenuto del `Customers` nella tabella `NorthwindDataSet` dall'interno una `try` / `catch` blocco.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)