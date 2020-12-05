---
title: Istruzione Invert if
description: Informazioni su come usare il menu azioni rapide e refactoring per invertire un'istruzione if o if else senza modificare il significato del codice.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 71b3a11e053b6a600d0b33db7c52a91c4950bf5b
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616980"
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
