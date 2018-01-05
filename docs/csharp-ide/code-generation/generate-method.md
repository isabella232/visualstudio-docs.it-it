---
title: Generare un metodo - la generazione di codice (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 2d0354549d01fb31a813630066c96f6378db4b7a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-method-in-c"></a>Generare un metodo in c# #
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
[Code Generation (C#)](../code-generation-csharp.md) (Generazione di codice (C#))  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
