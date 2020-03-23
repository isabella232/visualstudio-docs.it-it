---
title: Impostare il ritorno a capo automatico, il rientro e l'allineamento dei refactoring
description: Informazioni su come impostare il ritorno a capo e l'allineamento delle catene di chiamate di metodi.
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
ms.openlocfilehash: d801f052cb02e6a5b53189eeae342b9015d30f9b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093880"
---
# <a name="wrap-indent-and-align-refactorings"></a>Impostare il ritorno a capo automatico, il rientro e l'allineamento dei refactoring

## <a name="wrap-and-align-call-chains"></a>Ritorno a capo e allineamento delle catene di chiamate

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di eseguire il wrapping e allineare le catene delle chiamate al metodo.

**Quando:** Si dispone di una catena lunga costituita da diverse chiamate al metodo in un'istruzione.

**Perché:** La lettura di un lungo elenco è più semplice quando viene eseguito il wrapping o il rientro in base alle preferenze dell'utente.

### <a name="how-to"></a>Procedure

1. Posizionare il cursore in qualsiasi catena di chiamate.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Esegui il wrapping della catena di chiamate** o **Esegui il wrapping e allinea la catena di chiamate** per accettare il refactoring.

   ![Ritorno a capo e allineamento delle catene di chiamate](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Ritorno a capo automatico, rientro e allineamento dei parametri o degli argomenti

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di eseguire il wrapping, il rientro e l'allineamento di parametri o argomenti.

**Quando:** Si dispone di una dichiarazione di metodo o una chiamata che dispone di più parametri o argomenti.

**Perché:** La lettura di un lungo elenco di parametri o argomenti è più semplice quando vengono incapsulati o rientrati in base alle preferenze dell'utente.

### <a name="how-to"></a>Procedure

1. Posizionare il cursore nell'elenco di parametri.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

   ![Impostare il ritorno a capo automatico, il rientro e l'allineamento dei parametri](media/wrap-parameters.png)

3. Selezionare **Avvolgi ogni parametro** per accettare il refactoring.

## <a name="wrap-binary-expressions"></a>Wrapping delle espressioni binarie

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di eseguire il wrapping delle espressioni binarie.

**Quando:** Si dispone di un'espressione binaria.

**Perché:** La lettura di un'espressione binaria è più semplice quando viene eseguito il wrapping in base alle preferenze dell'utente.

### <a name="how-to"></a>Procedure

1. Posizionare il cursore nell'espressione binaria.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Espressione di ritorno** a capo per accettare il refactoring.

   ![Ritorno a capo e allineamento delle catene di chiamate](media/wrap-binary-expression.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
