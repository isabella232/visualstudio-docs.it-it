---
title: Inversione di espressioni condizionali e operazioni logiche
description: Informazioni su come usare il menu Azioni rapide e refactoring per invertire un'espressione condizionale o un operatore AND/OR condizionale.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6d42cbd379550d8abb739aafacca5698f164048f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151509"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Invertire le espressioni condizionali e gli operatori AND/OR condizionali

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Consente di invertire un'espressione condizionale o un operatore AND/OR condizionale.

**Quando:** Si dispone di un'espressione condizionale o di un operatore AND/OR condizionale che sarebbe meglio compreso se invertito.

**Perché:** L'inversione manuale di un'espressione o di un operatore AND/OR condizionale può richiedere molto più tempo ed eventualmente introdurre errori. Questa correzione del codice consente di eseguire automaticamente questo refactoring.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Refactoring con inversione delle espressioni condizionali e degli operatori AND/OR condizionali

1. Posizionare il cursore in un'espressione condizionale o in un operatore AND/OR condizionale.
2. Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Invert conditional** (Inverti condizionale) o **Replace '&&' with '||'** (Sostituisci '&&' con '||')

    ![Screenshot dell'opzione condizionale Inverti.](media/invert-conditional.png)

    ![Screenshot della finestra di dialogo && con || Opzione.](media/invert-logical-operator.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
