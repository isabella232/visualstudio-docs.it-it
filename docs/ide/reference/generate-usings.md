---
title: Generare direttive using
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 903b160bac0e8096062e09fd78ff4c92c46cf8ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094314"
---
# <a name="add-missing-usings-in-visual-studio"></a>Aggiungere istruzioni using mancanti in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** Consente di aggiungere immediatamente le importazioni necessarie o [di utilizzare direttive](/dotnet/csharp/language-reference/keywords/using-directive) per il codice copia e incollato.

**Quando:** È pratica comune copiare il codice da posizioni diverse nel progetto o in altre origini e incollarlo nel nuovo codice. Questa azione rapida trova le direttive imports mancanti per il codice copia e incollato e quindi richiede di aggiungerle. Questa correzione del codice può anche aggiungere riferimenti da progetto a progetto.

**Perché:** Poiché l'azione rapida aggiunge automaticamente le importazioni necessarie, `using` non è necessario copiare manualmente le direttive necessarie per il codice.

## <a name="add-missing-usings-refactoring"></a>Refactoring per l'aggiunta di istruzioni using mancanti

1. Copiare il codice da un file e incollarlo in uno nuovo senza includere le direttive necessarie. `using` L'errore risultante è accompagnato da una `using` correzione del codice che aggiunge le direttive mancanti.

    > [!NOTE]
    > È necessario abilitare questo suggerimento in **Strumenti > Opzioni > Editor di testo > C# > Avanzate > Direttive using**.

2. Selezionare CTRL+. per aprire il menu **Azioni rapide e refactoring**.

    ![Generare direttive using](media/generate-using-codefix.png)

3. Selezionare **con \<riferimento\>;** per aggiungere il riferimento mancante.

    ![Risultato della generazione di istruzioni using](media/generate-using-result.png)

## <a name="see-also"></a>Vedere anche

- [Generazione del codice](../code-generation-in-visual-studio.md)
- [Anteprima delle modifiche](../../ide/preview-changes.md)
- [Suggerimenti per gli sviluppatori .NETTips for .NET developers](../csharp-developer-productivity.md)
