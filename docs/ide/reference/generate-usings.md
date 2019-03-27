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
ms.openlocfilehash: afd4b758332d9357dc20dd84e726d72da4d2db74
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355185"
---
# <a name="generate-usings-in-visual-studio"></a>Generare istruzioni using in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** Consente di aggiungere immediatamente le importazioni necessarie o le [istruzioni using](/dotnet/csharp/language-reference/keywords/using-statement) di codice copiato e incollato.

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
