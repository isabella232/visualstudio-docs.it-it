---
title: Convertire un tipo anonimo in classe
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
ms.openlocfilehash: 2379ce588eeb4773e562f630ade37e28d7f17315
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094286"
---
# <a name="convert-anonymous-type-to-class"></a>Conversione di tipi anonimi in classe

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Convertire un tipo anonimo in classe.

**Quando:** Si dispone di un tipo anonimo che si desidera continuare a compilare su in una classe.

**Perché:** I tipi anonimi sono utili se vengono usati solo localmente. Con l'aumento del codice, è utile avere la possibilità di promuoverli facilmente in una classe.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore in un tipo anonimo.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

   ![Convertire un tipo anonimo in classe](media/convert-anon-to-class.png)

2. Premere **INVIO** per accettare il refactoring.

   ![Conversione del tipo anonimo in classe accettata](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
