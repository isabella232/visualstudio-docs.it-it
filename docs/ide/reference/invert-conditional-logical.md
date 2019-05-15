---
title: Inversione di espressioni condizionali e operazioni logiche
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
ms.openlocfilehash: 3931ae53fc29b0ffd8b8b6e96951a0f4786ff756
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531684"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Invertire le espressioni condizionali e gli operatori AND/OR condizionali

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** consente di invertire un'espressione condizionale o un operatore AND/OR condizionale.

**Quando:** si ha un'espressione condizionale o un operatore AND/OR condizionale che potrebbe essere più chiaro se invertito.

**Perché?:** l'inversione manuale di un'espressione o di un operatore AND/OR condizionale può richiedere molto più tempo e può introdurre errori. Questa correzione del codice consente di eseguire automaticamente questo refactoring.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Refactoring con inversione delle espressioni condizionali e degli operatori AND/OR condizionali

1. Posizionare il cursore in un'espressione condizionale o in un operatore AND/OR condizionale.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Invert conditional** (Inverti condizionale) o **Replace '&&' with '||'** (Sostituisci '&&' con '||')

    ![Invertire l'elemento condizionale](media/invert-conditional.png)

    ![Invertire l'elemento condizionale](media/invert-logical-operator.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
