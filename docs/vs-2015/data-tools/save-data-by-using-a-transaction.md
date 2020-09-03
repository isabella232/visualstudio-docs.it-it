---
title: Salvare i dati tramite una transazione | Microsoft Docs
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
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85f3584073523e748168faf569aa918ba912fbf8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652827"
---
# <a name="save-data-by-using-a-transaction"></a>Salvare dati usando una transazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per salvare i dati in una transazione, è possibile utilizzare lo <xref:System.Transactions> spazio dei nomi. Utilizzare l' <xref:System.Transactions.TransactionScope> oggetto per partecipare a una transazione gestita automaticamente.

 I progetti non vengono creati con un riferimento all'assembly System. Transactions, quindi è necessario aggiungere manualmente un riferimento a progetti che usano transazioni.

> [!NOTE]
> Lo <xref:System.Transactions> spazio dei nomi è supportato in Windows 2000 o versioni successive.

 Il modo più semplice per implementare una transazione è creare un'istanza di un <xref:System.Transactions.TransactionScope> oggetto in un' `using` istruzione. Per ulteriori informazioni, vedere [istruzione using](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)e [istruzione using](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3). Il codice eseguito all'interno dell' `using` istruzione fa parte della transazione.

 Per eseguire il commit della transazione, chiamare il <xref:System.Transactions.TransactionScope.Complete%2A> metodo come ultima istruzione nel blocco using.

 Per eseguire il rollback della transazione, generare un'eccezione prima di chiamare il <xref:System.Transactions.TransactionScope.Complete%2A> metodo.

 Per ulteriori informazioni, vedere [salvare dati in una transazione](../data-tools/save-data-in-a-transaction.md).

### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Per aggiungere un riferimento alla dll System. Transactions

1. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

2. Nella scheda **.NET** (**SQL Server** TAB per SQL Server Projects) selezionare **System. Transactions**e quindi fare clic su **OK**.

     Al progetto viene aggiunto un riferimento a System.Transactions.dll.

### <a name="to-save-data-in-a-transaction"></a>Per salvare i dati in una transazione

- Aggiungere il codice per salvare i dati all'interno dell'istruzione using che contiene la transazione. Nel codice seguente viene illustrato come creare e creare un'istanza di un <xref:System.Transactions.TransactionScope> oggetto in un'istruzione using:

     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]

## <a name="see-also"></a>Vedere anche
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
