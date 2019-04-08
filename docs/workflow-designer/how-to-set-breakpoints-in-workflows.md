---
title: 'Finestra di progettazione del flusso di lavoro - procedura: Impostare punti di interruzione in flussi di lavoro'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7503d0b0bee201a9617e90966c9f75ac6333f228
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908439"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Procedura: Impostare punti di interruzione in flussi di lavoro

Quando si utilizza Progettazione flussi di lavoro, è possibile impostare i punti di interruzione su flussi di lavoro grafici come si farebbe nel codice Visual Basic o C#. Come previsto, l'esecuzione del flusso di lavoro viene arrestata a ogni punto di interruzione impostato.

Un punto di interruzione ha tre stati: *In sospeso*, *associato*, e *errore*. Quando viene impostato, un punto di interruzione si trova nello stato In sospeso e viene rappresentato da un'icona rossa. Quando il runtime carica il tipo di flusso di lavoro, lo stato passa ad Associato. Se si specifica un formato non corretto per il punto di interruzione, ad esempio un nome di attività non valido, viene visualizzata una finestra di errore. Il punto di interruzione risulta ancora aggiunto alla finestra del punto di interruzione, ma è contrassegnato con una piccola “x”.

> [!NOTE]
> L'impostazione dei punti di interruzione sui flussi di lavoro richiamati non è supportata.

> [!NOTE]
> Assicurarsi di selezionare l'opzione **Abilita Just My Code (solo gestito)** dalle **Tools** > **opzioni** > **debug**  menu prima di eseguire il debug. Se non è selezionata l'opzione e si dispone di due sequenze annidate in un'altra sequenza e impostare un punto di interruzione nella prima sequenza interna, premendo **F11** non consente il debug nella seconda sequenza interna.

> [!NOTE]
> I punti di interruzione in un flusso di lavoro non vengano raggiunti se il percorso completo di proprietà del file XAML non è preciso. Il percorso completo al file XAML non è preciso dopo lo spostamento di progetto o della soluzione in un'altra cartella o in un altro computer. Selezionare **Ctrl**+**S** per salvare e aggiornare la proprietà percorso completo.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Per impostare un punto di interruzione su un'attività nella visualizzazione Progettazione

1. Selezionare l'attività in corrispondenza della quale si desidera che il debugger si interrompa.

2. Nel **Debug** dal menu **Attiva/Disattiva punto di interruzione**. Verrà visualizzata un'icona rossa sul bordo superiore sinistro dell'attività.

   In alternativa, è possibile premere **F9** dopo aver selezionato l'attività o si può fare doppio clic su attività e selezionare **punto di interruzione** > **Inserisci punto di interruzione** dal menu di scelta rapida.

## <a name="see-also"></a>Vedere anche

- [Debug dei flussi di lavoro mediante Progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Procedura: Eseguire il debug di XAML con la finestra di progettazione del flusso di lavoro](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)