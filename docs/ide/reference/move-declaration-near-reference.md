---
title: Spostare la dichiarazione di variabile vicino al riferimento in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: a76e6024a2b61bcae08fb8db169483bcee6e5d19
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2018
---
# <a name="move-declaration-near-reference-refactoring"></a>Refactoring con spostamento della dichiarazione vicino al riferimento

Questo refactoring si applica a:

- C#

**Cosa:** consente di spostare le dichiarazioni di variabili più vicino al loro utilizzo.

**Quando:** in presenza di dichiarazioni di variabili che possono essere in un ambito più ristretto.

**Perché:** si potrebbe non intervenire, ma ciò potrebbe causare problemi di leggibilità o nascondere informazioni. Questa è un'opportunità di eseguire il refactoring per migliorare la leggibilità.

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