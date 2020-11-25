---
title: Convertire un tipo anonimo in tupla
description: Informazioni su come usare il menu azioni rapide e refactoring per convertire un tipo anonimo in una tupla in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 452ba826a2765ef624e6c3d04bb20915a26c51fb
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040862"
---
# <a name="convert-anonymous-type-to-tuple"></a>Conversione di tipi anonimi in tupla

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Converte un tipo anonimo in Tuple.

**Quando:** Si dispone di un tipo anonimo che si qualifica come tupla.

**Perché:** le [Tuple](/dotnet/csharp/tuples) sono utili per mantenere la sintassi leggera. Questa azione rapida consente di usare più facilmente questa funzionalità di C#.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore in un tipo anonimo.
2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

   ![Convertire un tipo anonimo in tupla](media/convert-anon-to-tuple.png)

2. Premere **invio** per accettare il refactoring.

   ![Converti tipo anonimo in tupla accettata](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
