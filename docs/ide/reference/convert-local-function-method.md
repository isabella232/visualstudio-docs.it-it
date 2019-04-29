---
title: Convertire una funzione locale in un metodo
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a580077528c87e62f81e840ed6dee76ff1eac57f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968283"
---
# <a name="convert-a-local-function-to-a-method"></a>Convertire una funzione locale in un metodo

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** convertire una funzione locale in un metodo.

**Quando:** si ha una funzione locale che si vuole definire al di fuori del contesto locale corrente.

**Perché?:** potrebbe essere necessario convertire una funzione locale in un metodo per poterla chiamare al di fuori del contesto locale. Oppure potrebbe essere necessario eseguire la conversione in un metodo quando la funzione locale è troppo lunga. Quando si definisce la funzione in un metodo separato, il codice è più facile da leggere.

## <a name="convert-local-function-to-method-refactoring"></a>Refactoring con conversione della funzione locale in metodo

1. Posizionare il cursore nella funzione locale.

    ![Esempio di codice di conversione della funzione locale in metodo](media/convert-local-function-to-method.png)

2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

    ![Esempio di correzione del codice di conversione della funzione locale in metodo](media/convert-local-function-to-method-codefix.png)

2. Premere INVIO per accettare il refactoring.

    ![Esempio di risultato della conversione della funzione locale in metodo](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
