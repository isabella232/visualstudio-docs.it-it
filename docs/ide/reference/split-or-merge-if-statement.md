---
title: Istruzioni if di suddivisione o unione
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 405ccd4bc0197ce06aa14982a16dc02f6d13a537
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160737"
---
# <a name="split-or-merge-if-statements"></a>Istruzioni if di suddivisione o unione

Questo refactoring si applica a:

- C#

**Cosa:** **Cosa:** dividere o unire istruzioni [if](/dotnet/csharp/language-reference/keywords/if-else).

**Quando:** si vuole dividere un'istruzione `if` che usa l'operatore `&&` o `||` in un'istruzione `if` annidata oppure unire un'istruzione `if` con un'istruzione `if` esterna.

**Perché?:** si tratta di una preferenza di stile.  

## <a name="how-to"></a>Procedura

Se si vuole dividere l'istruzione `if`:

1. Posizionare il cursore nell'istruzione `if` in corrispondenza dell'operatore `&&` o `||`.

2. Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.

    ![Dividere l'istruzione if](../media/split-if-statement.png)

3. Selezionare **Split into nested if statements** (Dividi in istruzioni if annidate).

    ![Divisione dell'istruzione if completata](../media/split-if-statement-complete.png)

Se si vuole unire l'istruzione `if` interna con l'istruzione `if` esterna: 

1. Posizionare il cursore nella parola chiave `if` interna.

2. Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.

    ![Unire l'istruzione if](../media/merge-if-statement.png)

3. Selezionare **Merge with outer if statement** (Unisci con istruzione if esterna).

    ![Unione delle istruzioni if completata](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)