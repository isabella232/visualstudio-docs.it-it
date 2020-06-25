---
title: Semplificare l'espressione condizionale
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d0571c01217441d4a39fbfe6fb58ccfe95fd0c5a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290618"
---
# <a name="simplify-conditional-expression-refactoring"></a>Refactoring semplificato dell'espressione condizionale

Questo refactoring si applica a:

- C#

**Cosa:** Consente di semplificare un' [espressione condizionale](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).

**Quando:** Si vuole rimuovere il codice non necessario per fornire maggiore chiarezza.

**Motivo:** La semplificazione di un'espressione condizionale può fornire maggiore chiarezza e sintassi concisa. Questo strumento di refactoring eseguirà automaticamente l'attività invece di eseguirla manualmente.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore sull'espressione condizionale:

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare **semplifica espressione condizionale**

    ![Semplificare l'espressione condizionale](media/simplify-conditional-expression.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)