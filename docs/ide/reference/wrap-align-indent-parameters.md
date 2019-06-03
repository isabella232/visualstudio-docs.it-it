---
title: Impostare il ritorno a capo automatico, il rientro e l'allineamento dei parametri
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ccdf29e3a4cda2bf5d527a2b712878c1fbd76197
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/22/2019
ms.locfileid: "66037589"
---
# <a name="wrap-indent-and-align-parameters-or-arguments"></a>Ritorno a capo automatico, rientro e allineamento dei parametri o degli argomenti

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di impostare il ritorno a capo automatico, il rientro e l'allineamento dei parametri o degli argomenti.

**Quando:** si ha una dichiarazione o chiamata di metodo con molteplici parametri o argomenti.

**Perché?:** la lettura di un lungo elenco di parametri o argomenti è più semplice quando viene impostato il ritorno a capo automatico o il rientro in base alle preferenze dell'utente.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore nell'elenco di parametri.
2. Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.

   ![Impostare il ritorno a capo automatico, il rientro e l'allineamento dei parametri](media/wrap-parameters.png)

3. Premere **INVIO** per accettare il refactoring.

   ![Ritorno a capo automatico, rientro e allineamento dei parametri applicato](media/wrap-parameters-completed.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
