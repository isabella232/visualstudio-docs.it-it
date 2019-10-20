---
title: 'Procedura: eseguire il debug di XAML con la Progettazione flussi di lavoro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a696123551c24fd0d14fecde67826cf14f88826f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668655"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Procedura: debug di XML mediante Progettazione flussi di lavoro
I flussi di lavoro vengono definiti mediante codice XAML. La rappresentazione dell'interfaccia utente del flusso di lavoro si basa sull'albero XAML che definisce il flusso di lavoro. Il processo di debug è simile a quello eseguito per i flussi di lavoro di [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Durante il debug di XAML, ad esempio, le finestre delle variabili locali, delle espressioni di controllo e dei thread funzionano esattamente come durante il debug di [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Durante il debug di XAML, inoltre, la visualizzazione degli stack di chiamate si presenta sotto forma di visualizzazione gerarchica basata sulle righe del flusso di esecuzione del flusso di lavoro.

> [!NOTE]
> Se XAML per un flusso di lavoro si trova nello stesso assembly delle attività, la parte dell'assembly dei nomi di classe non è inclusa. Senza questa parte dei nomi di classe (attività), XAML non può essere caricato in fase di esecuzione. Non è consigliabile per definire le attività nello stesso spazio dei nomi del progetto principale; in caso contrario, XAML dovrà essere modificato a mano dopo essere stato modificato nella finestra di progettazione.

### <a name="to-debug-workflow-xaml"></a>Per eseguire il debug del flusso di lavoro XAML

1. Aprire un flusso di lavoro o un progetto di attività in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Impostare un punto di interruzione per l'attività o le attività di cui si vuole eseguire il debug, come descritto in [procedura: impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3. Fare clic con il pulsante destro del mouse sul file con estensione XAML che contiene la definizione del flusso di lavoro e selezionare **Visualizza codice**. Verrà visualizzato un punto di interruzione nella stessa riga in cui si trova la dichiarazione dell'elemento XAML dell'attività per la quale è stato impostato il punto di interruzione nella visualizzazione Progettazione.

4. Richiamare il debugger come descritto in [procedura: richiamare il debugger del flusso di lavoro](../workflow-designer/how-to-invoke-the-workflow-debugger.md).

5. Quando l'esecuzione del codice raggiunge uno dei punti di interruzione, l'elemento XAML associato a tale punto verrà evidenziato. Per passare al punto di interruzione successivo, usare il tasto **F10** o **F11** .

## <a name="see-also"></a>Vedere anche
 [Procedura: impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [procedura: richiamare il debugger del flusso di lavoro](../workflow-designer/how-to-invoke-the-workflow-debugger.md)