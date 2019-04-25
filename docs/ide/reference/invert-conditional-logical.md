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
ms.openlocfilehash: 7d59b61cff622a9ba305ebfa86f7c0ebe3c00fe3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422220"
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
