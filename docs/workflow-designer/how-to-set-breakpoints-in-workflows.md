---
title: 'Finestra di progettazione del flusso di lavoro - procedura: impostare punti di interruzione nei flussi di lavoro'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1d7dcb437a77bd91c8dbb3360a33c7260fabb91
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755239"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Procedura: impostare punti di interruzione nei flussi di lavoro

Quando si utilizza Progettazione flussi di lavoro, è possibile impostare i punti di interruzione su flussi di lavoro grafici come si farebbe nel codice Visual Basic o c#. Come previsto, l'esecuzione del flusso di lavoro viene arrestata a ogni punto di interruzione impostato.

Un punto di interruzione ha tre stati: *in sospeso*, *associato*, e *errore*. Quando viene impostato, un punto di interruzione si trova nello stato In sospeso e viene rappresentato da un'icona rossa. Quando il runtime carica il tipo di flusso di lavoro, lo stato passa ad Associato. Se si specifica un formato non corretto per il punto di interruzione, ad esempio un nome di attività non valido, viene visualizzata una finestra di errore. Il punto di interruzione risulta ancora aggiunto alla finestra del punto di interruzione, ma è contrassegnato con una piccola “x”.

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

- [Procedura: Richiamare il debugger del flusso di lavoro](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
- [Debug dei flussi di lavoro mediante Progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Procedura: Debug di XML mediante Progettazione flussi di lavoro](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)