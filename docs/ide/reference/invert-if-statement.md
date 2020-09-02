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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531593"
---
# <a name="invert-if-statement"></a>Istruzione Invert if

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Consente di invertire `if` un' `if else` istruzione o senza modificare il significato del codice.

**Quando:** Quando si dispone di `if` un' `if else` istruzione o che verrebbe riconosciuta meglio quando invertita.

**Motivo:** L'inversione `if` `if else` Manuale di un'istruzione o può richiedere molto più tempo ed eventualmente introdurre errori. Questa correzione del codice consente di eseguire automaticamente questo refactoring.

## <a name="invert-if-statement-refactoring"></a>Refactoring dell'istruzione Invert if

1. Posizionare il cursore in un'istruzione `if` o `if else`.

    ![Invert if else](media/invert-if.png)

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

    ![Correzione del codice Invert if else](media/invert-if-codefix.png)

3. Selezionare **Invert if**.

    ![Risultato di Invert if else](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
