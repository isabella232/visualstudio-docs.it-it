---
title: Generare un costruttore - la generazione di codice (Visual Basic) | Documenti Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 53b1ab5cb202995cb6a5e9eeef76ee4cf38b4ea9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-constructor-in-visual-basic"></a>Generare un costruttore in Visual Basic
**Novità:** consente di generare immediatamente il codice per un nuovo costruttore in una classe. 

**Quando:** si introducono un nuovo costruttore e si desidera dichiarare in modo corretto, automaticamente.  

**Motivo:** era possibile dichiarare il costruttore prima di utilizzarlo, tuttavia questa funzionalità verrà generato automaticamente, con i parametri appropriati, automaticamente. 

**Procedura:**

1. Posizionare il cursore sulla riga in cui è presente una sottolineatura ondulata rossa che indica è stato usato un costruttore che non esiste ancora.

   ![Codice evidenziato](media/constructor_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu  **genera costruttore '*TypeName*' * * nel popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu  **genera costruttore '*TypeName*' * * nel popup di finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa e scegliere il ![Lampadina](media/bulb.png) icona che verrà visualizzata.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Generare l'anteprima di costruttore](media/constructor_preview.png)

   >[!TIP]
   >Utilizzare il [ **Anteprima modifiche** ](../../ide/preview-changes.md) collegamento nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche apportate prima di effettuare la selezione.

1. Verrà creato automaticamente il costruttore con parametri dedotti dal relativo utilizzo.

   ![Generare il risultato di costruttore](media/constructor_result.png)
  
## <a name="see-also"></a>Vedere anche  
[Code Generation (Visual Basic)](../code-generation-vb.md) (Generazione di codice (Visual Basic))  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)