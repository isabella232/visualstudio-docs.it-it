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
ms.openlocfilehash: f59dceabb076ebce36755c41caa6de00258be883
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160641"
---
# <a name="generate-usings-in-visual-studio"></a>Generare istruzioni using in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** **Cosa:** Consente di aggiungere immediatamente le importazioni necessarie o le [istruzioni using](/dotnet/csharp/language-reference/keywords/using-statement) di codice copiato e incollato.

**Quando:** È pratica comune copiare e incollare codice da posizioni diverse nel progetto o in altre origini di codice. Questa azione rapida analizza le importazioni mancanti per il codice copiato e incollato e quindi ne richiede l'aggiunta.

**Perché?:** Aggiungendo automaticamente le importazioni necessarie, l'utente non dovrà copiare manualmente le istruzioni `using` necessarie.

## <a name="generate-usings-refactoring"></a>Refactoring per la generazione di istruzioni using

1. Copiare e incollare codice da un file diverso senza includere le istruzioni `using` necessarie. L'errore è ora accompagnato da una correzione del codice che aggiunge le istruzioni `using` mancanti.

    > [!NOTE] 
    > Questo suggerimento deve essere attivato in **Strumenti > Opzioni > Editor di testo > C# > Avanzate > Direttive using**.

2. Premere **CTRL**+**.** per aprire il menu **Azioni rapide e refactoring**. 

    ![Generare istruzioni using](media/generate-using-codefix.png)

3. Selezionare **con \<riferimento\>;** per aggiungere il riferimento mancante.

    ![Risultato della generazione di istruzioni using](media/generate-using-result.png)

## <a name="see-also"></a>Vedere anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
- [Suggerimenti per gli sviluppatori di .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)