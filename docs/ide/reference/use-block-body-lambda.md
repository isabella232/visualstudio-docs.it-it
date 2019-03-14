---
title: Usare l'espressione lambda o il corpo del blocco
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 01ea32ffe978d7b1544597857187f00bec9c3467
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324766"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Usare il corpo dell'espressione o il corpo del blocco per le espressioni lambda

Questo refactoring si applica a:

- C#

**Cosa:** consente di effettuare il refactoring di un'espressione lambda per usare un corpo dell'espressione o un corpo del blocco.

**Quando:** si preferiscono le espressioni lambda per usare un corpo dell'espressione o un corpo del blocco. 

**Perché?:** è possibile effettuare il refactoring delle espressioni lambda per migliorare la leggibilità in base alle preferenze dell'utente.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refactoring del corpo dell'espressione lambda o del corpo del blocco

1. Posizionare il cursore a destra di un operatore lambda.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

  ![Usare l'espressione lambda o il corpo del blocco](media/block-body-lambda.png)

3. Selezionare **Use block body for lambda expressions** (Usa il corpo del blocco per le espressioni lambda) o **Use expression body for lambda expressions** (Usa il corpo dell'espressione per le espressioni lambda).

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)