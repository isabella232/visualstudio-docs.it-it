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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b54aeb91ea873b23b1e68731e40542df04fcbd01
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648118"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aggiornare i dati mediante un TableAdapter

Una volta che i dati nel set di dati sono stati modificati e convalidati, è possibile inviare di nuovo i dati aggiornati a un database chiamando il metodo `Update` di un [TableAdapter](../data-tools/create-and-configure-tableadapters.md). Il metodo `Update` aggiorna una singola tabella dati ed esegue il comando corretto (INSERT, UPDATE o DELETE) in base al <xref:System.Data.DataRow.RowState%2A> di ogni riga di dati nella tabella. Quando un set di dati include tabelle correlate, Visual Studio genera una classe TableAdapterManager da usare per eseguire gli aggiornamenti. La classe TableAdapterManager garantisce che gli aggiornamenti vengano eseguiti nell'ordine corretto in base ai vincoli FOREIGN KEY definiti nel database. Quando si utilizzano i controlli associati a dati, l'architettura DataBinding crea una variabile membro della classe TableAdapterManager denominata tableAdapterManager.

> [!NOTE]
> Quando si tenta di aggiornare un'origine dati con il contenuto di un set di dati, è possibile ottenere errori. Per evitare errori, è consigliabile inserire il codice che chiama il metodo di `Update` dell'adapter all'interno di un blocco `catch` / `try`.

La procedura esatta per l'aggiornamento di un'origine dati può variare a seconda delle esigenze aziendali, ma prevede i passaggi seguenti:

1. Chiamare il metodo `Update` dell'adapter in un blocco `catch` / `try`.

2. Se viene rilevata un'eccezione, individuare la riga di dati che ha causato l'errore.

3. Riconciliare il problema nella riga di dati (a livello di codice, se è possibile, o presentando la riga non valida all'utente per la modifica), quindi riprovare a eseguire l'aggiornamento (<xref:System.Data.DataRow.HasErrors%2A> <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Salvare i dati in un database

Chiamare il metodo `Update` di un TableAdapter. Passare il nome della tabella dati contenente i valori da scrivere nel database.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Per aggiornare un database utilizzando un TableAdapter

- Racchiudere il metodo `Update` del TableAdapter in un blocco di `catch` / `try`. Nell'esempio seguente viene illustrato come aggiornare il contenuto della tabella `Customers` in `NorthwindDataSet` all'interno di un blocco `try` / `catch`.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)