---
title: Convertire una funzione locale in un metodo
description: Informazioni su come usare il menu Azioni rapide e refactoring per convertire una funzione locale in un metodo.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 32808364220cea253d0cc085115bd58de11bedb768e3583dacab833474dd1581
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121430154"
---
# <a name="convert-a-local-function-to-a-method"></a>Convertire una funzione locale in un metodo

Questo refactoring si applica a:

- C#

**Cosa:** Convertire una funzione locale in un metodo.

**Quando:** Si dispone di una funzione locale che si vuole definire al di fuori del contesto locale corrente.

**Perché:** Si vuole convertire una funzione locale in un metodo in modo da poterla chiamare all'esterno del contesto locale. Oppure potrebbe essere necessario eseguire la conversione in un metodo quando la funzione locale è troppo lunga. Quando si definisce la funzione in un metodo separato, il codice è più facile da leggere.

## <a name="convert-local-function-to-method-refactoring"></a>Refactoring con conversione della funzione locale in metodo

1. Posizionare il cursore nella funzione locale.

    ![Esempio di codice di conversione della funzione locale in metodo](media/convert-local-function-to-method.png)

2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

    ![Esempio di correzione del codice di conversione della funzione locale in metodo](media/convert-local-function-to-method-codefix.png)

2. Premere INVIO per accettare il refactoring.

    ![Esempio di risultato della conversione della funzione locale in metodo](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
