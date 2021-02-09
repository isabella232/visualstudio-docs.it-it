---
title: Spostare la dichiarazione di variabile vicino al riferimento
description: Informazioni su come usare il menu azioni rapide e refactoring per spostare dichiarazioni di variabili più vicine al loro utilizzo.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce731da61c0c119869c1c1b85a87ebe44fabf273
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927925"
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
      - Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Sposta la dichiarazione accanto al riferimento** dal popup della finestra di anteprima.
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

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
