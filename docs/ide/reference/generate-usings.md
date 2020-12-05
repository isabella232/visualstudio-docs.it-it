---
title: Generare direttive using
description: Informazioni su come usare il menu azioni rapide e refactoring per aggiungere immediatamente le direttive import o using necessarie per il codice copiato e incollato.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 38996d1cda52dfe98b6ce9cf24e5adcca6a8b069
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617162"
---
# <a name="add-missing-usings-in-visual-studio"></a>Aggiungere istruzioni using mancanti in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** Consente di aggiungere immediatamente le [direttive](/dotnet/csharp/language-reference/keywords/using-directive) Import o using necessarie per il codice di copia e incolla.

**Quando:** È pratica comune copiare il codice da diverse posizioni nel progetto o in altre origini e incollarlo in un nuovo codice. Questa azione rapida trova le direttive Import mancanti per il codice di copia e incolla e quindi richiede di aggiungerle. Questa correzione del codice può anche aggiungere riferimenti da progetto a progetto.

**Motivo:** Poiché l'azione rapida aggiunge automaticamente le importazioni necessarie, non è necessario copiare manualmente le `using` direttive necessarie per il codice.

## <a name="add-missing-usings-refactoring"></a>Refactoring per l'aggiunta di istruzioni using mancanti

1. Copiare il codice da un file e incollarlo in uno nuovo senza includere le `using` direttive necessarie. L'errore risultante è accompagnato da una correzione del codice che aggiunge le `using` direttive mancanti.

    > [!NOTE]
    > È necessario abilitare questo suggerimento in **Strumenti > Opzioni > Editor di testo > C# > Avanzate > Direttive using**.

2. Selezionare CTRL+. per aprire il menu **Azioni rapide e refactoring**.

    ![Generare direttive using](media/generate-using-codefix.png)

3. Selezionare **using \<your reference\> ;** per aggiungere il riferimento mancante.

    ![Risultato della generazione di istruzioni using](media/generate-using-result.png)

## <a name="see-also"></a>Vedere anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
- [Suggerimenti per gli sviluppatori .NET](../csharp-developer-productivity.md)
