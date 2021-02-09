---
title: Istruzione Invert if
description: Informazioni su come usare il menu azioni rapide e refactoring per invertire un'istruzione if o if else senza modificare il significato del codice.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cf4ad7c25030e4a331ee67f4957ddac59afdd966
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852232"
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

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
