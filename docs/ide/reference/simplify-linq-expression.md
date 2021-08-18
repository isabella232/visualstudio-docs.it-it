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
ms.openlocfilehash: dc52c81b8899d5b2d2ef3fb22581d3f7ef6c1a68
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041100"
---
# <a name="simplify-linq-expression"></a>Semplificare l'espressione LINQ

Questo refactoring si applica a:

- C#

**Cosa:** Refactoring di istanze di per e dei `SomeEnumerableType.Where(<LambdaExpression>).Single()` `SomeEnumerable.Single(<LambdaExpression>)` metodi `Enumerable.Single()` enumerabili seguenti: `SingleOrDefault()` , , , , , , e `Last()` `LastOrDefault()` `Any()` `Count()` `First()` `FirstOrDefault()` .

**Quando:**  Tutte le istanze in cui il metodo chiama , e così via, non hanno argomenti ed è `Single()` `SingleOrDefault()` preceduta da `Where()` un'espressione. L'input per `Where()` l'espressione non può essere costruito come albero delle espressioni.

**Perché:** La rimozione della chiamata non necessaria a Enumerable per il `.Where()` metodo migliora le prestazioni e la leggibilità.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore all'interno `SomeEnumerableType.Where(<LambdaExpression>).Single()` dell'istanza di in Visual Studio.
2. Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Semplifica espressione LINQ**

   ![Convertire typeof in nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
