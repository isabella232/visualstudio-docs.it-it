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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cfb03944743609d20d14f6104e5fadd529a5cfa6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641315"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Procedura: Salvare dati usando una transazione

Per salvare i dati in una transazione, è possibile utilizzare lo spazio dei nomi <xref:System.Transactions>. Utilizzare l'oggetto <xref:System.Transactions.TransactionScope> per partecipare a una transazione gestita automaticamente.

I progetti non vengono creati con un riferimento all'assembly *System. Transactions* , quindi è necessario aggiungere manualmente un riferimento a progetti che usano transazioni.

Il modo più semplice per implementare una transazione è creare un'istanza di un oggetto <xref:System.Transactions.TransactionScope> in un'istruzione `using`. Per ulteriori informazioni, vedere [istruzione using](/dotnet/visual-basic/language-reference/statements/using-statement)e [istruzione using](/dotnet/csharp/language-reference/keywords/using-statement). Il codice eseguito all'interno dell'istruzione `using` fa parte della transazione.

Per eseguire il commit della transazione, chiamare il metodo <xref:System.Transactions.TransactionScope.Complete%2A> come ultima istruzione nel blocco using.

Per eseguire il rollback della transazione, generare un'eccezione prima di chiamare il metodo <xref:System.Transactions.TransactionScope.Complete%2A>.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Per aggiungere un riferimento a System. Transactions. dll

1. Scegliere **Aggiungi riferimento**dal menu **progetto** .

2. Nella scheda **.NET** (**SQL Server** TAB per SQL Server Projects) selezionare **System. Transactions**e quindi fare clic su **OK**.

     Al progetto viene aggiunto un riferimento a *System. Transactions. dll* .

## <a name="to-save-data-in-a-transaction"></a>Per salvare i dati in una transazione

- Aggiungere il codice per salvare i dati all'interno dell'istruzione using che contiene la transazione. Nel codice seguente viene illustrato come creare e creare un'istanza di un oggetto <xref:System.Transactions.TransactionScope> in un'istruzione using:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
- [Procedura dettagliata: Salvare dati in una transazione](../data-tools/save-data-in-a-transaction.md)