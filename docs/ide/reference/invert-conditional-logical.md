---
title: Inversione di espressioni condizionali e operazioni logiche
description: Informazioni su come usare il menu azioni rapide e refactoring per invertire un'espressione condizionale o un operatore AND/OR condizionale.
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
ms.openlocfilehash: 0bd75a40f52a6148a6c50b212183bb8dc7a52d56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852245"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Invertire le espressioni condizionali e gli operatori AND/OR condizionali

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Consente di invertire un'espressione condizionale o un operatore AND/OR condizionale.

**Quando:** Si dispone di un'espressione condizionale o di un operatore condizionale e/o che verrebbe meglio riconosciuta se invertita.

**Motivo:** L'inversione a mano di un'espressione o di un operatore condizionale e/o può richiedere molto più tempo ed eventualmente introdurre errori. Questa correzione del codice consente di eseguire automaticamente questo refactoring.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Refactoring con inversione delle espressioni condizionali e degli operatori AND/OR condizionali

1. Posizionare il cursore in un'espressione condizionale o in un operatore AND/OR condizionale.
2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Invert conditional** (Inverti condizionale) o **Replace '&&' with '||'** (Sostituisci '&&' con '||')

    ![Screenshot dell'opzione Inverti condizionale.](media/invert-conditional.png)

    ![Screenshot del && di sostituzione con | | opzione.](media/invert-logical-operator.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
