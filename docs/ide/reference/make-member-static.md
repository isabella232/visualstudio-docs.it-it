---
title: Rendi statico il membro
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1ecc66cb58ad11bd431acb341dae0493ce8192da
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515302"
---
# <a name="make-member-static"></a>Rendi statico il membro

Questo refactoring si applica a:

- C#

**Cosa:** Rendere statico un membro.

**Quando:** Si vuole che un membro non statico sia statico.

**Motivo:** I membri statici migliorano la leggibilità: sapere che il codice specifico è isolato rende più semplice comprendere, rileggere e riutilizzare. 

## <a name="how-to"></a>Procedura

1. Posizionare il punto di inserimento sul nome del membro.

2. Premere **CTRL**+ **.** (periodo) per attivare il menu **azioni rapide e refactoring** .

   ![Rendi statico il membro](media/make-member-static.png)

3. Selezionare **Imposta come statici**.

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
