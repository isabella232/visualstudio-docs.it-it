---
title: Convertire un tipo anonimo in tupla
description: Informazioni su come usare il menu azioni rapide e refactoring per convertire un tipo anonimo in una tupla in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6486b771207722c64993d5a880894fe07beb99c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907662"
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

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
