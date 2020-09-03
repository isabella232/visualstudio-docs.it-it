---
title: Convertire un tipo anonimo in tupla
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
ms.openlocfilehash: f7e89c5b5a05900fe42af62ef87f70292e94e662
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094276"
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

   ![Convertire un tipo anonimo in tupla](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
