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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "68740044"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Convertire un'istruzione switch in un'espressione switch

Questo refactoring si applica a:

- C#

**Cosa:** Convertire [un'istruzione switch](/dotnet/csharp/language-reference/keywords/switch) in [un'espressione switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions)di C .

**Quando:** Si desidera convertire `switch` un'istruzione in un'espressione `switch` e viceversa. 

**Perché:** Se si utilizzano solo espressioni, questo refactoring `switch` consente una transizione semplice dalle istruzioni tradizionali.

## <a name="how-to"></a>Procedure

1. Nel file di progetto [impostare la versione del linguaggio come anteprima](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) poiché le espressioni `switch` sono una nuova funzionalità di C# 8.0.
2. Posizionare il `switch` cursore nella parola chiave e premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Convert switch statement to expression** (Converti istruzione switch in espressione).

   ![Convertire un'istruzione switch in un'espressione switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
