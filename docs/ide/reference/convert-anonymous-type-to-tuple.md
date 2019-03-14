---
title: Convertire un tipo anonimo in tupla
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b7a53aa8f329c1cdedc0cedff7e56b3f6dfa2f2a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335825"
---
# <a name="convert-anonymous-type-to-tuple"></a>Conversione di tipi anonimi in tupla

Questo refactoring si applica a:

- C#

**Cosa:** convertire un tipo anonimo in tupla.

**Quando:** si ha un tipo anonimo con le caratteristiche di una tupla.

**Perché:** le [tuple](/dotnet/csharp/tuples) sono utili per mantenere leggera la sintassi. Questa azione rapida consente di usare più facilmente questa funzionalità di C#.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore in un tipo anonimo.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

   ![Convertire un tipo anonimo in tupla](media/convert-anon-to-tuple.png)

2. Premere **INVIO** per accettare il refactoring.

   ![Convertire un tipo anonimo in tupla](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)