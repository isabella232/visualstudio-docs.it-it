---
title: Refactoring a capo, rientro e allineamento
description: Informazioni su come impostare il ritorno a capo e l'allineamento delle catene di chiamate di metodi.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 349f2eeccfea4fea03967929b01114c0de1af155
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527668"
---
# <a name="wrap-indent-and-align-refactorings"></a>Refactoring a capo, rientro e allineamento

## <a name="wrap-and-align-call-chains"></a>Wrapping e allineamento delle catene di chiamate

Questo refactoring si applica a:

- C#

**Cosa:** Consente di eseguire il wrapping e allineare le catene di chiamate al metodo.

**Quando:** Si dispone di una catena estesa costituita da diverse chiamate al metodo in un'unica istruzione.

**Motivo:** La lettura di un lungo elenco è più semplice quando ne viene eseguito il wrapped o il rientro in base alle preferenze dell'utente.

### <a name="how-to"></a>Procedura

1. Posizionare il cursore in qualsiasi catena di chiamate.
2. Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Esegui il wrapping della catena di chiamate** o **Esegui il wrapping e allinea la catena di chiamate** per accettare il refactoring.

   ![Ritorno a capo e allineamento delle catene di chiamate](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Ritorno a capo automatico, rientro e allineamento dei parametri o degli argomenti

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di incapsulare, rientrare e allineare parametri o argomenti.

**Quando:** Si dispone di una dichiarazione di metodo o di una chiamata con più parametri o argomenti.

**Motivo:** La lettura di un lungo elenco di parametri o argomenti è più semplice quando ne viene eseguito il wrapped o il rientro in base alle preferenze dell'utente.

### <a name="how-to"></a>Procedura

1. Posizionare il cursore nell'elenco di parametri.
2. Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.

   ![Impostare il ritorno a capo automatico, il rientro e l'allineamento dei parametri](media/wrap-parameters.png)

3. Selezionare **Wrap ogni parametro** per accettare il refactoring.

## <a name="wrap-binary-expressions"></a>Wrapping delle espressioni binarie

Questo refactoring si applica a:

- C#

**Cosa:** Consente di eseguire il wrapping di espressioni binarie.

**Quando:** Si dispone di un'espressione binaria.

**Motivo:** La lettura di un'espressione binaria è più semplice quando viene sottoposta a incapsulamento in preferenza utente

### <a name="how-to"></a>Procedura

1. Posizionare il cursore nell'espressione binaria.
2. Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **espressione a capo** per accettare il refactoring.

   ![Ritorno a capo e allineamento delle catene di chiamate](media/wrap-binary-expression.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
