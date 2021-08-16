---
title: Usare l'espressione lambda o il corpo del blocco
description: Informazioni su come usare il menu Azioni rapide e refactoring per eseguire il refactoring di un'espressione lambda per usare un corpo dell'espressione o un corpo del blocco.
ms.custom: SEO-VS-2020
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e6262c3ac7b9a95c173d4adc9c5c5a82767a326afe273d6838289ccfdedc5110
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412095"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Usare il corpo dell'espressione o il corpo del blocco per le espressioni lambda

Questo refactoring si applica a:

- C#

**Cosa:** Consente di eseguire il refactoring di un'espressione lambda per usare un corpo dell'espressione o un corpo del blocco.

**Quando:** Si preferisce che le espressioni lambda usino un corpo dell'espressione o un corpo del blocco.

**Perché:** È possibile eseguire il refactoring delle espressioni lambda per migliorare la leggibilità in base alle preferenze dell'utente.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refactoring del corpo dell'espressione lambda o del corpo del blocco

1. Posizionare il cursore a destra di un operatore lambda.
2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

  ![Usare l'espressione lambda o il corpo del blocco](media/block-body-lambda.png)

3. Selezionare **Use block body for lambda expressions** (Usa il corpo del blocco per le espressioni lambda) o **Use expression body for lambda expressions** (Usa il corpo dell'espressione per le espressioni lambda).

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)