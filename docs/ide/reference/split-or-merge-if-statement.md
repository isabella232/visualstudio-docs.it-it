---
title: Istruzioni if di suddivisione o unione
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a3b42f83faacda6be34b282150cf4fb4c0f379f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "79093666"
---
# <a name="split-or-merge-if-statements"></a>Istruzioni if di suddivisione o unione

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa** **: le istruzioni Split o** merge [if](/dotnet/csharp/language-reference/keywords/if-else) .

**Quando:** Si desidera suddividere un'istruzione `if` che utilizza gli `&&` `||` operatori o in un'istruzione annidata `if` oppure unire un'istruzione `if` con un' `if` istruzione esterna.

**Motivo:** Si tratta di una situazione di preferenza dello stile.  

## <a name="how-to"></a>Procedure

Se si vuole dividere l'istruzione `if`:

1. Posizionare il cursore nell'istruzione `if` in corrispondenza dell'operatore `&&` o `||`.

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

    ![Dividere l'istruzione if](../media/split-if-statement.png)

3. Selezionare **Split into nested if statements** (Dividi in istruzioni if annidate).

    ![Divisione dell'istruzione if completata](../media/split-if-statement-complete.png)

Se si vuole unire l'istruzione `if` interna con l'istruzione `if` esterna: 

1. Posizionare il cursore nella parola chiave `if` interna.

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

    ![Unire l'istruzione if](../media/merge-if-statement.png)

3. Selezionare **Merge with outer if statement** (Unisci con istruzione if esterna).

    ![Unione delle istruzioni if completata](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)