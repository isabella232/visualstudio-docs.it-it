---
title: 'Finestra di progettazione del flusso di lavoro - procedura: Eseguire il debug di XAML con Progettazione flussi di lavoro'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 03556c00a6b43e7bbab308bf1acbb1501582a118
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823484"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Procedura: Eseguire il debug di XAML con Progettazione flussi di lavoro

I flussi di lavoro vengono definiti mediante codice XAML. La rappresentazione dell'interfaccia utente del flusso di lavoro si basa sull'albero XAML che definisce il flusso di lavoro. L'esperienza di debug è simile all'esecuzione del debug dei flussi di lavoro nella finestra di progettazione del flusso di lavoro. Ad esempio, durante il debug di XAML, le variabili locali, espressioni di controllo e finestre thread funzionano esattamente come avviene in Progettazione flussi di lavoro di debug. Durante il debug di XAML, inoltre, la visualizzazione degli stack di chiamate si presenta sotto forma di visualizzazione gerarchica basata sulle righe del flusso di esecuzione del flusso di lavoro.

> [!NOTE]
> Se XAML per un flusso di lavoro si trova nello stesso assembly delle attività, la parte dell'assembly dei nomi di classe non è inclusa. Senza questa parte dei nomi di classe (attività), XAML non può essere caricato in fase di esecuzione. Non è consigliabile per definire le attività nello stesso spazio dei nomi del progetto principale; in caso contrario, XAML dovrà essere modificato a mano dopo essere stato modificato nella finestra di progettazione.

## <a name="to-debug-workflow-xaml"></a>Per eseguire il debug del flusso di lavoro XAML

1.  Aprire un progetto flusso di lavoro o attività in Visual Studio.

2.  Impostare un punto di interruzione nell'attività o attività che si desidera eseguire il debug come descritto in [come: Impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3.  Fare clic sul file con estensione XAML contenente la definizione del flusso di lavoro e selezionare **Visualizza codice**. Verrà visualizzato un punto di interruzione nella stessa riga in cui si trova la dichiarazione dell'elemento XAML dell'attività per la quale è stato impostato il punto di interruzione nella visualizzazione Progettazione.

4.  Richiama il debugger, come descritto in [eseguire il Debug dei flussi di lavoro](debugging-workflows-with-the-workflow-designer.md).

5.  Quando l'esecuzione del codice raggiunge uno dei punti di interruzione, l'elemento XAML associato a tale punto verrà evidenziato. Per spostare il punto di interruzione successivo, usare il **F10** oppure **F11** chiave.

## <a name="see-also"></a>Vedere anche

- [Procedura: Impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Eseguire il debug dei flussi di lavoro](debugging-workflows-with-the-workflow-designer.md)