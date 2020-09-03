---
title: Estrai funzione locale
description: Trasformare un frammento di codice nel metodo corrispondente selezionando il codice e immettendo CTRL+R, CTRL+M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 031fbe22ec61837d489df7a6af923ef0cd2454c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77515330"
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

    ![Estrai funzione locale](media/extract-local-function.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
