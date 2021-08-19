---
title: Istruzioni if di suddivisione o unione
description: Informazioni su come usare il menu Azioni rapide e refactoring per suddividere o unire istruzioni if.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9d34aa066d84deeaf4ac16f683822d539b0d1357
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117072"
---
# <a name="split-or-merge-if-statements"></a>Istruzioni if di suddivisione o unione

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** **Cosa: Dividere** o unire [istruzioni](/dotnet/csharp/language-reference/keywords/if-else) if.

**Quando:** Si vuole suddividere un'istruzione che usa gli operatori o in un'istruzione annidata oppure unire `if` `&&` `||` `if` `if` un'istruzione con un'istruzione `if` esterna.

**Perché:** Si tratta di una questione di preferenza di stile.  

## <a name="how-to"></a>Procedure

Se si vuole dividere l'istruzione `if`:

1. Posizionare il cursore nell'istruzione `if` in corrispondenza dell'operatore `&&` o `||`.

2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

    ![Dividere l'istruzione if](../media/split-if-statement.png)

3. Selezionare **Split into nested if statements** (Dividi in istruzioni if annidate).

    ![Divisione dell'istruzione if completata](../media/split-if-statement-complete.png)

Se si vuole unire l'istruzione `if` interna con l'istruzione `if` esterna: 

1. Posizionare il cursore nella parola chiave `if` interna.

2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

    ![Unire l'istruzione if](../media/merge-if-statement.png)

3. Selezionare **Merge with outer if statement** (Unisci con istruzione if esterna).

    ![Unione delle istruzioni if completata](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)