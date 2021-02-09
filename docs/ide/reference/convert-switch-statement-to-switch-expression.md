---
title: Convertire un'istruzione switch in un'espressione switch
description: Informazioni su come usare il menu azioni rapide e refactoring per convertire un'istruzione switch in un'espressione switch C# 8,0.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 56a1b20854cdd2c1821490bb4972d67bbe912056
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919668"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Convertire un'istruzione switch in un'espressione switch

Questo refactoring si applica a:

- C#

**Cosa:** Converte un' [istruzione switch](/dotnet/csharp/language-reference/keywords/switch) in un' [espressione switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8,0.

**Quando:** Si vuole convertire un' `switch` istruzione in un' `switch` espressione e viceversa. 

**Motivo:** Se si usano solo le espressioni, questo refactoring consente una semplice transizione dalle `switch` istruzioni tradizionali.

## <a name="how-to"></a>Procedure

1. Nel file di progetto [impostare la versione del linguaggio come anteprima](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) poiché le espressioni `switch` sono una nuova funzionalità di C# 8.0.
2. Posizionare il cursore nella `switch` parola chiave e premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Convert switch statement to expression** (Converti istruzione switch in espressione).

   ![Convertire un'istruzione switch in un'espressione switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
