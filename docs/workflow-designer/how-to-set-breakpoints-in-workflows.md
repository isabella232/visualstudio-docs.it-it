---
title: Impostare punti di interruzione in flussi di lavoro
description: Informazioni su come usare il Progettazione flussi di lavoro per impostare punti di interruzione nei flussi di lavoro grafici come nel codice Visual Basic o C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 5a40b357c71fffd1ef44be4e904cd52b583fb956
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963551"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Procedura: Impostare punti di interruzione nei flussi di lavoro

Quando si usa Progettazione flussi di lavoro, è possibile impostare punti di interruzione nei flussi di lavoro grafici come nel codice Visual Basic o C#. Come previsto, l'esecuzione del flusso di lavoro viene arrestata a ogni punto di interruzione impostato.

Un punto di interruzione ha tre *stati: In sospeso,* *Associato* ed *Errore*. Quando viene impostato, un punto di interruzione si trova nello stato In sospeso e viene rappresentato da un'icona rossa. Quando il runtime carica il tipo di flusso di lavoro, lo stato passa ad Associato. Se si specifica un formato non corretto per il punto di interruzione, ad esempio un nome di attività non valido, viene visualizzata una finestra di errore. Il punto di interruzione risulta ancora aggiunto alla finestra del punto di interruzione, ma è contrassegnato con una piccola “x”.

> [!NOTE]
> L'impostazione dei punti di interruzione sui flussi di lavoro richiamati non è supportata.

> [!NOTE]
> Assicurarsi di selezionare l'opzione **Abilita Just My Code (solo gestito)** dal menu Strumenti   >  **Opzioni**  >  **Debug** prima di eseguire il debug. Se l'opzione non è selezionata e sono presenti due sequenze annidate all'interno di un'altra sequenza e si imposta un punto di interruzione nella prima sequenza interna, premendo **F11** non viene esempio il debug nella seconda sequenza interna.

> [!NOTE]
> I punti di interruzione in un flusso di lavoro non vengono raggiunto se il percorso completo della proprietà del file XAML non è accurato. Il percorso completo del file XAML non è accurato dopo lo spostamento del progetto o della soluzione in un'altra cartella o in un altro computer. Premere **CTRL** + **S** per salvare e aggiornare la proprietà del percorso completo.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Per impostare un punto di interruzione su un'attività nella visualizzazione Progettazione

1. Selezionare l'attività in corrispondenza della quale si desidera che il debugger si interrompa.

2. Scegliere **Attiva/Disattiva** punto di **interruzione dal** menu Debug . Verrà visualizzata un'icona rossa sul bordo superiore sinistro dell'attività.

   In alternativa, è possibile premere **F9** dopo aver selezionato l'attività oppure fare clic con il pulsante destro del mouse sull'attività e scegliere Punto di interruzione Inserisci punto di interruzione dal menu di scelta  >   rapida.

## <a name="see-also"></a>Vedi anche

- [Debug dei flussi di lavoro mediante Progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Procedura: debug di XML mediante Progettazione flussi di lavoro](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
