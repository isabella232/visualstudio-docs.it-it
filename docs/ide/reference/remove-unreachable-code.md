---
title: Refactoring con rimozione del codice non eseguibile
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1e5bdab773cf70963e1d0f485a7779e57084c8a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655597"
---
# <a name="remove-unreachable-code-refactoring"></a>Refactoring con rimozione del codice non eseguibile

Questo refactoring si applica a:

- C#

**Cosa:** consente di rimuovere il codice che non verrà mai eseguito.

**Quando:** il programma non include un percorso a un frammento di codice, rendendo il frammento di codice superfluo.

**Motivo:** migliorare leggibilità e facilità di gestione con la rimozione di codice superfluo che non verrà mai eseguito.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore in qualsiasi punto nel codice sfumato non eseguibile:

![Codice non eseguibile sfumato](media/unreachablecode-faded-cs.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Rimuovi il codice non eseguibile** dal popup della finestra di anteprima.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Rimuovi il codice non eseguibile** dal popup della finestra di anteprima.

1. Quando si è soddisfatti della modifica, premere **INVIO** o fare clic sulla correzione nel menu. Verrà eseguito il commit delle modifiche.

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

- [Refactoring](../refactoring-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)