---
title: Convertire un tipo anonimo in classe
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f29e31fb87d8b18e7f5a46d16f90217ee08d51f6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154582"
---
# <a name="convert-anonymous-type-to-class"></a>Convertire un tipo anonimo in classe

Questo refactoring si applica a:

- C#

**Cosa:** convertire un tipo anonimo in classe.

**Quando:** si ha un tipo anonimo che si vuole continuare a usare come base in una classe.

**Perché?:** i tipi anonimi sono utili se si usano solo localmente. Con l'aumento del codice, è utile avere la possibilità di promuoverli facilmente in una classe.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore in un tipo anonimo.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

   ![Convertire un tipo anonimo in classe](media/convert-anon-to-class.png)

2. Premere **INVIO** per accettare il refactoring.

   ![Conversione del tipo anonimo in classe accettata](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
