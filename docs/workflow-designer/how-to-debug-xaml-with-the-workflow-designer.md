---
title: 'Progettazione flussi di lavoro: Eseguire il debug di XAML'
description: Informazioni su come vengono definiti i flussi di lavoro in termini di XAML e su come eseguire il debug di XAML con il Progettazione flussi di lavoro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- uwp
ms.openlocfilehash: 721ee723c6f7d0e28c4d7da376233641a580d21d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633676"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Procedura: debug di XML mediante Progettazione flussi di lavoro

I flussi di lavoro vengono definiti mediante codice XAML. La rappresentazione dell'interfaccia utente del flusso di lavoro si basa sull'albero XAML che definisce il flusso di lavoro. L'esperienza di debug è simile al debug dei flussi di lavoro nel Progettazione flussi di lavoro. Durante il debug di XAML, ad esempio, le finestre variabili locali, espressioni di controllo e thread funzionano allo stesso modo delle finestre di Progettazione flussi di lavoro debug. Durante il debug di XAML, inoltre, la visualizzazione degli stack di chiamate si presenta sotto forma di visualizzazione gerarchica basata sulle righe del flusso di esecuzione del flusso di lavoro.

> [!NOTE]
> Se XAML per un flusso di lavoro si trova nello stesso assembly delle attività, la parte dell'assembly dei nomi di classe non è inclusa. Senza questa parte dei nomi di classe (attività), il codice XAML non può essere caricato in fase di esecuzione. Non è consigliabile per definire le attività nello stesso spazio dei nomi del progetto principale; in caso contrario, XAML dovrà essere modificato a mano dopo essere stato modificato nella finestra di progettazione.

## <a name="to-debug-workflow-xaml"></a>Per eseguire il debug del flusso di lavoro XAML

1. Aprire un progetto di flusso di lavoro o attività in Visual Studio.

2. Impostare un punto di interruzione sull'attività o sulle attività di cui si vuole eseguire il debug come descritto in [Procedura: Impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3. Fare clic con il pulsante destro del mouse sul file con estensione xaml che contiene la definizione del flusso di lavoro e **scegliere Visualizza codice.** Verrà visualizzato un punto di interruzione nella stessa riga in cui si trova la dichiarazione dell'elemento XAML dell'attività per la quale è stato impostato il punto di interruzione nella visualizzazione Progettazione.

4. Richiamare il debugger come descritto in Eseguire [il debug dei flussi di lavoro.](debugging-workflows-with-the-workflow-designer.md)

5. Quando l'esecuzione del codice raggiunge uno dei punti di interruzione, l'elemento XAML associato a tale punto verrà evidenziato. Per passare al punto di interruzione successivo, usare **il tasto F10** **o F11.**

## <a name="see-also"></a>Vedi anche

- [Procedura: Impostazione di punti di interruzione nei Flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Flussi di lavoro di debug](debugging-workflows-with-the-workflow-designer.md)
