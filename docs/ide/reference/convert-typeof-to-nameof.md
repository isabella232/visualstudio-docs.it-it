---
title: Convertire typeof in nameof
description: Informazioni su come usare il menu azioni rapide e refactoring in Visual Studio per convertire typeof in NameOf in C# e GetType in NameOf in Visual Basic.
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
ms.openlocfilehash: ce76b82e2ebc68634be7cf4d463f6b8216d81e06
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761199"
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
      <br>Selezionare **Converti ' typeof ' in ' NameOf '**: ![ screenshot del menu azioni rapide e refactoring in Visual Studio con convert ' typeof ' in ' NameOf ' selezionato e modifiche del codice C# visualizzate.](media/convert-type-of.PNG)

    - Visual Basic
      <br>Selezionare **Converti ' GetType ' in ' NameOf '**: ![ screenshot del menu azioni rapide e refactoring in Visual Studio con convert ' GetType ' in ' NameOf ' selezionato e Visual Basic modifiche del codice visualizzate.](media/convert-get-type.PNG)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
