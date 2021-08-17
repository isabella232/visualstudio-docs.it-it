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
ms.openlocfilehash: 951bc8fa65991daaad2661744efd6bcbd17bdcd4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056069"
---
# <a name="wrap-indent-and-align-refactorings"></a>Impostare il ritorno a capo automatico, il rientro e l'allineamento dei refactoring

## <a name="wrap-and-align-call-chains"></a>Ritorno a capo e allineamento delle catene di chiamate

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di eseguire il wrapping e allineare le catene di chiamate al metodo.

**Quando:** Si dispone di una lunga catena costituita da diverse chiamate al metodo in un'unica istruzione.

**Perché:** La lettura di un lungo elenco è più semplice quando viene eseguito il wrapping o il rientro in base alle preferenze dell'utente.

### <a name="how-to"></a>Procedure

1. Posizionare il cursore in qualsiasi catena di chiamate.
2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Esegui il wrapping della catena di chiamate** o **Esegui il wrapping e allinea la catena di chiamate** per accettare il refactoring.

   ![Immagine del menu Azioni rapide e refactoring in Visual Studio con la catena di chiamate Warap selezionata e le modifiche al codice C# visualizzate.](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Ritorno a capo automatico, rientro e allineamento dei parametri o degli argomenti

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Consente di eseguire il wrapping, impostare un rientro e allineare parametri o argomenti.

**Quando:** Si dispone di una dichiarazione di metodo o di una chiamata con più parametri o argomenti.

**Perché:** La lettura di un lungo elenco di parametri o argomenti è più semplice quando viene eseguito il wrapping o il rientro in base alle preferenze dell'utente.

### <a name="how-to"></a>Procedure

1. Posizionare il cursore nell'elenco di parametri.
2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

   ![Impostare il ritorno a capo automatico, il rientro e l'allineamento dei parametri](media/wrap-parameters.png)

3. Selezionare **Wrap every parameter (Eseguire** il wrapping di ogni parametro) per accettare il refactoring.

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
3. Selezionare **Wrap expression (Incapsula** espressione) per accettare il refactoring.

   ![Immagine del menu Azioni rapide e refactoring in Visual Studio con l'espressione Warap selezionata e le modifiche al codice C# visualizzate.](media/wrap-binary-expression.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
