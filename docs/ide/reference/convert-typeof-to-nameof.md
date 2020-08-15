---
title: Converti typeof in NameOf
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
ms.openlocfilehash: 233393114883c2a9833aa7ec82f0d78f0ef33bae
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2020
ms.locfileid: "88251290"
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
  <br>Selezionare **Convert ' typeof ' in ' NameOf '** 
   ![ Convert typeof in NameOf](media/convert-type-of.PNG)

- Visual Basic
  <br>Selezionare **Convert ' GetType ' in ' NameOf '** ![ Convert typeof in NameOf](media/convert-get-type.PNG)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
