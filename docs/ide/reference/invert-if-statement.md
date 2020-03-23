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
ms.openlocfilehash: a0419100cbc5fcd543eb250fa85cbfe2ebd1c97f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531593"
---
# <a name="invert-if-statement"></a>Istruzione Invert if

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Consente di `if` invertire `if else` un'istruzione o senza modificare il significato del codice.

**Quando:** Quando si `if` dispone `if else` di un'affermazione o che sarebbe meglio capito quando invertito.

**Perché:** L'inversione manuale di un'istruzione `if` o `if else` può richiedere molto più tempo ed eventualmente introdurre errori. Questa correzione del codice consente di eseguire automaticamente questo refactoring.

## <a name="invert-if-statement-refactoring"></a>Refactoring dell'istruzione Invert if

1. Posizionare il cursore in un'istruzione `if` o `if else`.

    ![Invert if else](media/invert-if.png)

2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

    ![Correzione del codice Invert if else](media/invert-if-codefix.png)

3. Selezionare **Invert if**.

    ![Risultato di Invert if else](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
