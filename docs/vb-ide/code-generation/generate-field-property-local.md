---
title: "Generare un campo, la proprietà o locale - la generazione di codice (Visual Basic) | Documenti Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8e23dfa2b482a16d70ef71614ba35f9b20523aeb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-field-property-or-local-in-visual-basic"></a>Generare un campo, la proprietà o locale in Visual Basic
**Novità:** consente di generare immediatamente il codice per un campo in precedenza non dichiarato, proprietà o locale. 

**Quando:** si introducono un nuovo campo, la proprietà o locale durante la digitazione e si desidera dichiarare in modo corretto, automaticamente.  

**Motivo:** prima di utilizzarlo, tuttavia questa funzionalità genera la dichiarazione e digitare automaticamente, è possibile dichiarare il campo, la proprietà o locale. 

**Procedura:**

1. Posizionare il cursore sulla riga in cui è presente una sottolineatura ondulata rossa che indica un campo, locale o una proprietà che non esiste ancora.

   ![Codice evidenziato](media/field_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu  **variabile genera '*nome*' > genera campo o la proprietà/locale * * da una finestra popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu  **variabile genera '*nome*' > genera campo/proprietà/locale * * dall'anteprima popup di finestra.
     * Passare il mouse sulla sottolineatura rossa e scegliere il ![Lampadina](media/bulb.png) icona che verrà visualizzata.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Generare l'anteprima di campo o proprietà/locale](media/field_preview.png)

   >[!TIP]
   >Utilizzare il [ **Anteprima modifiche** ](../../ide/preview-changes.md) collegamento nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche apportate prima di effettuare la selezione.

1. Il campo, la proprietà o locale verrà creata automaticamente con il tipo dedotto dal relativo utilizzo.

   ![Generare il risultato di campo o proprietà/locale](media/field_result.png)

## <a name="see-also"></a>Vedere anche  
[Code Generation (Visual Basic)](../code-generation-vb.md) (Generazione di codice (Visual Basic))  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)