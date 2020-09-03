---
title: Semplificare l'interpolazione di stringhe
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
ms.openlocfilehash: a8b0fd53164cb98921b111d49fa04a76c9d0d8a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094307"
---
# <a name="simplify-string-interpolation-refactoring"></a>Semplificazione del refactoring dell'interpolazione di stringhe

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di semplificare un' [interpolazione di stringhe](https://docs.microsoft.com/dotnet/csharp/tutorials/string-interpolation).

**Quando:** Si dispone di un'interpolazione di stringhe che può essere semplificata.

**Motivo:** La semplificazione di un'interpolazione di stringhe può fornire maggiore chiarezza e sintassi concisa. Questo strumento di refactoring eseguirà automaticamente l'attività invece di eseguirla manualmente.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore sull'interpolazione di stringhe:

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare **semplifica l'interpolazione**

    ![Semplificare l'interpolazione di stringhe](media/simplify-string-interpolation.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)