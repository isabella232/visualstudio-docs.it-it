---
title: 'Procedura: impostare punti di interruzione nei flussi di lavoro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d1bbb18a9015b52b3d65cb8f8fd02674693abc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659143"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Procedura: impostazione di punti di interruzione nei Flussi di lavoro
Quando si usa [!INCLUDE[wfd1](../includes/wfd1-md.md)], è possibile impostare punti di interruzione nei flussi di lavoro grafici come si farebbe nel codice Visual Basic o C#. Come previsto, l'esecuzione del flusso di lavoro viene arrestata a ogni punto di interruzione impostato.

 Un punto di interruzione ha tre stati: *Pending*, *Bound*ed *Error*. Quando viene impostato, un punto di interruzione si trova nello stato In sospeso e viene rappresentato da un'icona rossa. Quando il runtime carica il tipo di flusso di lavoro, lo stato passa ad Associato. Se si specifica un formato non corretto per il punto di interruzione, ad esempio un nome di attività non valido, viene visualizzata una finestra di errore. Il punto di interruzione risulta ancora aggiunto alla finestra del punto di interruzione, ma è contrassegnato con una piccola “x”.

> [!NOTE]
> L'impostazione dei punti di interruzione sui flussi di lavoro richiamati non è supportata.
>
> [!WARNING]
> Assicurarsi di selezionare l'opzione **abilita Just My Code (solo gestito)** dal menu **strumenti**, **Opzioni**, **debug** prima di eseguire il debug. Se si dispone di due sequenze annidate all'interno di un'altra sequenza e si imposta un punto di rottura sulla prima sequenza interna, premendo **F11** non verrà eseguito il debug nella seconda sequenza interna se l'opzione <strong>Abilita Just My Code (solo gestito)</strong>non è selezionata.
>
> [!WARNING]
> I punti di interruzione in un flusso di lavoro non vengono raggiunti se il percorso completo per la proprietà del file XAML non è corretto. Il percorso completo del file XAML non è preciso dopo avere spostato il progetto o la soluzione in un'altra cartella o a un altro computer. Selezionare CTRL+S per salvare e aggiornare la proprietà percorso completo.

### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Per impostare un punto di interruzione su un'attività nella visualizzazione Progettazione

1. Selezionare l'attività in corrispondenza della quale si desidera che il debugger si interrompa.

2. Scegliere **Imposta/Rimuovi**punto di interruzione dal menu **debug** . Verrà visualizzata un'icona rossa sul bordo superiore sinistro dell'attività.

     In alternativa, è possibile premere il tasto di **scelta rapida dopo** aver selezionato l'attività oppure è possibile fare clic con il pulsante destro del mouse sull'attività e **scegliere punto di interruzione,** quindi Inserisci punto di **interruzione** dal menu di scelta rapida.

## <a name="see-also"></a>Vedere anche
 [Procedura: richiamare i](../workflow-designer/how-to-invoke-the-workflow-debugger.md) [flussi di lavoro di debug del debugger del flusso di lavoro con il progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) [procedura: eseguire il debug di XAML con la progettazione flussi di lavoro](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)