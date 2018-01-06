---
title: Implementare una classe astratta - la generazione di codice (Visual Basic) | Documenti Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 663a5ed393502d24c8b677dd2776a87b9855540e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="implement-an-abstract-class-in-visual-basic"></a>Implementare una classe astratta in Visual Basic
**Novità:** consente di generare immediatamente il codice necessario per implementare una classe astratta. 

**Quando:** per ereditare da una classe astratta.  

**Motivo:** è possibile implementare manualmente tutti i membri astratti, uno alla volta, tuttavia questa funzionalità genera automaticamente tutte le firme di metodo. 

**Procedura:**

1. Posizionare il cursore sulla riga in cui è presente una sottolineatura ondulata rossa che indica sono ereditate da una classe astratta, ma non sono implementati tutti i membri obbligatori.

   ![Codice evidenziato](media/abstract_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **implementa classe astratta** nel popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu **implementa classe astratta** nel popup di finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa e scegliere il ![Lampadina](media/bulb.png) icona che verrà visualizzata.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima di classe di implementazione](media/abstract_preview.png)

   >[!TIP]
   >Utilizzare il [ **Anteprima modifiche** ](../../ide/preview-changes.md) collegamento nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche apportate prima di effettuare la selezione.
   >
   >Inoltre, è possibile utilizzare il **documento**, **progetto**, e **soluzione** collegamenti nella parte inferiore della finestra di anteprima per creare le firme del metodo corretto in più classi che ereditano dalla classe astratta.

1. Le firme del metodo astratto saranno creati automaticamente, pronto per essere implementato.

   ![Implementare il risultato di classe](media/abstract_result.png)

## <a name="see-also"></a>Vedere anche  
[Code Generation (Visual Basic)](../code-generation-vb.md) (Generazione di codice (Visual Basic))  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)