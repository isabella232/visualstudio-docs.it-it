---
title: Gli oggetti a cui si aggiunge alla finestra di progettazione utilizzano una connessione dati diversa da quella della finestra di progettazione | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c86b40a79cc91f1a778d6c98be0865dc4a161840
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260923"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Gli oggetti in corso di aggiunta alla finestra di progettazione utilizzano una connessione dati diversa da quella utilizzata per la finestra di progettazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Gli oggetti in corso di aggiunta alla finestra di progettazione usano una connessione dati diversa da quella usata per la finestra di progettazione. Sostituire la connessione usata per la finestra di progettazione?  
  
 Quando si aggiungono elementi per il [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), tutti gli elementi usano una sola connessione dei dati condivisa. (l'area di progettazione rappresenta l'oggetto <xref:System.Data.Linq.DataContext>, che usa una sola connessione per tutti gli oggetti nell'area). Questo messaggio viene visualizzato se si aggiunge alla finestra di progettazione un oggetto che usa una connessione dati differente da quella attualmente usata per la finestra di progettazione. Per correggere l'errore, è possibile scegliere di mantenere la connessione esistente. In questo caso, l'oggetto selezionato non verrà aggiunto. In alternativa, è possibile scegliere di aggiungere l'oggetto e reimpostare il <xref:System.Data.Linq.DataContext> connessione alla nuova connessione.  
  
> [!NOTE]
>  Se si sceglie **Yes**, classi di tutte le entità nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] viene eseguito il mapping alla nuova connessione.  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Per sostituire la connessione esistente con quella usata per l'oggetto selezionato  
  
-   Scegliere **Sì**.  
  
     L'oggetto selezionato viene aggiunto a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]e l'oggetto DataContext.Connection viene impostato sulla nuova connessione.  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Per continuare a usare la connessione esistente e annullare l'aggiunta dell'oggetto selezionato  
  
-   Fare clic su **No**.  
  
     L'azione viene annullata e l'oggetto DataContext.Connection resta impostato sulla connessione esistente.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)

