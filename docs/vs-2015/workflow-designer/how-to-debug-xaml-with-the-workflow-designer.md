---
title: 'Procedura: Eseguire il debug di XAML con la finestra di progettazione del flusso di lavoro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 053ea0c65183f57bc80b87980b100f1a76067ea8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966167"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Procedura: Eseguire il debug di XAML con Progettazione flussi di lavoro
I flussi di lavoro vengono definiti mediante codice XAML. La rappresentazione dell'interfaccia utente del flusso di lavoro si basa sull'albero XAML che definisce il flusso di lavoro. Il processo di debug è simile a quello eseguito per i flussi di lavoro di [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Durante il debug di XAML, ad esempio, le finestre delle variabili locali, delle espressioni di controllo e dei thread funzionano esattamente come durante il debug di [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Durante il debug di XAML, inoltre, la visualizzazione degli stack di chiamate si presenta sotto forma di visualizzazione gerarchica basata sulle righe del flusso di esecuzione del flusso di lavoro.  
  
> [!NOTE]
>  Se XAML per un flusso di lavoro si trova nello stesso assembly delle attività, la parte dell'assembly dei nomi di classe non è inclusa. Senza questa parte dei nomi di classe (attività), XAML non può essere caricato in fase di esecuzione. Non è consigliabile per definire le attività nello stesso spazio dei nomi del progetto principale; in caso contrario, XAML dovrà essere modificato a mano dopo essere stato modificato nella finestra di progettazione.  
  
### <a name="to-debug-workflow-xaml"></a>Per eseguire il debug del flusso di lavoro XAML  
  
1.  Aprire un flusso di lavoro o un progetto di attività in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2.  Impostare un punto di interruzione nell'attività o attività che si desidera eseguire il debug come descritto in [come: Impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md).  
  
3.  Fare clic sul file con estensione XAML contenente la definizione del flusso di lavoro e selezionare **Visualizza codice**. Verrà visualizzato un punto di interruzione nella stessa riga in cui si trova la dichiarazione dell'elemento XAML dell'attività per la quale è stato impostato il punto di interruzione nella visualizzazione Progettazione.  
  
4.  Richiama il debugger, come descritto in [come: Richiama il Debugger del flusso di lavoro](../workflow-designer/how-to-invoke-the-workflow-debugger.md).  
  
5.  Quando l'esecuzione del codice raggiunge uno dei punti di interruzione, l'elemento XAML associato a tale punto verrà evidenziato. Per spostare il punto di interruzione successivo, usare il **F10** oppure **F11** chiave.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Procedura: Richiamare il debugger del flusso di lavoro](../workflow-designer/how-to-invoke-the-workflow-debugger.md)