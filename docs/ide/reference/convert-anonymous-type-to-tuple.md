---
title: Convertire un tipo anonimo in tupla
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b6f5dd8e53ed2e0695370a1cdcb837609be30035
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968572"
---
# <a name="convert-anonymous-type-to-tuple"></a>Conversione di tipi anonimi in tupla

Questo refactoring si applica a:

- C#

**Cosa:** convertire un tipo anonimo in tupla.

**Quando:** si ha un tipo anonimo con le caratteristiche di una tupla.

**Perché?:** le [tuple](/dotnet/csharp/tuples) sono utili per mantenere leggera la sintassi. Questa azione rapida consente di usare più facilmente questa funzionalità di C#.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore in un tipo anonimo.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

   ![Convertire un tipo anonimo in tupla](media/convert-anon-to-tuple.png)

2. Premere **INVIO** per accettare il refactoring.

   ![Convertire un tipo anonimo in tupla](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
