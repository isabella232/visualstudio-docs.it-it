---
title: 'Procedura: Salvare dati usando una transazione'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bf5864d25e78b6050da5c13097503b2998dda44a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080995"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Procedura: Salvare dati usando una transazione

Salvare i dati in una transazione usando il <xref:System.Transactions> dello spazio dei nomi. Usare il <xref:System.Transactions.TransactionScope> oggetto da inserire in una transazione che viene gestita automaticamente.

I progetti non vengono creati con un riferimento per la *System. Transactions* assembly, pertanto è necessario aggiungere manualmente un riferimento a progetti che usano le transazioni.

Il modo più semplice per implementare una transazione è creare un'istanza di un <xref:System.Transactions.TransactionScope> dell'oggetto un `using` istruzione. (Per altre informazioni, vedere [istruzione Using](/dotnet/visual-basic/language-reference/statements/using-statement), e [istruzione Using](/dotnet/csharp/language-reference/keywords/using-statement).) Il codice eseguito all'interno di `using` istruzione partecipa alla transazione.

Per eseguire il commit della transazione, chiamare il <xref:System.Transactions.TransactionScope.Complete%2A> blocca l'ultima istruzione nel usando il metodo.

Per eseguire il rollback della transazione, generare un'eccezione prima di chiamare il <xref:System.Transactions.TransactionScope.Complete%2A> (metodo).

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Per aggiungere un riferimento al Transactions

1. Nel **Project** dal menu **Aggiungi riferimento**.

2. Nel **.NET** scheda (**SQL Server** scheda per i progetti di SQL Server), selezionare **System. Transactions**, quindi selezionare **OK**.

     Un riferimento a *Transactions* viene aggiunto al progetto.

## <a name="to-save-data-in-a-transaction"></a>Per salvare i dati in una transazione

- Aggiungere il codice per salvare i dati all'interno di usando istruzione che contiene la transazione. Il codice seguente viene illustrato come creare e creare un'istanza di un <xref:System.Transactions.TransactionScope> oggetto in un uso istruzione:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
- [Procedura dettagliata: Salvare i dati in una transazione](../data-tools/save-data-in-a-transaction.md)