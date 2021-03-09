---
title: Semplificare l'espressione LINQ
description: Questo refactoring viene usato per rimuovere le chiamate non necessarie a Enumerable per il metodo Where.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 20a3524d786b1f03fc3e221d1b257892d9439a0b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466167"
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
