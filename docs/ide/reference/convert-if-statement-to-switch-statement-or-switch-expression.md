---
title: Convertire l'istruzione if in un'istruzione o un'espressione switch
description: Informazioni su come usare il menu Azioni rapide e refactoring per convertire un'istruzione if in un'istruzione switch o in un'espressione switch C# 8.0.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ad4dfd3450bdbc8c6210133c4d61f495353a1e9a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117410"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Convertire un'istruzione if in un'istruzione switch o un'espressione switch

Questo refactoring si applica a:

- C#

**Cosa:** Convertire un'istruzione if in [un'istruzione switch](/dotnet/csharp/language-reference/keywords/switch) o nell'espressione switch di C# 8.0. [](/dotnet/csharp/whats-new/csharp-8#switch-expressions)

**Quando:** Si vuole convertire `if` un'istruzione in `switch` un'istruzione o `switch` un'espressione e viceversa.

**Perché:** Se si usa `if` un'istruzione , questo refactoring consente una transizione semplice a istruzioni o `switch` `switch` espressioni.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nella parola chiave `if`.
2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare una delle due opzioni seguenti:

    Selezionare **Converti in istruzione 'switch'.**

   ![Convertire l'istruzione if in istruzione switch](media/convert-if-to-switch-statement.png)

    Selezionare **Convert to 'switch' expression (Converti in espressione 'switch').**

    ![Convertire l'istruzione if in un'espressione switch](media/convert-if-to-switch-expression.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
