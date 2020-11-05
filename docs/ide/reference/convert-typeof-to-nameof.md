---
title: Convertire typeof in nameof
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 96bd4d67302fb09e5c1cb7837ad73b345ad88c81
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400324"
---
# <a name="convert-typeof-to-nameof"></a>Convertire `typeof` in `nameof`

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Consente di convertire un'istanza di `typeof(<QualifiedType>).Name` in `nameof(<QualifiedType>)` C# e un'istanza di `GetType(<QualifiedType>).Name` `NameOf(<QualifiedType>)` in Visual Basic.

**Quando:**  Tutte le istanze di in `typeof(<QualifiedType>).Name` cui `someType` non è un tipo generico. Questa esclusione è necessaria perché in questo caso non viene restituito lo stesso valore di stringa di `nameof(<QualifiedType>)` . Lo stesso vale per l'istanza di Visual Basic.

**Motivo:** L'utilizzo di `nameof` anziché il nome di `type` evita la reflection che riguarda il recupero di un `type` oggetto ed è un modo più pragmatico di scriverlo.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore all'interno dell' `typeof(<QualifiedType>).Name` istanza per C# o `GetType(<QualifiedType>).Name` in Visual Basic.

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare una delle opzioni seguenti:

    - C#
      <br>Selezionare **Convert ' typeof ' in ' NameOf '** : ![ Convert typeof in NameOf](media/convert-type-of.PNG)

    - Visual Basic
      <br>Select **Convert ' GetType ' in ' NameOf '** : ![ Convert typeof in NameOf](media/convert-get-type.PNG)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
