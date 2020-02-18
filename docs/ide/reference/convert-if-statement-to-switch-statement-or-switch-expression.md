---
title: Converti istruzione if in istruzione switch o espressione switch
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cb0c06fe0493f973ea9cf0a566ffda45a49eeeff
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2020
ms.locfileid: "77280782"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Converti istruzione if in istruzione switch o espressione switch

Questo refactoring si applica a:

- C#

**Cosa:** Converte un'istruzione if in un' [istruzione switch](/dotnet/csharp/language-reference/keywords/switch) o nell' C# [espressione switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions)8,0.

**Quando:** Si vuole convertire un'istruzione `if` in un'istruzione `switch` o un'espressione `switch` e viceversa. 

**Motivo:** Se si usa un'istruzione `if`, questo refactoring consente una semplice transizione a istruzioni `switch` o `switch` espressioni.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nella parola chiave `if`.
2. Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Converti nell'istruzione ' switch '** .

   ![Converti istruzione if in istruzione switch o espressione switch](media/convert-if-statement-to-switch-statement-or-switch-expression.png) 

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
