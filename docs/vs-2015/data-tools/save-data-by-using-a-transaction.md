---
title: Salvare i dati utilizzando una transazione | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c88bd18e8b02c62a31743427bf70cc7eac68ed79
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525918"
---
# <a name="save-data-by-using-a-transaction"></a>Salvare dati usando una transazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [salvare i dati utilizzando una transazione](https://docs.microsoft.com/visualstudio/data-tools/save-data-by-using-a-transaction).  
  
  
Salvare i dati in una transazione usando il <xref:System.Transactions> dello spazio dei nomi. Usare il <xref:System.Transactions.TransactionScope> oggetto da inserire in una transazione che viene gestita automaticamente.  
  
 I progetti non vengono creati con un riferimento all'assembly System. Transactions, pertanto è necessario aggiungere manualmente un riferimento a progetti che usano le transazioni.  
  
> [!NOTE]
>  Il <xref:System.Transactions> dello spazio dei nomi è supportata in Windows 2000 o versioni successive.  
  
 Il modo più semplice per implementare una transazione è creare un'istanza di un <xref:System.Transactions.TransactionScope> dell'oggetto un `using` istruzione. (Per altre informazioni, vedere [istruzione Using](http://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1), e [istruzione using](http://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) Il codice eseguito all'interno di `using` istruzione partecipa alla transazione.  
  
 Per eseguire il commit della transazione, chiamare il <xref:System.Transactions.TransactionScope.Complete%2A> blocca l'ultima istruzione nel usando il metodo.  
  
 Per eseguire il rollback della transazione, generare un'eccezione prima di chiamare il <xref:System.Transactions.TransactionScope.Complete%2A> (metodo).  
  
 Per altre informazioni, vedere [salvare i dati in una transazione](../data-tools/save-data-in-a-transaction.md).  
  
### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Per aggiungere un riferimento alla dll System. Transactions  
  
1.  Nel **Project** dal menu **Aggiungi riferimento**.  
  
2.  Nel **.NET** della scheda (**SQL Server** tab per i progetti di SQL Server), selezionare **System. Transactions**e thenselect**OK**.  
  
     Un riferimento a Transactions viene aggiunto al progetto.  
  
### <a name="to-save-data-in-a-transaction"></a>Per salvare i dati in una transazione  
  
-   Aggiungere il codice per salvare i dati all'interno di usando istruzione che contiene la transazione. Il codice seguente viene illustrato come creare e creare un'istanza di un <xref:System.Transactions.TransactionScope> oggetto in un uso istruzione:  
  
     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)

