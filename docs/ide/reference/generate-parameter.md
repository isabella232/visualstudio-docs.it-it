---
title: Generare un parametro - Refactoring
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
ms.openlocfilehash: 372a3f705e5e85c0edb31a754105f61056402b9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094346"
---
# <a name="generate-parameter"></a>Generare un parametro

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Genera automaticamente un parametro del metodo.

**Quando:** Si fa riferimento a una variabile in un metodo che non esiste nel contesto corrente e si riceve un errore. è possibile generare un parametro come correzione del codice. 

**Motivo:** È possibile modificare rapidamente una firma del metodo senza perdere il contesto.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nel nome della variabile e premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
1. Selezionare **Generate parameter** (Genera parametro).

   ![Generare un parametro](media/generate-parameter.png) 

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
