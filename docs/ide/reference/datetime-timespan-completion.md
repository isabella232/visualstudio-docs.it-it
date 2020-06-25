---
title: Completamento di DateTime e TimeSpan tramite il menu IntelliSense
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: eaa8a344e46c031b37b52106ba9aef25dac59b0c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290338"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>Completamento di DateTime e TimeSpan tramite il menu IntelliSense

Questo refactoring si applica a:

- C#

**Cosa:** Terminazione del valore letterale stringa DateTime e TimeSpan tramite il menu IntelliSense.

**Quando:** Si desidera scrivere valori letterali stringa DateTime e TimeSpan. IntelliSense fornisce il completamento di base e una spiegazione del significato di ogni carattere. 

**Motivo:** Ricordare i formati DateTime è un disco rigido e IntelliSense può aiutarti a scriverlo.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nel valore letterale stringa DateTime o TimeSpan.
2. Premere **CTRL +** + **barra spaziatrice** per attivare il menu **IntelliSense** .
3. Selezionare il carattere che si desidera aggiungere.

   ![IntelliSense completamento DateTime](media/datetime-completion.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
