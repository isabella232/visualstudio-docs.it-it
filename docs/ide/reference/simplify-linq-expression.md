---
title: Semplifica espressione LINQ
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 04485d6ce67c822fd0620bd63f3557851db6dbb9
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2020
ms.locfileid: "88251318"
---
# <a name="simplify-linq-expression"></a>Semplifica espressione LINQ

Questo refactoring si applica a:

- C#

**Cosa:** Effettua il refactoring delle istanze di `SomeEnumerableType.Where(<LambdaExpression>).Single()` in `SomeEnumerable.Single(<LambdaExpression>)` per e `Enumerable.Single()` dei metodi enumerabili seguenti: `SingleOrDefault()` ,, `Last()` `LastOrDefault()` , `Any()` , `Count()` , `First()` e `FirstOrDefault()` .

**Quando:**  Tutte le istanze in cui il metodo chiama `Single()` , `SingleOrDefault()` e così via, non ha alcun argomento ed è preceduto da un' `Where()` espressione. L'input per l' `Where()` espressione non può essere costruito come albero delle espressioni.

**Motivo:** La rimozione della chiamata non necessaria a Enumerable per il `.Where()` metodo migliora le prestazioni e la leggibilità.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore all'interno dell' `SomeEnumerableType.Where(<LambdaExpression>).Single()` istanza in Visual Studio.
2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **semplifica espressione LINQ**

   ![Converti typeof in NameOf](media/simplify-linq-expression.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
