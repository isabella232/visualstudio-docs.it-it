---
title: Modifica del tipo restituito di un metodo DataContext non può essere annullata | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d3b94b70db49903e41d26ac0f1382eaa2826e31a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059757"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>La modifica del tipo restituito di un metodo DataContext non può essere annullata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La modifica del tipo restituito di un metodo DataContext non può essere annullata. Per ripristinare il tipo generato automaticamente, è necessario trascinare nuovamente l'oggetto da Esplora server/Esplora database su Progettazione relazionale oggetti. Modificare il tipo restituito?  
  
 Il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> varia a seconda della posizione in cui si rilascia l'elemento in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Se si rilascia un elemento direttamente in una classe di entità esistente, viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità. Se invece si rilascia un elemento in un'area vuota di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], viene creato un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e fare clic sulla proprietà **Return Type** nella finestra **Proprietà**.  
  
### <a name="to-change-the-return-type-of-a-datacontext"></a>Per modificare il tipo restituito di un metodo DataContext  
  
- Scegliere **Sì**.  
  
### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Per uscire dalla finestra di messaggio e lasciare invariato il tipo restituito  
  
- Fare clic su **No**.  
  
### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Per ripristinare il tipo restituito originale dopo la modifica del tipo restituito  
  
1. Selezionare il metodo <xref:System.Data.Linq.DataContext> in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ed eliminarlo.  
  
2. Individuare l'elemento in **Esplora server/Esplora database** e trascinarlo in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito predefinito originale.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: Creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
