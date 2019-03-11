---
title: Convertire la funzione locale in metodo
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 55c82aa896de5c3f3bf18468a1da98253a3def74
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324676"
---
# <a name="convert-local-function-to-method"></a>Convertire la funzione locale in metodo

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Convertire una funzione locale in un metodo

**Quando:** si ha una funzione locale che si vuole definire al di fuori del contesto locale corrente.

**Perché?:** potrebbe essere necessario convertire una funzione locale in un metodo per poterla chiamare al di fuori del contesto locale. È possibile eseguire la conversione in un metodo quando la funzione locale è troppo lunga. Definendola in un metodo separato, il codice è più facile da leggere.

## <a name="convert-local-function-to-method-refactoring"></a>Refactoring con conversione della funzione locale in metodo

1. Posizionare il cursore in una funzione locale.

    ![Convertire la funzione locale in metodo](media/convert-local-function-to-method.png)

2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

    ![Correzione del codice di conversione della funzione locale in metodo](media/convert-local-function-to-method-codefix.png)

2. Premere **INVIO** per accettare il refactoring.

    ![Risultato della conversione della funzione locale in metodo](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
