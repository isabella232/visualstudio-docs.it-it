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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789067"
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
