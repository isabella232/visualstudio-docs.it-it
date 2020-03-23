---
title: Spostare un tipo in uno spazio dei nomi
ms.date: 06/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 821e915a0b66f25c5b89a83b31e93b01aea6f400
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "67292695"
---
# <a name="move-type-to-namespace"></a>Spostare un tipo in uno spazio dei nomi

Questo refactoring si applica a:

- C#

**Cosa:** Spostare il tipo nello spazio dei nomi.

**Quando:** Si desidera spostare un tipo in uno spazio dei nomi o in una cartella diversa. 

**Perché:** Si desidera eseguire il refactoring di parti della soluzione e disporre di un modo rapido per spostare un tipo in uno spazio dei nomi o in una cartella diversa. 

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nel nome della classe.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Move to namespace** (Sposta in spazio dei nomi).

   ![Spostare in uno spazio dei nomi - Refactoring](media/move-to-namespace.png)

4. Nella finestra di dialogo visualizzata selezionare lo spazio dei nomi di destinazione in cui si vuole spostare il tipo. 

   ![Finestra di dialogo per la selezione di uno spazio dei nomi](media/select-target-namespace.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
