---
title: Aggiornare i dati mediante un TableAdapter
description: Aggiornare i dati in un set di dati. Inviare i dati al database chiamando il metodo Update di un oggetto TableAdapter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 77ef45eadadab661639b17c4e29fdf13986da9fd89bf51f7c7358252d64af932
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346661"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aggiornare i dati mediante un TableAdapter

Dopo aver modificato e convalidato i dati nel set di dati, è possibile inviare i dati aggiornati a un database chiamando il metodo `Update` di un [oggetto TableAdapter](../data-tools/create-and-configure-tableadapters.md). Il metodo aggiorna una singola tabella di dati ed esegue il comando corretto (INSERT, UPDATE o DELETE) in base all'oggetto di ogni riga `Update` <xref:System.Data.DataRow.RowState%2A> di dati nella tabella. Quando un set di dati include tabelle correlate, Visual Studio genera una classe TableAdapterManager che viene utilizzata per eseguire gli aggiornamenti. La classe TableAdapterManager garantisce che gli aggiornamenti siano evasi nell'ordine corretto in base ai vincoli di chiave esterna definiti nel database. Quando si usano controlli associati a dati, l'architettura di databinding crea una variabile membro della classe TableAdapterManager denominata tableAdapterManager.

> [!NOTE]
> Quando si tenta di aggiornare un'origine dati con il contenuto di un set di dati, è possibile ottenere errori. Per evitare errori, è consigliabile inserire il codice che chiama il metodo dell'adapter `Update` all'interno di un `try` / `catch` blocco .

La procedura esatta per l'aggiornamento di un'origine dati può variare a seconda delle esigenze aziendali, ma include i passaggi seguenti:

1. Chiamare il metodo `Update` dell'adapter in un blocco `try` / `catch` .

2. Se viene rilevata un'eccezione, individuare la riga di dati che ha causato l'errore.

3. Riconciliare il problema nella riga di dati (a livello di codice, se possibile oppure presentando la riga non valida all'utente per la modifica), quindi provare di nuovo l'aggiornamento ( <xref:System.Data.DataRow.HasErrors%2A> , <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="save-data-to-a-database"></a>Salvare i dati in un database

Chiamare il `Update` metodo di un oggetto TableAdapter. Passare il nome della tabella dati che contiene i valori da scrivere nel database.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Per aggiornare un database tramite un tableadapter

- Racchiudere il metodo del TableAdapter `Update` in un `try` / `catch` blocco . Nell'esempio seguente viene illustrato come aggiornare il contenuto della tabella `Customers` in `NorthwindDataSet` dall'interno di un `try` / `catch` blocco .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet9":::

## <a name="see-also"></a>Vedi anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
