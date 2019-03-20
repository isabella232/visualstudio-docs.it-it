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
ms.openlocfilehash: 9c17d5c9d6874c836954941e1fccd8ce9d9f2e3a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149263"
---
# <a name="wrap-indent-and-align-parameters"></a>Impostare il ritorno a capo automatico, il rientro e l'allineamento dei parametri

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di impostare il ritorno a capo automatico, il rientro e l'allineamento dei parametri.

**Quando:** si ha una dichiarazione o chiamata al metodo con molteplici parametri.

**Perché?:** la lettura di un lungo elenco di parametri è più semplice quando è stato impostato il ritorno a capo automatico o il rientro in base alle preferenze dell'utente.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore nell'elenco di parametri.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

   ![Impostare il ritorno a capo automatico, il rientro e l'allineamento dei parametri](media/wrap-parameters.png)

3. Premere **INVIO** per accettare il refactoring.

   ![Ritorno a capo automatico, rientro e allineamento dei parametri applicato](media/wrap-parameters-completed.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
