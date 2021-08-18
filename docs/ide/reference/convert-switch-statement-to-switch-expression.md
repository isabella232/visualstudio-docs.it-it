---
title: Convertire un'istruzione switch in un'espressione switch
description: Informazioni su come usare il menu Azioni rapide e refactoring per convertire un'istruzione switch in un'espressione switch C# 8.0.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b7d01862774fd36bc5c9347df3fce6bd02c56263
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094152"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Convertire un'istruzione switch in un'espressione switch

Questo refactoring si applica a:

- C#

**Cosa:** Convertire [un'istruzione switch](/dotnet/csharp/language-reference/keywords/switch) in un'espressione [switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8.0 .

**Quando:** Si vuole convertire `switch` un'istruzione in `switch` un'espressione e viceversa. 

**Perché:** Se si usano solo espressioni, questo refactoring consente una transizione semplice dalle istruzioni `switch` tradizionali.

## <a name="how-to"></a>Procedure

1. Nel file di progetto [impostare la versione del linguaggio come anteprima](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) poiché le espressioni `switch` sono una nuova funzionalità di C# 8.0.
2. Posizionare il cursore nella `switch` parola chiave e premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Convert switch statement to expression** (Converti istruzione switch in espressione).

   ![Convertire un'istruzione switch in un'espressione switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
