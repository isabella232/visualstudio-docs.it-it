---
title: Gli oggetti usano una connessione diversa
description: Gli oggetti da aggiungere alla finestra di progettazione usano una connessione dati diversa da quella della finestra di progettazione. Visualizzare informazioni su questo Visual Studio O/R Designer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a93906f50fb332b05c7894c80d581d49d3f3be22
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052577"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Gli oggetti da aggiungere alla finestra di progettazione usano una connessione dati diversa da quella della finestra di progettazione

Gli oggetti in corso di aggiunta alla finestra di progettazione usano una connessione dati diversa da quella usata per la finestra di progettazione. Sostituire la connessione usata per la finestra di progettazione?

Quando si aggiungono elementi al **Object Relational Designer** (**O/R Designer**), tutti gli elementi usano una connessione dati condivisa. L'area di progettazione rappresenta <xref:System.Data.Linq.DataContext> , che usa una singola connessione per tutti gli oggetti sulla superficie. Se si aggiunge un oggetto alla finestra di progettazione che usa una connessione dati diversa dalla connessione dati attualmente usata dalla finestra di progettazione, viene visualizzato questo messaggio. Per correggere l'errore, è possibile scegliere di mantenere la connessione esistente. In questo caso, l'oggetto selezionato non verrà aggiunto. In alternativa, è possibile scegliere di aggiungere l'oggetto e reimpostare la connessione di <xref:System.Data.Linq.DataContext> sulla nuova connessione.

## <a name="connection-options"></a>Opzioni di connessione

- Per sostituire la connessione esistente con la connessione usata dall'oggetto selezionato, fare clic su **Sì**.

   L'oggetto selezionato viene aggiunto a **O/R Designer** e *DataContext.Connection* viene impostato sulla nuova connessione.

   > [!NOTE]
   > Se si fa **clic su Sì,** tutte le classi di entità in **O/R Designer** vengono mappate alla nuova connessione.

- Per continuare a usare la connessione esistente e annullare l'aggiunta dell'oggetto selezionato, fare clic su **No.**

   L'azione viene annullata *DataContext.Connection rimane* impostato sulla connessione esistente.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
