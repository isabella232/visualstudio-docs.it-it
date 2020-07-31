---
title: Completamento di DateTime e TimeSpan tramite il menu IntelliSense
ms.date: 07/31/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 36b6d5440e532653845638f87f7f1d7066af6ba3
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471554"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>Completamento di DateTime e TimeSpan tramite il menu IntelliSense

Questo refactoring si applica a:

- C#

**Cosa:** Valore letterale stringa DateTime e TimeSpan e completamento stringa di formato tramite il menu IntelliSense.

**Quando:** Si desidera scrivere un valore letterale stringa DateTime e TimeSpan e una stringa di formato. IntelliSense fornisce il completamento di base e una spiegazione del significato di ogni carattere. 

**Motivo:** Ricordare i formati DateTime è un disco rigido e IntelliSense può aiutarti a scriverlo.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nella stringa di formato DateTime o TimeSpan.
2. Premere **CTRL +** + **barra spaziatrice** per attivare il menu **IntelliSense** .
3. Selezionare il carattere che si desidera aggiungere.

   ![IntelliSense completamento DateTime](media/datetime-completion.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
