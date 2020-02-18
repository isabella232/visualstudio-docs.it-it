---
title: Semplificazione dell'interpolazione di stringhe
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 15f034b0ecf46e19681f3b74e4137a2de9e9d950
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2020
ms.locfileid: "77280754"
---
# <a name="simplify-string-interpolation-refactoring"></a>Semplificazione del refactoring dell'interpolazione di stringhe

Questo refactoring si applica a:

- C#

**Cosa:** Consente di semplificare un' [interpolazione di stringhe](https://docs.microsoft.com/dotnet/csharp/tutorials/string-interpolation).

**Quando:** Si dispone di un'interpolazione di stringhe che può essere semplificata.

**Motivo:** La semplificazione di un'interpolazione di stringhe può fornire maggiore chiarezza e sintassi concisa. Questo strumento di refactoring eseguirà automaticamente l'attività invece di eseguirla manualmente.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore sull'interpolazione di stringhe:

2. Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare **semplifica l'interpolazione**

    ![Semplificazione dell'interpolazione di stringhe](media/simplify-string-interpolation.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)