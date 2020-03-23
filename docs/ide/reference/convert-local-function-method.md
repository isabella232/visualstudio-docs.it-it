---
title: Convertire una funzione locale in un metodo
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3572682fe68d9b0b1bc4adee537de5cd056a8906
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "71301689"
---
# <a name="convert-a-local-function-to-a-method"></a>Convertire una funzione locale in un metodo

Questo refactoring si applica a:

- C#

**Cosa:** Convertire una funzione locale in un metodo.

**Quando:** Si dispone di una funzione locale che si desidera definire all'esterno del contesto locale corrente.

**Perché:** Si desidera convertire una funzione locale in un metodo in modo che sia possibile chiamarla all'esterno del contesto locale. Oppure potrebbe essere necessario eseguire la conversione in un metodo quando la funzione locale è troppo lunga. Quando si definisce la funzione in un metodo separato, il codice è più facile da leggere.

## <a name="convert-local-function-to-method-refactoring"></a>Refactoring con conversione della funzione locale in metodo

1. Posizionare il cursore nella funzione locale.

    ![Esempio di codice di conversione della funzione locale in metodo](media/convert-local-function-to-method.png)

2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

    ![Esempio di correzione del codice di conversione della funzione locale in metodo](media/convert-local-function-to-method-codefix.png)

2. Premere INVIO per accettare il refactoring.

    ![Esempio di risultato della conversione della funzione locale in metodo](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
