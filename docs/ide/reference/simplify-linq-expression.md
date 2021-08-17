---
title: Semplificare l'espressione LINQ
description: Questo refactoring viene usato per rimuovere le chiamate non necessarie a Enumerable per il metodo Where.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 951f7bebe8e63139326081c70615d91cf0b958018a964ac1928651a0cb2ac0f6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121446943"
---
# <a name="simplify-linq-expression"></a>Semplificare l'espressione LINQ

Questo refactoring si applica a:

- C#

**Cosa:** Refactoring delle istanze di in per e dei metodi `SomeEnumerableType.Where(<LambdaExpression>).Single()` `SomeEnumerable.Single(<LambdaExpression>)` `Enumerable.Single()` enumerabili seguenti: `SingleOrDefault()` , , , , , e `Last()` `LastOrDefault()` `Any()` `Count()` `First()` `FirstOrDefault()` .

**Quando:**  Tutte le istanze in cui il metodo chiama , e così via, non hanno argomenti ed `Single()` `SingleOrDefault()` è preceduta da `Where()` un'espressione. L'input per `Where()` l'espressione non può essere costruito come albero delle espressioni.

**Perché:** La rimozione della chiamata non necessaria a Enumerable per il `.Where()` metodo migliora le prestazioni e la leggibilità.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore all'interno `SomeEnumerableType.Where(<LambdaExpression>).Single()` dell'istanza di in Visual Studio.
2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Semplifica espressione LINQ**

   ![Convertire typeof in nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
