---
title: 'Procedura: Salvare dati usando una transazione'
description: Esaminare come salvare i dati usando una transazione con gli strumenti di DataSet in Visual Studio. Per salvare i dati in una transazione, usare lo spazio dei nomi System.Transactions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5acc25ecb9a370317170d6d419a931414a7dee11ed0b4bcf1c1b4442248d109a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346908"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Procedura: Salvare dati usando una transazione

Per salvare i dati in una transazione, usare lo spazio dei <xref:System.Transactions> nomi . Utilizzare <xref:System.Transactions.TransactionScope> l'oggetto per partecipare a una transazione gestita automaticamente.

I progetti non vengono creati con un riferimento all'assembly *System.Transactions,* pertanto è necessario aggiungere manualmente un riferimento ai progetti che usano transazioni.

Il modo più semplice per implementare una transazione è creare un'istanza di <xref:System.Transactions.TransactionScope> un oggetto in `using` un'istruzione . Per altre informazioni, vedere [Istruzione Using](/dotnet/visual-basic/language-reference/statements/using-statement)e [Istruzione Using.](/dotnet/csharp/language-reference/keywords/using-statement) Il codice eseguito all'interno `using` dell'istruzione partecipa alla transazione.

Per eseguire il commit della transazione, <xref:System.Transactions.TransactionScope.Complete%2A> chiamare il metodo come ultima istruzione nel blocco using.

Per eseguire il rollback della transazione, generare un'eccezione prima di chiamare il <xref:System.Transactions.TransactionScope.Complete%2A> metodo .

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Per aggiungere un riferimento al System.Transactions.dll

1. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

2. Nella scheda **.NET** **(SQL Server** per i progetti SQL Server), selezionare **System.Transactions** e quindi **selezionare OK.**

     Un riferimento *aSystem.Transactions.dll* viene aggiunto al progetto.

## <a name="to-save-data-in-a-transaction"></a>Per salvare i dati in una transazione

- Aggiungere il codice per salvare i dati all'interno dell'istruzione using che contiene la transazione. Nel codice seguente viene illustrato come creare e creare un'istanza di un <xref:System.Transactions.TransactionScope> oggetto in un'istruzione using:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet11":::

## <a name="see-also"></a>Vedi anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
- [Procedura dettagliata: Salvare dati in una transazione](../data-tools/save-data-in-a-transaction.md)
