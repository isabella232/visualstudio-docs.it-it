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
ms.openlocfilehash: 0242c8c89848e3e76673ddfbca8a27c20605048d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810350"
---
# <a name="simplify-conditional-expression-refactoring"></a>Refactoring semplificato dell'espressione condizionale

Questo refactoring si applica a:

- C#

**Cosa:** Consente di semplificare un' [espressione condizionale](/dotnet/csharp/language-reference/operators/conditional-operator).

**Quando:** Si vuole rimuovere il codice non necessario per fornire maggiore chiarezza.

**Motivo:** La semplificazione di un'espressione condizionale può fornire maggiore chiarezza e sintassi concisa. Questo strumento di refactoring eseguirà automaticamente l'attività invece di eseguirla manualmente.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore sull'espressione condizionale:

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare **semplifica espressione condizionale**

    ![Semplificare l'espressione condizionale](media/simplify-conditional-expression.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)