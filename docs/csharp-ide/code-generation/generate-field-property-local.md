---
title: "Generare un campo, proprietà o locale - la generazione di codice (c#) | Documenti Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 85d15d28fae994f029e678183d2f08d561c70f1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-field-property-or-local-in-c"></a>Generare un campo, proprietà o locale in c# #
**Novità:** consente di generare immediatamente il codice per un campo in precedenza non dichiarato, proprietà o locale. 

**Quando:** si introducono un nuovo campo, la proprietà o locale durante la digitazione e si desidera dichiarare in modo corretto, automaticamente.  

**Motivo:** prima di utilizzarlo, tuttavia questa funzionalità genera la dichiarazione e digitare automaticamente, è possibile dichiarare il campo, la proprietà o locale. 

**Procedura:**

1. Posizionare il cursore sulla riga in cui è presente una sottolineatura ondulata rossa che indica un campo, locale o una proprietà che non esiste ancora.

   ![Codice evidenziato](media/field_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **genera proprietà/campo/locale** nel popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu **genera proprietà/campo/locale** nel popup di finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa e scegliere il ![Lampadina](media/bulb.png) icona che verrà visualizzata.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Generare l'anteprima di campo o proprietà/locale](media/field_preview.png)

   >[!TIP]
   >Utilizzare il [ **Anteprima modifiche** ](../../ide/preview-changes.md) collegamento nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche apportate prima di effettuare la selezione.

1. Il campo, la proprietà o locale verrà creata automaticamente con il tipo dedotto dal relativo utilizzo.

   ![Generare il risultato di campo o proprietà/locale](media/field_result.png)

## <a name="see-also"></a>Vedere anche  
[Code Generation (C#)](../code-generation-csharp.md) (Generazione di codice (C#))  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md) 
