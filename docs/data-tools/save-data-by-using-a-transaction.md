---
title: 'Procedura: Salvare dati usando una transazione'
description: Vedere come salvare i dati usando una transazione con gli strumenti del set di dati in Visual Studio. Per salvare i dati in una transazione, utilizzare lo spazio dei nomi System. Transactions.
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c1cd112a1960078c72c575542525a5ecf6571b06
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434584"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Procedura: Salvare dati usando una transazione

Per salvare i dati in una transazione, è possibile utilizzare lo <xref:System.Transactions> spazio dei nomi. Utilizzare l' <xref:System.Transactions.TransactionScope> oggetto per partecipare a una transazione gestita automaticamente.

I progetti non vengono creati con un riferimento all'assembly *System. Transactions* , quindi è necessario aggiungere manualmente un riferimento a progetti che usano transazioni.

Il modo più semplice per implementare una transazione è creare un'istanza di un <xref:System.Transactions.TransactionScope> oggetto in un' `using` istruzione. Per ulteriori informazioni, vedere [istruzione using](/dotnet/visual-basic/language-reference/statements/using-statement)e [istruzione using](/dotnet/csharp/language-reference/keywords/using-statement). Il codice eseguito all'interno dell' `using` istruzione fa parte della transazione.

Per eseguire il commit della transazione, chiamare il <xref:System.Transactions.TransactionScope.Complete%2A> metodo come ultima istruzione nel blocco using.

Per eseguire il rollback della transazione, generare un'eccezione prima di chiamare il <xref:System.Transactions.TransactionScope.Complete%2A> metodo.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Per aggiungere un riferimento al System.Transactions.dll

1. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

2. Nella scheda **.NET** ( **SQL Server** TAB per SQL Server Projects) selezionare **System. Transactions** e quindi fare clic su **OK**.

     Al progetto viene aggiunto un riferimento a *System.Transactions.dll* .

## <a name="to-save-data-in-a-transaction"></a>Per salvare i dati in una transazione

- Aggiungere il codice per salvare i dati all'interno dell'istruzione using che contiene la transazione. Nel codice seguente viene illustrato come creare e creare un'istanza di un <xref:System.Transactions.TransactionScope> oggetto in un'istruzione using:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
- [Procedura dettagliata: Salvare dati in una transazione](../data-tools/save-data-in-a-transaction.md)
