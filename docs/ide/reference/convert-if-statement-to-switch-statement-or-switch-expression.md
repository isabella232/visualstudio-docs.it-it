---
title: Convertire un'istruzione if in un'istruzione switch o un'espressione switch
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 93ad96809c77d5644b13e6221a41f0b182fb448f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094149"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Convertire un'istruzione if in un'istruzione switch o un'espressione switch

Questo refactoring si applica a:

- C#

**Cosa:** Convertire un'istruzione if in [un'istruzione switch](/dotnet/csharp/language-reference/keywords/switch) o nell'espressione [switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions)di C. 8.0 .

**Quando:** Si desidera convertire `if` un'istruzione in un'istruzione `switch` o un'espressione `switch` e viceversa. 

**Perché:** Se si utilizza `if` un'istruzione, questo refactoring `switch` consente `switch` una transizione semplice a istruzioni o espressioni.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nella parola chiave `if`.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare una delle due opzioni seguenti: 

    Selezionare **Converti in istruzione 'switch'.**

   ![Converti istruzione if in istruzione switch](media/convert-if-to-switch-statement.png) 

    Selezionare **Converti in espressione 'switch'.** 

    ![Converti istruzione if in espressione switch](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
