---
title: Refactoring con rimozione del codice non eseguibile
description: Informazioni su come usare il menu Azioni rapide e refactoring per rimuovere il codice che non verrà mai eseguito.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 66ea34ff9cf8ba60775d12da001d49b58747d1c6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117202"
---
# <a name="remove-unreachable-code-refactoring"></a>Refactoring con rimozione del codice non eseguibile

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di rimuovere il codice che non verrà mai eseguito.

**Quando:** il programma non include un percorso a un frammento di codice, rendendo il frammento di codice superfluo.

**Motivo:** migliorare leggibilità e facilità di gestione con la rimozione di codice superfluo che non verrà mai eseguito.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore in qualsiasi punto nel codice sfumato non eseguibile:

![Codice non eseguibile sfumato](media/unreachablecode-faded-cs.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring** e selezionare **Rimuovi il codice non eseguibile** dal popup della finestra di anteprima.
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

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
