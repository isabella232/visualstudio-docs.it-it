---
title: Spostare la dichiarazione di variabile vicino al riferimento
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 1339f4a9d151ef41d9a35c5aac0a96f220a297b3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093996"
---
# <a name="move-declaration-near-reference-refactoring"></a>Refactoring con spostamento della dichiarazione vicino al riferimento

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di spostare le dichiarazioni di variabili più vicino al loro utilizzo.

**Quando:** in presenza di dichiarazioni di variabili che possono essere in un ambito più ristretto.

**Perché:** si potrebbe non intervenire, ma ciò potrebbe causare problemi di leggibilità o nascondere informazioni. Questa è un'opportunità di eseguire il refactoring per migliorare la leggibilità.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nella dichiarazione della variabile.

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Sposta la dichiarazione accanto al riferimento** dal popup della finestra di anteprima.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Sposta la dichiarazione accanto al riferimento** dal popup della finestra di anteprima.

1. Quando si è soddisfatti della modifica, premere **INVIO** o fare clic sulla correzione nel menu. Verrà eseguito il commit delle modifiche.

Esempio:

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima delle modifiche](../../ide/preview-changes.md)
