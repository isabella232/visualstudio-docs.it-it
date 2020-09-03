---
title: Gli oggetti aggiunti alla finestra di progettazione utilizzano una connessione dati diversa da quella attualmente utilizzata dalla finestra di progettazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9ec76446aff930475ea5e3ca0133e11b3798b0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672297"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Gli oggetti in corso di aggiunta alla finestra di progettazione utilizzano una connessione dati diversa da quella utilizzata per la finestra di progettazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli oggetti in corso di aggiunta alla finestra di progettazione usano una connessione dati diversa da quella usata per la finestra di progettazione. Sostituire la connessione usata per la finestra di progettazione?

 Quando si aggiungono elementi a [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ), tutti gli elementi utilizzano una connessione dati condivisa. L'area di progettazione rappresenta <xref:System.Data.Linq.DataContext> , che utilizza una singola connessione per tutti gli oggetti sulla superficie. Se si aggiunge un oggetto alla finestra di progettazione che utilizza una connessione dati diversa dalla connessione dati attualmente utilizzata dalla finestra di progettazione, verrà visualizzato questo messaggio. Per correggere l'errore, è possibile scegliere di mantenere la connessione esistente. In questo caso, l'oggetto selezionato non verrà aggiunto. In alternativa, è possibile scegliere di aggiungere l'oggetto e reimpostare la connessione di <xref:System.Data.Linq.DataContext> sulla nuova connessione.

> [!NOTE]
> Se si fa clic su **Sì**, viene eseguito il mapping di tutte le classi di entità nell'oggetto [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] alla nuova connessione.

### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Per sostituire la connessione esistente con quella usata per l'oggetto selezionato

- Fare clic su **Sì**.

     L'oggetto selezionato viene aggiunto a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]e l'oggetto DataContext.Connection viene impostato sulla nuova connessione.

### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Per continuare a usare la connessione esistente e annullare l'aggiunta dell'oggetto selezionato

- Fare clic su **No**.

     L'azione viene annullata e l'oggetto DataContext.Connection resta impostato sulla connessione esistente.

## <a name="see-also"></a>Vedere anche
 [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)