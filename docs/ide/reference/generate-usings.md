---
title: Generare direttive using
description: Informazioni su come usare il menu Azioni rapide e refactoring per aggiungere immediatamente le direttive imports o using necessarie per il codice copiato e incollato.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: b3eaa7d035c95ba3ff2eeccf37968cb858ddcf02
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711647"
---
# <a name="add-missing-usings-in-visual-studio"></a>Aggiungere istruzioni using mancanti in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** Consente di aggiungere immediatamente le direttive imports [o using necessarie](/dotnet/csharp/language-reference/keywords/using-directive) per il codice copiato e incollato.

**Quando:** È pratica comune copiare il codice da posizioni diverse nel progetto o in altre origini e incollarlo nel nuovo codice. Questa azione rapida trova le direttive imports mancanti per il codice copiato e incollato e quindi richiede di aggiungerle. Questa correzione del codice può anche aggiungere riferimenti da un progetto all'altro.

**Perché:** Poiché l'azione rapida aggiunge automaticamente le importazioni necessarie, non è necessario copiare manualmente `using` le direttive necessarie per il codice.

## <a name="add-missing-usings-refactoring"></a>Refactoring per l'aggiunta di istruzioni using mancanti

1. Copiare il codice da un file e incollarlo in uno nuovo senza includere `using` le direttive necessarie. L'errore risultante è accompagnato da una correzione del codice che aggiunge le `using` direttive mancanti.

    > [!NOTE]
    > È necessario abilitare questo suggerimento in **Strumenti > Opzioni > Editor di testo > C# > Avanzate > Direttive using**.

2. Selezionare CTRL+. per aprire il menu **Azioni rapide e refactoring**.

    ![Generare direttive using](media/generate-using-codefix.png)

3. Selezionare **utilizzando \<your reference\> ;** per aggiungere il riferimento mancante.

    ![Risultato della generazione di istruzioni using](media/generate-using-result.png)

## <a name="see-also"></a>Vedi anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
- [Suggerimenti per sviluppatori .NET](../csharp-developer-productivity.md)
