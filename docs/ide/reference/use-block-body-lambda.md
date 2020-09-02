---
title: Usare l'espressione lambda o il corpo del blocco
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5c46506e81e5334efea9060e957269e92e9d49cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531930"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Usare il corpo dell'espressione o il corpo del blocco per le espressioni lambda

Questo refactoring si applica a:

- C#

**Cosa:** Consente di effettuare il refactoring di un'espressione lambda per utilizzare il corpo di un'espressione o un corpo del blocco.

**Quando:** Si preferisce che le espressioni lambda usino il corpo di un'espressione o il corpo di un blocco.

**Motivo:** È possibile eseguire il refactoring delle espressioni lambda per migliorare la leggibilità in base alle preferenze dell'utente.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refactoring del corpo dell'espressione lambda o del corpo del blocco

1. Posizionare il cursore a destra di un operatore lambda.
2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

  ![Usare l'espressione lambda o il corpo del blocco](media/block-body-lambda.png)

3. Selezionare **Use block body for lambda expressions** (Usa il corpo del blocco per le espressioni lambda) o **Use expression body for lambda expressions** (Usa il corpo dell'espressione per le espressioni lambda).

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)