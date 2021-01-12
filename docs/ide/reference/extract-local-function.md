---
title: Estrai funzione locale
description: Trasformare un frammento di codice nella propria funzione selezionando il codice e digitando CTRL + R, CTRL + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e007246b85671a0f4606bbdb3d1e9c4e0dc83541
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129458"
---
# <a name="extract-local-function-refactoring"></a>Refactoring Estrai funzione locale

Questo refactoring si applica a:

- C#

**Cosa:** Consente di trasformare un frammento di codice da un metodo esistente in una funzione locale.

**Quando:** Si dispone di un frammento di codice esistente in un metodo che deve essere chiamato da una funzione locale.

**Perché:** è possibile copiare e incollare il codice, ma ciò potrebbe causare la duplicazione. Una soluzione migliore consiste nel effettuare il refactoring del frammento nella propria funzione locale.

## <a name="how-to"></a>Procedure

1. Evidenziare il codice da estrarre.

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**. 

3. Selezionare **Estrai funzione locale**.

    ![Screenshot della finestra di Visual Studio Code con una riga evidenziata. Il menu azioni rapide e refactoring è aperto ed Estrai funzione locale è selezionata.](media/extract-local-function.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
