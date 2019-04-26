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
ms.openlocfilehash: 0ce1b620a6d8aba7e4aea767745891dff6d9f869
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790048"
---
# <a name="generate-usings-in-visual-studio"></a>Generare istruzioni using in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** Consente di aggiungere immediatamente le importazioni necessarie o le [istruzioni using](/dotnet/csharp/language-reference/keywords/using-statement) per il codice copiato e incollato.

**Quando:** È pratica comune copiare codice da posizioni diverse nel progetto o in altre origini e incollarlo nel codice nuovo. Questa azione rapida consente di trovare le istruzioni imports mancanti per il codice copiato e incollato e quindi ne richiede l'aggiunta.

**Perché?:** Dato che l'azione rapida aggiunge automaticamente le importazioni necessarie, non è necessario copiare manualmente le istruzioni `using` necessarie per il codice.

## <a name="generate-usings-refactoring"></a>Refactoring per la generazione di istruzioni using

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
- [Suggerimenti per gli sviluppatori di .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
