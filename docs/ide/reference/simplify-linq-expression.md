---
title: Semplificare l'espressione LINQ
description: Questo refactoring viene usato per rimuovere le chiamate non necessarie a Enumerable per il metodo Where.
ms.date: 07/05/2021
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 4d97f56dbf3e8c4e3b198de413f6f4700ea4eb16
ms.sourcegitcommit: 811e4ee80311433fefbe6d6223bf72c431008403
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2021
ms.locfileid: "127890694"
---
# <a name="simplify-linq-expression"></a>Semplificare l'espressione LINQ

Questo refactoring si applica a:

- C#

**Cosa:** Refactoring di istanze di per e dei `SomeEnumerableType.Where(<LambdaExpression>).Single()` `SomeEnumerable.Single(<LambdaExpression>)` metodi `Enumerable.Single()` enumerabili seguenti: `SingleOrDefault()` , , , , , , e `Last()` `LastOrDefault()` `Any()` `Count()` `First()` `FirstOrDefault()` .

**Quando:**  Tutte le istanze in cui il metodo chiama , e così via, non hanno argomenti ed è `Single()` `SingleOrDefault()` preceduta da `Where()` un'espressione. L'input per `Where()` l'espressione non può essere costruito come albero delle espressioni.

**Perché:** La rimozione della chiamata non necessaria a Enumerable per il metodo migliora la leggibilità e, in alcuni casi, le `.Where()` prestazioni, vedere le osservazioni.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore all'interno `SomeEnumerableType.Where(<LambdaExpression>).Single()` dell'istanza di in Visual Studio.
2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Semplifica espressione LINQ**

   ![Convertire typeof in nameof](media/simplify-linq-expression.png)
   
## <a name="remarks"></a>Commenti

In alcuni casi questo refactoring può ridurre le prestazioni. Le operazioni LINQ `List<T>` su e non sono `T[]` ottimizzate in questo caso e comportano prestazioni peggiori.

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
