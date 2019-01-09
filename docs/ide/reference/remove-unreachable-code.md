---
title: Refactoring con rimozione del codice non eseguibile
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 481c0d116eb2aee2c4f931f1ca4cb2de7927c62e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842538"
---
# <a name="remove-unreachable-code-refactoring"></a>Refactoring con rimozione del codice non eseguibile

Questo refactoring si applica a:

- C#

**Cosa:** consente di rimuovere il codice che non verrà mai eseguito.

**Quando:** il programma non include un percorso a un frammento di codice e rende quindi superfluo tale frammento.

**Perché?:** migliorare leggibilità e facilità di gestione con la rimozione di codice superfluo che non verrà mai eseguito.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore in qualsiasi punto nel codice sfumato non eseguibile:

![Codice non eseguibile sfumato](media/unreachablecode-faded-cs.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Rimuovi il codice non eseguibile** dal popup della finestra di anteprima.
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