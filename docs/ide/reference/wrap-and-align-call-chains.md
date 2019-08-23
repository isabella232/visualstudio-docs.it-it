---
title: Ritorno a capo e allineamento delle catene di chiamate
description: Informazioni su come impostare il ritorno a capo e l'allineamento delle catene di chiamate di metodi.
ms.date: 08/13/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2a5b6bea4c915e029ca3ae448444decce0d7b041
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69620013"
---
# <a name="wrap-and-align-call-chains"></a>Ritorno a capo e allineamento delle catene di chiamate

Questo refactoring si applica a:

- C#

**Cosa:** consente di impostare il ritorno a capo e l'allineamento delle catene di chiamate di metodi.

**Quando:** è presente una lunga catena costituita da diverse chiamate di metodi in un'unica istruzione.

**Perché?:** la lettura di un lungo elenco è più semplice quando viene impostato il ritorno a capo o il rientro in base alle preferenze dell'utente.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore in qualsiasi catena di chiamate.
2. Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Esegui il wrapping della catena di chiamate** o **Esegui il wrapping e allinea la catena di chiamate** per accettare il refactoring.

   ![Ritorno a capo e allineamento delle catene di chiamate](media/wrap-call-chain.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
