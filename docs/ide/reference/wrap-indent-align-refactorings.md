---
title: Impostare il ritorno a capo automatico, il rientro e l'allineamento dei refactoring
description: Informazioni su come impostare il ritorno a capo e l'allineamento delle catene di chiamate di metodi.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 54e0fccbc4ff1994b6c7c1e3469232eaf7a64ece75e575d203a8d6e845afccc7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121371808"
---
# <a name="wrap-indent-and-align-refactorings"></a>Impostare il ritorno a capo automatico, il rientro e l'allineamento dei refactoring

## <a name="wrap-and-align-call-chains"></a>Ritorno a capo e allineamento delle catene di chiamate

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di eseguire il wrapping e l'allineamento di catene di chiamate al metodo.

**Quando:** Si dispone di una catena lunga costituita da diverse chiamate al metodo in un'unica istruzione.

**Perché:** La lettura di un elenco lungo è più semplice quando viene eseguito il wrapping o il rientro in base alle preferenze dell'utente.

### <a name="how-to"></a>Procedure

1. Posizionare il cursore in qualsiasi catena di chiamate.
2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Esegui il wrapping della catena di chiamate** o **Esegui il wrapping e allinea la catena di chiamate** per accettare il refactoring.

   ![Screeenshot del menu Azioni rapide e refactoring in Visual Studio con la catena di chiamate Warap selezionata e le modifiche al codice C# visualizzate.](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Ritorno a capo automatico, rientro e allineamento dei parametri o degli argomenti

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di eseguire il wrapping, il rientro e l'allineamento di parametri o argomenti.

**Quando:** Si dispone di una dichiarazione di metodo o di una chiamata con più parametri o argomenti.

**Perché:** La lettura di un lungo elenco di parametri o argomenti è più semplice quando ne viene eseguito il wrapping o il rientro in base alle preferenze dell'utente.

### <a name="how-to"></a>Procedure

1. Posizionare il cursore nell'elenco di parametri.
2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

   ![Impostare il ritorno a capo automatico, il rientro e l'allineamento dei parametri](media/wrap-parameters.png)

3. Selezionare **Wrap every parameter (Esegue** il wrapping di ogni parametro) per accettare il refactoring.

## <a name="wrap-binary-expressions"></a>Wrapping delle espressioni binarie

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di eseguire il wrapping di espressioni binarie.

**Quando:** Si dispone di un'espressione binaria.

**Perché:** La lettura di un'espressione binaria è più semplice quando viene eseguito il wrapping in base alle preferenze dell'utente.

### <a name="how-to"></a>Procedure

1. Posizionare il cursore nell'espressione binaria.
2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Wrap expression (Espressione di** wrapping) per accettare il refactoring.

   ![Screeenshot del menu Azioni rapide e refactoring in Visual Studio con l'espressione Warap selezionata e le modifiche al codice C# visualizzate.](media/wrap-binary-expression.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
