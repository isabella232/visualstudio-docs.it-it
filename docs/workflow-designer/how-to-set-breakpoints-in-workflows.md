---
title: 'Progettazione flussi di lavoro-procedura: impostare punti di interruzione nei flussi di lavoro'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9530e7ec018a89c3648f61660a5651eddaace805
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817489"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Procedura: impostare punti di interruzione nei flussi di lavoro

Quando si usa Progettazione flussi di lavoro, è possibile impostare punti di interruzione nei flussi di lavoro grafici come per il codice Visual Basic o C#. Come previsto, l'esecuzione del flusso di lavoro viene arrestata a ogni punto di interruzione impostato.

Un punto di interruzione ha tre stati: *Pending*, *Bound*ed *Error*. Quando viene impostato, un punto di interruzione si trova nello stato In sospeso e viene rappresentato da un'icona rossa. Quando il runtime carica il tipo di flusso di lavoro, lo stato passa ad Associato. Se si specifica un formato non corretto per il punto di interruzione, ad esempio un nome di attività non valido, viene visualizzata una finestra di errore. Il punto di interruzione risulta ancora aggiunto alla finestra del punto di interruzione, ma è contrassegnato con una piccola “x”.

> [!NOTE]
> L'impostazione dei punti di interruzione sui flussi di lavoro richiamati non è supportata.

> [!NOTE]
> Assicurarsi di selezionare l'opzione **Abilita Just My Code (solo gestito)** dal menu **strumenti**  >  **Opzioni**di  >  **debug** prima di eseguire il debug. Se l'opzione non è selezionata e si hanno due sequenze annidate all'interno di un'altra sequenza e si imposta un punto di rottura sulla prima sequenza interna, la pressione di **F11** non esegue il debug nella seconda sequenza interna.

> [!NOTE]
> I punti di interruzione in un flusso di lavoro non vengono raggiunti se il percorso completo della proprietà del file XAML non è accurato. Il percorso completo del file XAML non è accurato dopo aver spostato il progetto o la soluzione in un'altra cartella o in un altro computer. Selezionare **CTRL** + **S** per salvare e aggiornare la proprietà percorso completo.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Per impostare un punto di interruzione su un'attività nella visualizzazione Progettazione

1. Selezionare l'attività in corrispondenza della quale si desidera che il debugger si interrompa.

2. Scegliere **Imposta/Rimuovi**punto di interruzione dal menu **debug** . Verrà visualizzata un'icona rossa sul bordo superiore sinistro dell'attività.

   In alternativa, è possibile premere **F9** dopo aver selezionato l'attività oppure fare clic con il pulsante destro del mouse sull'attività **e scegliere punto**  >  di**interruzione Inserisci** punto di interruzione dal menu di scelta rapida.

## <a name="see-also"></a>Vedere anche

- [Debug dei flussi di lavoro mediante Progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Procedura: debug di XML mediante Progettazione flussi di lavoro](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
