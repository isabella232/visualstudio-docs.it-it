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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 61ebcd6c833b55f0769365b89274e35136c914f9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925354"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aggiornare i dati mediante un TableAdapter

Una volta che i dati nel set di dati sono stati modificati e convalidati, è possibile inviare di nuovo i dati aggiornati a `Update` un database chiamando il metodo di un [TableAdapter](../data-tools/create-and-configure-tableadapters.md). Il `Update` metodo aggiorna una singola tabella dati ed esegue il comando corretto (Insert, Update o DELETE) in base all'oggetto <xref:System.Data.DataRow.RowState%2A> di ogni riga di dati della tabella. Quando un set di dati include tabelle correlate, Visual Studio genera una classe TableAdapterManager da usare per eseguire gli aggiornamenti. La classe TableAdapterManager garantisce che gli aggiornamenti vengano eseguiti nell'ordine corretto in base ai vincoli FOREIGN KEY definiti nel database. Quando si utilizzano i controlli associati a dati, l'architettura DataBinding crea una variabile membro della classe TableAdapterManager denominata tableAdapterManager.

> [!NOTE]
> Quando si tenta di aggiornare un'origine dati con il contenuto di un set di dati, è possibile ottenere errori. Per evitare errori, è consigliabile inserire il codice che chiama `Update` il metodo dell'adapter all'interno di un `try` / `catch` blocco.

La procedura esatta per l'aggiornamento di un'origine dati può variare a seconda delle esigenze aziendali, ma prevede i passaggi seguenti:

1. Chiamare il `Update` metodo dell'adapter in un `try` / `catch` blocco.

2. Se viene rilevata un'eccezione, individuare la riga di dati che ha causato l'errore.

3. Risolvere il problema nella riga di dati (a livello di codice, se è possibile o presentando la riga non valida all'utente per la modifica), quindi riprovare l'<xref:System.Data.DataRow.HasErrors%2A>aggiornamento <xref:System.Data.DataTable.GetErrors%2A>(,).

## <a name="save-data-to-a-database"></a>Salvare i dati in un database

Chiamare il `Update` metodo di un TableAdapter. Passare il nome della tabella dati contenente i valori da scrivere nel database.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Per aggiornare un database utilizzando un TableAdapter

- Racchiudere il`Update` metodo del TableAdapter in un `try` / `catch` blocco. Nell'esempio seguente viene illustrato come `Customers` aggiornare il contenuto della tabella in `NorthwindDataSet` dall'interno di un `try` / `catch` blocco.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)