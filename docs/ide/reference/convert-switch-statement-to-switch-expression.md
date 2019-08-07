---
title: Convertire un'istruzione switch in un'espressione switch
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cc13cffe8352d9fb57f5bb991c3af615eddb2a14
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/02/2019
ms.locfileid: "68740044"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Convertire un'istruzione switch in un'espressione switch

Questo refactoring si applica a:

- C#

**Cosa:** convertire un'[istruzione switch](/dotnet/csharp/language-reference/keywords/switch) in un'[espressione switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions) di C# 8.0.

**Quando:** si vuole convertire un'istruzione `switch` in un'espressione `switch` e viceversa. 

**Perché?:** se si usano solo le espressioni, questo refactoring facilita la transizione dalle istruzioni `switch` tradizionali.

## <a name="how-to"></a>Procedura

1. Nel file di progetto [impostare la versione del linguaggio come anteprima](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) poiché le espressioni `switch` sono una nuova funzionalità di C# 8.0.
2. Posizionare il cursore nella parola chiave `switch` e premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Convert switch statement to expression** (Converti istruzione switch in espressione).

   ![Convertire un'istruzione switch in un'espressione switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
