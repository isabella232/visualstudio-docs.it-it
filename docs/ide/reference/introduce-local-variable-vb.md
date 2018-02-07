---
title: Introdurre una variabile locale - Generazione del codice (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: abc0ef3ffdbada86a66bac9823894ee83d04047f
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2018
---
# <a name="introduce-a-local-variable-in-visual-basic"></a>Introdurre una variabile locale in Visual Basic
**Cosa:** consente di generare immediatamente una variabile locale per sostituire un'espressione esistente.

**Quando:** si dispone di codice che potrebbe essere facilmente riutilizzato in un secondo momento se fosse in una variabile locale.  

**Perché:** è possibile copiare e incollare il codice più volte per usarlo in varie posizioni, ma sarebbe preferibile eseguire l'operazione una sola volta, archiviare il risultato in una variabile locale e usare poi la variabile locale. 

**Come:**

1. Evidenziare l'espressione che si vuole assegnare a una nuova variabile locale.

   ![Codice evidenziato](media/local-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Introduce l'elemento locale per tutte le occorrenze di '*espressione*'** dal popup della finestra di anteprima, dove *espressione* è il codice evidenziato.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Introduce l'elemento locale per tutte le occorrenze di '*espressione*'** dal popup della finestra di anteprima, dove *espressione* è il codice evidenziato.
     * Fare clic sul pulsante ![lampadina](media/bulb-vb.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima di Introduce l'elemento locale](media/local-preview-vb.png)

   >[!TIP]
   >Usare il collegamento [**Anteprima modifiche**](../../ide/preview-changes.md) nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche che verranno apportate prima di effettuare la selezione.

1. La variabile verrà creata automaticamente con il tipo dedotto dal relativo utilizzo.  Assegnare alla nuova variabile locale un nuovo nome digitandolo.

   ![Risultato di Introduce l'elemento locale](media/local-result-vb.png)

   >[!NOTE]
   >È possibile usare l'opzione di menu **....tutte le occorrenze di...** per sostituire ogni istanza dell'espressione selezionata trovata e non solo quella evidenziata in modo specifico.

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md) 