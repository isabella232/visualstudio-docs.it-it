---
title: Semplificare l'espressione LINQ
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 006fc0fe84b11573ece98019a4446d83de52d62c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957556"
---
# <a name="simplify-linq-expression"></a>Semplificare l'espressione LINQ

Questo refactoring si applica a:

- C#

**Cosa:** Effettua il refactoring delle istanze di `SomeEnumerableType.Where(<LambdaExpression>).Single()` in `SomeEnumerable.Single(<LambdaExpression>)` per e `Enumerable.Single()` dei metodi enumerabili seguenti: `SingleOrDefault()` ,, `Last()` `LastOrDefault()` , `Any()` , `Count()` , `First()` e `FirstOrDefault()` .

**Quando:**  Tutte le istanze in cui il metodo chiama `Single()` , `SingleOrDefault()` e così via, non ha alcun argomento ed è preceduto da un' `Where()` espressione. L'input per l' `Where()` espressione non può essere costruito come albero delle espressioni.

**Motivo:** La rimozione della chiamata non necessaria a Enumerable per il `.Where()` metodo migliora le prestazioni e la leggibilità.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore all'interno dell' `SomeEnumerableType.Where(<LambdaExpression>).Single()` istanza in Visual Studio.
2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **semplifica espressione LINQ**

   ![Convertire typeof in nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
