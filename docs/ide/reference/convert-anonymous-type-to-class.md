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
monikerRange: '>= vs-2019'
ms.openlocfilehash: 251a011695f6f5056e1fdf8e1a6be36b898b66f5
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809211"
---
# <a name="convert-anonymous-type-to-class"></a>Conversione di tipi anonimi in classe

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Converte un tipo anonimo in classe.

**Quando:** Si dispone di un tipo anonimo che si vuole continuare a compilare in una classe.

**Motivo:** I tipi anonimi sono utili se vengono utilizzati solo localmente. Con l'aumento del codice, è utile avere la possibilità di promuoverli facilmente in una classe.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore in un tipo anonimo.
2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

   ![Convertire un tipo anonimo in classe](media/convert-anon-to-class.png)

2. Premere **invio** per accettare il refactoring.

   ![Conversione del tipo anonimo in classe accettata](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
