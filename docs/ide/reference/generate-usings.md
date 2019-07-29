---
title: Generare istruzioni using
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: d971bcdaca4efdf587c7e441f1b0b28d21388dee
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416473"
---
# <a name="add-missing-usings-in-visual-studio"></a>Aggiungere istruzioni using mancanti in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** Consente di aggiungere immediatamente le importazioni necessarie o le [istruzioni using](/dotnet/csharp/language-reference/keywords/using-statement) per il codice copiato e incollato.

**Quando:** È pratica comune copiare codice da posizioni diverse nel progetto o in altre origini e incollarlo nel codice nuovo. Questa azione rapida consente di trovare le istruzioni imports mancanti per il codice copiato e incollato e quindi ne richiede l'aggiunta.

**Perché?:** Dato che l'azione rapida aggiunge automaticamente le importazioni necessarie, non è necessario copiare manualmente le istruzioni `using` necessarie per il codice.

## <a name="add-missing-usings-refactoring"></a>Refactoring per l'aggiunta di istruzioni using mancanti

1. Copiare codice da un file e incollarlo in un nuovo file senza includere le istruzioni `using` necessarie. L'errore risultante è accompagnato da una correzione del codice che aggiunge le istruzioni `using` mancanti.

    > [!NOTE]
    > È necessario abilitare questo suggerimento in **Strumenti > Opzioni > Editor di testo > C# > Avanzate > Direttive using**.

2. Selezionare CTRL+. per aprire il menu **Azioni rapide e refactoring**.

    ![Generare istruzioni using](media/generate-using-codefix.png)

3. Selezionare **con \<riferimento\>;** per aggiungere il riferimento mancante.

    ![Risultato della generazione di istruzioni using](media/generate-using-result.png)

## <a name="see-also"></a>Vedere anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
