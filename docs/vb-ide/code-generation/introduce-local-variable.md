---
title: Introdurre una variabile locale - la generazione di codice (Visual Basic) | Documenti Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9caafd73703478c75d7d91708ddcf5d14139e7fa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="introduce-a-local-variable-in-visual-basic"></a>Introdurre una variabile locale in Visual Basic
**Novità:** consente di generare immediatamente una variabile locale per sostituire un'espressione esistente.

**Quando:** si dispone di codice che può essere facilmente riutilizzato in un secondo momento se si trattasse di una variabile locale.  

**Motivo:** è possibile copiare e incollare il codice più volte di usarlo in varie posizioni, ma sarebbe preferibile eseguire l'operazione una volta e memorizza il risultato in una variabile locale, utilizzare il throughought variabile locale. 

**Procedura:**

1. Evidenziare l'espressione che si desidera assegnare a una nuova variabile locale.

   ![Codice evidenziato](media/local_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu  **introdurre locale (tutte le occorrenze di) '*espressione*' * * da una finestra popup di finestra di anteprima, in cui *espressione* è il codice evidenziato.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu  **introdurre locale (tutte le occorrenze di) '*espressione*' * * da una finestra popup di finestra di anteprima, dove *espressione* è il codice evidenziato.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Introdurre anteprima locale](media/local_preview.png)

   >[!TIP]
   >Utilizzare il [ **Anteprima modifiche** ](../../ide/preview-changes.md) collegamento nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche apportate prima di effettuare la selezione.

1. La variabile locale verrà creata automaticamente con il tipo dedotto dal relativo utilizzo.  Assegnare la nuova variabile locale di un nuovo nome digitandolo.

   ![Introdurre risultati locali](media/local_result.png)

   >[!NOTE]
   >È possibile utilizzare il **.... tutti le occorrenze di...**  opzione di menu per sostituire ogni istanza dell'espressione selezionata viene trovato, non solo gli elementi in modo specifico viene evidenziato.

## <a name="see-also"></a>Vedere anche  
[Code Generation (Visual Basic)](../code-generation-vb.md) (Generazione di codice (Visual Basic))  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md) 