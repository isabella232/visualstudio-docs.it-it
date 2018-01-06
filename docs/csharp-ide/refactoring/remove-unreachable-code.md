---
title: Rimuovere il codice non raggiungibile - Refactoring (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: e57db74ea431d9090df1dc34fd3cff3cf03dd475
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="remove-unreachable-code-in-c"></a>Rimuovere codice non eseguibile in c# #
**Novità:** rimuove il codice che non verrà mai eseguito.

**Quando:** il programma non ha un percorso a un frammento di codice, rendendo il frammento di codice non necessari.

**Motivo:** migliorare la leggibilità e facilità di gestione con la rimozione di codice che sarebbe superflua e non verrà mai eseguito.

**Procedura:**

1. Posizionare il cursore in qualsiasi punto nel codice che non è raggiungibile in dissolvenza out:

![Codice non eseguibile in dissolvenza](media/unreachablecode_faded.png)  

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **rimuovere codice non eseguibile** nel popup di finestra di anteprima.
   * **Mouse**
     * Pulsante destro del mouse nel codice, selezionare il **azioni rapide e refactoring** dal menu **rimuovere codice non eseguibile** nel popup di finestra di anteprima.

1. Quando si è soddisfatti della modifica, premere **invio** o scegliere la correzione nel menu e le modifiche verranno salvate.

Esempio:
```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>Vedere anche  
[Refactoring (C#)](../refactoring-csharp.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)