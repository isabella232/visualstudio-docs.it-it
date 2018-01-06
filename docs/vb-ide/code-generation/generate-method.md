---
title: Generare un metodo - la generazione di codice (Visual Basic) | Documenti Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 93736bfbf2e0a97965e44978e379f0cbe40f656a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-method-in-visual-basic"></a>Generare un metodo in Visual Basic
**Novità:** consente di aggiungere immediatamente un metodo a una classe. 

**Quando:** si introducono un nuovo metodo e si desidera dichiarare in modo corretto, automaticamente.  

**Motivo:** era possibile dichiarare il metodo e i parametri prima di utilizzarlo, tuttavia questa funzionalità genera automaticamente la dichiarazione. 

**Procedura:**

1. Posizionare il cursore sulla riga in cui è presente una sottolineatura ondulata rossa che indica è stato utilizzato un metodo che non esiste ancora.

   ![Codice evidenziato](media/method_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **generare il metodo** nel popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu **generare il metodo** nel popup di finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa e scegliere il ![Lampadina](media/bulb.png) icona che verrà visualizzata.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Generare l'anteprima (metodo)](media/method_preview.png)

   >[!TIP]
   >Utilizzare il [ **Anteprima modifiche** ](../../ide/preview-changes.md) collegamento nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche apportate prima di effettuare la selezione.

1. Il metodo verrà creato automaticamente con i parametri dedotti dal relativo utilizzo.

   ![Generare il risultato (metodo)](media/method_result.png)
  
## <a name="see-also"></a>Vedere anche  
[Code Generation (Visual Basic)](../code-generation-vb.md) (Generazione di codice (Visual Basic))  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)