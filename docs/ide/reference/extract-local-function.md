---
title: Estrai funzione locale
description: Trasformare un frammento di codice nella propria funzione selezionando il codice e digitando CTRL + R, CTRL + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 80ac8f23b5404d70b70166915cd791f2c0d7ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860971"
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

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
