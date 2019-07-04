---
title: Generare un parametro - Refactoring
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e95e76c35afdb8cdbe38c8b33329734ba68361b1
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329090"
---
# <a name="generate-parameter"></a>Generare un parametro

Questo refactoring si applica a:

- C#

**Cosa:** genera automaticamente il parametro di un metodo.

**Quando:** si fa riferimento a una variabile in un metodo che non esiste nel contesto corrente e viene restituito un errore. È possibile generare un parametro come correzione del codice. 

**Perché?:** è possibile modificare rapidamente la firma di un metodo senza perdere il contesto.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore nel nome della variabile e premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.
1. Selezionare **Generate parameter** (Genera parametro).

   ![Generare un parametro](media/generate-parameter.png) 

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
