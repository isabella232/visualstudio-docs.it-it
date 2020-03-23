---
title: Rendere il membro statico
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77515302"
---
# <a name="make-member-static"></a>Rendere il membro statico

Questo refactoring si applica a:

- C#

**Cosa:** Rendere statico un membro.

**Quando:** Si desidera che un membro non statico sia statico.

**Perché:** I membri statici migliorano la leggibilità: sapere che il codice specifico è isolato rende più facile da comprendere, rileggere e riutilizzare. 

## <a name="how-to"></a>Procedure

1. Posizionare il punto di inserimento sul nome del membro.

2. Premere **CTRL**+**.** (periodo) per attivare il menu **Azioni rapide e refactoring.**

   ![Rendere il membro statico](media/make-member-static.png)

3. Selezionare **Imposta come statici**.

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
