---
title: Convertire typeof in nameof
description: Informazioni su come usare il menu Azioni rapide e refactoring in Visual Studio per convertire typeof in nameof in C# e GetType in NameOf in Visual Basic.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d37ae59d34968f91c95624784ce647831ef51804c4d67e8ad278472cacc1208f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121429939"
---
# <a name="convert-typeof-to-nameof"></a>Convertire `typeof` in `nameof`

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Consente di convertire un'istanza di `typeof(<QualifiedType>).Name` `nameof(<QualifiedType>)` in in C# e un'istanza di `GetType(<QualifiedType>).Name` in `NameOf(<QualifiedType>)` Visual Basic.

**Quando:**  Tutte le istanze `typeof(<QualifiedType>).Name` di in cui non è un tipo `someType` generico. Questa esclusione è necessaria perché questo caso non restituisce lo stesso valore stringa di `nameof(<QualifiedType>)` . Lo stesso vale per l'Visual Basic predefinita.

**Perché:** L'uso di anziché del nome di evita la reflection coinvolta nel recupero di un oggetto ed è `nameof` un modo più pratico per `type` `type` scriverlo.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore `typeof(<QualifiedType>).Name` all'interno dell'istanza di per C# o `GetType(<QualifiedType>).Name` in Visual Basic.

2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare una delle opzioni seguenti:

    - C#
      <br>Selezionare **Convert 'typeof' to 'nameof' (Converti 'typeof' in 'nameof'):** screenshot del menu Azioni rapide e refactoring in Visual Studio con l'opzione Convert 'typeof' to 'nameof' selezionata e le modifiche al codice ![ C# visualizzate.](media/convert-type-of.PNG)

    - Visual Basic
      <br>Selezionare **Convert 'GetType' to 'NameOf' (Converti 'GetType' in 'NameOf'):** screenshot del menu Azioni rapide e refactoring in Visual Studio con l'opzione Convert ![ 'GetType' to 'NameOf' selezionata e le modifiche al codice Visual Basic visualizzate.](media/convert-get-type.PNG)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
