---
title: Converti istruzione If nell'istruzione switch o nell'espressione
description: Informazioni su come usare il menu azioni rapide e refactoring per convertire un'istruzione if in un'istruzione switch o in un'espressione switch C# 8,0.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0d857338eb1c9b5bb66ccb89e20e6f892944d608
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936830"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Convertire un'istruzione if in un'istruzione switch o un'espressione switch

Questo refactoring si applica a:

- C#

**Cosa:** Converte un'istruzione if in un' [istruzione switch](/dotnet/csharp/language-reference/keywords/switch) o nell' [espressione switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8,0.

**Quando:** Si vuole convertire un' `if` istruzione in un' `switch` istruzione o in un' `switch` espressione e viceversa.

**Motivo:** Se si utilizza un' `if` istruzione, questo refactoring consente una semplice transizione a `switch` istruzioni o `switch` espressioni.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nella parola chiave `if`.
2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare una delle due opzioni seguenti:

    Selezionare **Converti nell'istruzione ' switch '**.

   ![Converti istruzione If nell'istruzione switch](media/convert-if-to-switch-statement.png)

    Selezionare **Converti in espressione ' switch '**.

    ![Converti istruzione if in espressione switch](media/convert-if-to-switch-expression.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
