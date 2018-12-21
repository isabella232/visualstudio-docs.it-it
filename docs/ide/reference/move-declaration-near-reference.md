---
title: Spostare la dichiarazione di variabile vicino al riferimento
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 9bc661331ee03af6d34caeae847b717db1f21fc5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065342"
---
# <a name="move-declaration-near-reference-refactoring"></a>Refactoring con spostamento della dichiarazione vicino al riferimento

Questo refactoring si applica a:

- C#

**Cosa:** consente di spostare le dichiarazioni di variabili più vicino al punto in cui le variabili vengono usate.

**Quando:** in presenza di dichiarazioni di variabili che possono essere inserite in un ambito più ristretto.

**Perché?:** si può anche non intervenire, ma ciò può causare problemi di leggibilità o nascondere informazioni. Questa è un'opportunità di eseguire il refactoring per migliorare la leggibilità.

## <a name="how-to"></a>Procedura

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
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)