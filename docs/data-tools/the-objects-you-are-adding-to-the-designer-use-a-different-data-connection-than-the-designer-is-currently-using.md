---
title: Gli oggetti utilizzano una connessione diversa
description: Gli oggetti aggiunti alla finestra di progettazione utilizzano una connessione dati diversa
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5b2ae4975f2848379403a0df1258640c32ccd58f
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036223"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Gli oggetti aggiunti alla finestra di progettazione utilizzano una connessione dati diversa da quella della finestra di progettazione

Gli oggetti in corso di aggiunta alla finestra di progettazione usano una connessione dati diversa da quella usata per la finestra di progettazione. Sostituire la connessione usata per la finestra di progettazione?

Quando si aggiungono elementi al **Object Relational Designer** (**O/R Designer**), tutti gli elementi utilizzano una connessione dati condivisa. L'area di progettazione rappresenta <xref:System.Data.Linq.DataContext> , che utilizza una singola connessione per tutti gli oggetti sulla superficie. Se si aggiunge un oggetto alla finestra di progettazione che utilizza una connessione dati diversa dalla connessione dati attualmente utilizzata dalla finestra di progettazione, verrà visualizzato questo messaggio. Per correggere l'errore, è possibile scegliere di mantenere la connessione esistente. In questo caso, l'oggetto selezionato non verrà aggiunto. In alternativa, è possibile scegliere di aggiungere l'oggetto e reimpostare la connessione di <xref:System.Data.Linq.DataContext> sulla nuova connessione.

## <a name="connection-options"></a>Opzioni di connessione

- Per sostituire la connessione esistente con la connessione utilizzata dall'oggetto selezionato, fare clic su **Sì**.

   L'oggetto selezionato viene aggiunto a **Progettazione relazionale**oggetti e *DataContext. Connection* è impostato sulla nuova connessione.

   > [!NOTE]
   > Se si fa clic su **Sì**, viene eseguito il mapping di tutte le classi di entità in **Progettazione relazionale di O/R** alla nuova connessione.

- Per continuare a utilizzare la connessione esistente e annullare l'aggiunta dell'oggetto selezionato, fare clic su **No**.

   L'azione viene annullata *DataContext. Connection* rimane impostato sulla connessione esistente.

## <a name="see-also"></a>Vedi anche

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
