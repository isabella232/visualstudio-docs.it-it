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
ms.openlocfilehash: 98f1680b63060f820bf8c7a8b23efd2731e18f98
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101518"
---
# <a name="convert-typeof-to-nameof"></a>Convertire `typeof` in `nameof`

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Consente di convertire un'istanza `typeof(<QualifiedType>).Name` di `nameof(<QualifiedType>)` in C# e un'istanza di `GetType(<QualifiedType>).Name` in `NameOf(<QualifiedType>)` Visual Basic.

**Quando:**  Tutte le istanze `typeof(<QualifiedType>).Name` di dove non è un tipo `someType` generico. Questa esclusione è necessaria perché questo caso non restituisce lo stesso valore stringa di `nameof(<QualifiedType>)` . Lo stesso vale per l'istanza Visual Basic.

**Perché:** L'uso di anziché del nome di evita la reflection implicata nel recupero di un oggetto ed è un modo `nameof` `type` più pratico per `type` scriverlo.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore `typeof(<QualifiedType>).Name` all'interno dell'istanza per C# o `GetType(<QualifiedType>).Name` in Visual Basic.

2. Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare una delle opzioni seguenti:

    - C#
      <br>Selezionare **Converti 'typeof' in 'nameof':** screenshot del menu Azioni rapide e refactoring in Visual Studio con l'opzione Convert 'typeof' to 'nameof' selezionata e le modifiche al codice ![ C# visualizzate.](media/convert-type-of.PNG)

    - Visual Basic
      <br>Selezionare **Convert 'GetType' to 'NameOf' (Converti 'GetType' in 'NameOf'):** screenshot del menu Azioni rapide e refactoring in Visual Studio con l'opzione Convert ![ 'GetType' to 'NameOf' selezionata e Visual Basic le modifiche al codice visualizzate.](media/convert-get-type.PNG)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
