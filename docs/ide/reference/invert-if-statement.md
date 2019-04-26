---
title: Istruzione Invert if
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
ms.openlocfilehash: 5a809eee1eb5460e245f64156385f759870adbd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970262"
---
# <a name="invert-if-statement"></a>Istruzione Invert if

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** consente di invertire un'istruzione `if` o `if else` senza modificare il significato del codice.

**Quando:** quando si ha un'istruzione `if` o `if else` che potrebbe essere più chiara se invertita.

**Perché?:** l'inversione manuale di un'istruzione `if` o `if else` può richiedere molto più tempo e introdurre errori. Questa correzione del codice consente di eseguire automaticamente questo refactoring.

## <a name="invert-if-statement-refactoring"></a>Refactoring dell'istruzione Invert if

1. Posizionare il cursore in un'istruzione `if` o `if else`.

    ![Invert if else](media/invert-if.png)

2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

    ![Correzione del codice Invert if else](media/invert-if-codefix.png)

3. Selezionare **Invert if**.

    ![Risultato di Invert if else](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
