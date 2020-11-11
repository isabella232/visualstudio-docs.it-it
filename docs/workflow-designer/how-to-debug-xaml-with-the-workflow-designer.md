---
title: 'Progettazione flussi di lavoro: debug di XAML'
description: Informazioni su come vengono definiti i flussi di lavoro in termini di XAML e su come eseguire il debug di XAML con la Progettazione flussi di lavoro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 24540a6e7a2f99f35edf6018355583b5f9230e1a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437931"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Procedura: debug di XML mediante Progettazione flussi di lavoro

I flussi di lavoro vengono definiti mediante codice XAML. La rappresentazione dell'interfaccia utente del flusso di lavoro si basa sull'albero XAML che definisce il flusso di lavoro. L'esperienza di debug è simile ai flussi di lavoro di debug nel Progettazione flussi di lavoro. Ad esempio, durante il debug di XAML, le finestre variabili locali, espressioni di controllo e thread funzionano in modo analogo a quanto avviene in Progettazione flussi di lavoro il debug. Durante il debug di XAML, inoltre, la visualizzazione degli stack di chiamate si presenta sotto forma di visualizzazione gerarchica basata sulle righe del flusso di esecuzione del flusso di lavoro.

> [!NOTE]
> Se XAML per un flusso di lavoro si trova nello stesso assembly delle attività, la parte dell'assembly dei nomi di classe non è inclusa. Senza questa parte dei nomi di classe (attività), il codice XAML non può essere caricato in fase di esecuzione. Non è consigliabile per definire le attività nello stesso spazio dei nomi del progetto principale; in caso contrario, XAML dovrà essere modificato a mano dopo essere stato modificato nella finestra di progettazione.

## <a name="to-debug-workflow-xaml"></a>Per eseguire il debug del flusso di lavoro XAML

1. Aprire un flusso di lavoro o un progetto di attività in Visual Studio.

2. Impostare un punto di interruzione per l'attività o le attività di cui si vuole eseguire il debug, come descritto in [procedura: impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3. Fare clic con il pulsante destro del mouse sul file con estensione XAML che contiene la definizione del flusso di lavoro e selezionare **Visualizza codice**. Verrà visualizzato un punto di interruzione nella stessa riga in cui si trova la dichiarazione dell'elemento XAML dell'attività per la quale è stato impostato il punto di interruzione nella visualizzazione Progettazione.

4. Richiamare il debugger come descritto in [debug dei flussi di lavoro](debugging-workflows-with-the-workflow-designer.md).

5. Quando l'esecuzione del codice raggiunge uno dei punti di interruzione, l'elemento XAML associato a tale punto verrà evidenziato. Per passare al punto di interruzione successivo, usare il tasto **F10** o **F11** .

## <a name="see-also"></a>Vedere anche

- [Procedura: Impostazione di punti di interruzione nei Flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Flussi di lavoro di debug](debugging-workflows-with-the-workflow-designer.md)
