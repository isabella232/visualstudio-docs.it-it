---
title: Metodo inline
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0cc619ea61a7fd4d7f4bc542b946e298933a8f73
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402301"
---
# <a name="inline-method"></a>Metodo inline

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Refactoring del metodo inline. 

**Quando:** Si desidera sostituire gli utilizzi di un metodo statico, di istanza e di estensione all'interno di un singolo corpo dell'istruzione con un'opzione per rimuovere la dichiarazione del metodo originale.

**Motivo:**  Questo refactoring fornirà una sintassi più chiara.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore sull'utilizzo del metodo.

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare una delle opzioni seguenti: 
    
   Selezionare **Inline `<QualifiedMethodName>`** (NomeMetodo inline) per rimuovere la dichiarazione del metodo inline: 

    ![Crea classe astratta](media/inline-method-remove-declaration.png)

   Selezionare **Inline and keep `<QualifiedMethodName>`** (NomeMetodo inline e mantieni) per mantenere la dichiarazione del metodo originale: 

    ![Crea classe astratta](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
