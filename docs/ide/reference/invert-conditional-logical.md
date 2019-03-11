---
title: Inversione di espressioni condizionali e operazioni logiche
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a35f5949bee6cb3c4fbcbf9ba6a9b501d54b2014
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324586"
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
- [Suggerimenti per gli sviluppatori di .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
