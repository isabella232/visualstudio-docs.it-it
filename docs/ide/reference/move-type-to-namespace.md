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
monikerRange: vs-2019
ms.openlocfilehash: 58d2757fa8798b67c8e597f5f82bc65a279f4a90
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80375563"
---
# <a name="move-type-to-namespace"></a>Spostare un tipo in uno spazio dei nomi

Questo refactoring si applica a:

- C#

**Cosa:** Spostare il tipo nello spazio dei nomi.

**Quando:** Si desidera spostare un tipo in uno spazio dei nomi o in una cartella diversa. 

**Motivo:** Si vuole effettuare il refactoring di parti della soluzione e avere un modo rapido per spostare un tipo in uno spazio dei nomi o in una cartella diversa. 

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nel nome della classe.
2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Move to namespace** (Sposta in spazio dei nomi).

   ![Spostare in uno spazio dei nomi - Refactoring](media/move-to-namespace.png)

4. Nella finestra di dialogo visualizzata selezionare lo spazio dei nomi di destinazione in cui si vuole spostare il tipo. 

   ![Finestra di dialogo per la selezione di uno spazio dei nomi](media/select-target-namespace.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
