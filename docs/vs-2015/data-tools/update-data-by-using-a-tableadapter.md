---
title: Aggiornare i dati tramite un TableAdapter | Microsoft Docs
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
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 312bf75100d2b9b270b45776c5f7ded21ab6ac52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72602340"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aggiornare i dati mediante un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una volta che i dati nel set di dati sono stati modificati e convalidati, è possibile inviare di nuovo i dati aggiornati a un DATABASEby chiamando il `Update` metodo di un TableAdapter. Il `Update` metodo aggiorna una singola tabella dati ed esegue il comando corretto (Insert, Update o DELETE) in base all'oggetto <xref:System.Data.DataRow.RowState%2A> di ogni riga di dati della tabella. Quando un set di dati include tabelle correlate, Visual Studio genera una classe TableAdapterManager da usare per eseguire gli aggiornamenti. La classe TableAdapterManager garantisce che gli aggiornamenti vengano eseguiti nell'ordine corretto in base ai vincoli FOREIGN KEY definiti nel database. Quando si utilizzano i controlli associati a dati, l'architettura DataBinding crea una variabile membro della classe TableAdapterManager denominata tableAdapterManager. Per ulteriori informazioni, vedere [Cenni preliminari sugli aggiornamenti gerarchici](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).

> [!NOTE]
> Quando si tenta di aggiornare un'origine dati con il contenuto di un set di dati, è possibile ottenere errori. Per evitare errori, è consigliabile inserire il codice che chiama il metodo dell'adapter `Update` all'interno di un `try` / `catch` blocco.

 La procedura esatta per l'aggiornamento di un'origine dati può variare a seconda delle esigenze aziendali, ma prevede i passaggi seguenti:

1. Chiamare il metodo dell'adapter `Update` in un `try` / `catch` blocco.

2. Se viene rilevata un'eccezione, individuare la riga di dati che ha causato l'errore. Per altre informazioni, vedere [procedura: individuare le righe che contengono errori](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).

3. Risolvere il problema nella riga di dati (a livello di codice, se è possibile o presentando la riga non valida all'utente per la modifica), quindi riprovare l'aggiornamento ( <xref:System.Data.DataRow.HasErrors%2A> , <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="savedata-to-a-database"></a>SaveData a un database
 Chiamare il `Update` metodo di un TableAdapter. Passare il nome della tabella dati contenente i valori da scrivere nel database.

#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Per aggiornare un database utilizzando un TableAdapter

- Racchiudere il metodo del TableAdapter `Update` in un `try` / `catch` blocco. Nell'esempio seguente viene illustrato come aggiornare il contenuto della `Customers` tabella in `NorthwindDataSet` dall'interno di un `try` / `catch` blocco.

     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]

## <a name="see-also"></a>Vedere anche
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
