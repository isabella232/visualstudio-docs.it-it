---
title: Semplificare l'espressione condizionale
description: Informazioni su come usare il menu Azioni rapide e refactoring per semplificare un'espressione condizionale.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 3784e6ac94440c433220432cd0b14c45254e8f14
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056212"
---
# <a name="simplify-conditional-expression-refactoring"></a>Semplificare il refactoring delle espressioni condizionali

Questo refactoring si applica a:

- C#

**Cosa:** Consente di semplificare [un'espressione condizionale](/dotnet/csharp/language-reference/operators/conditional-operator).

**Quando:** Si vuole rimuovere il codice non necessario per ottenere maggiore chiarezza.

**Perché:** La semplificazione di un'espressione condizionale può offrire maggiore chiarezza e sintassi concisa. Questo strumento di refactoring eseguirà l'attività automaticamente invece di doverla eseguire manualmente.

## <a name="how-to"></a>Procedure

1. Posizionare il punto di caret sull'espressione condizionale:

2. Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare **Semplifica espressione condizionale**

    ![Semplificare l'espressione condizionale](media/simplify-conditional-expression.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)