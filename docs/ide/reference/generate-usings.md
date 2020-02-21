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
ms.openlocfilehash: f3b3435e10d6bb9a71fd16b9286759b136c167f4
ms.sourcegitcommit: ea5e02720d71185f8e27fbea205024371b0c7ceb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77544550"
---
# <a name="add-missing-usings-in-visual-studio"></a>Aggiungere istruzioni using mancanti in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** Consente di aggiungere immediatamente le [direttive](/dotnet/csharp/language-reference/keywords/using-directive) Import o using necessarie per il codice di copia e incolla.

**Quando:** È pratica comune copiare il codice da diverse posizioni nel progetto o in altre origini e incollarlo in un nuovo codice. Questa azione rapida trova le direttive Import mancanti per il codice di copia e incolla e quindi richiede di aggiungerle. Questa correzione del codice può anche aggiungere riferimenti da progetto a progetto.

**Motivo:** Poiché l'azione rapida aggiunge automaticamente le importazioni necessarie, non è necessario copiare manualmente le direttive `using` richieste dal codice.

## <a name="add-missing-usings-refactoring"></a>Refactoring per l'aggiunta di istruzioni using mancanti

1. Copiare il codice da un file e incollarlo in uno nuovo senza includere le direttive `using` necessarie. L'errore risultante è accompagnato da una correzione del codice che aggiunge le direttive `using` mancanti.

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
