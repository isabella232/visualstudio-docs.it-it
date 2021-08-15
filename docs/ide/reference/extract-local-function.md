---
title: Estrai funzione locale
description: Trasformare un frammento di codice in una funzione propria selezionando il codice e digitando CTRL+R, CTRL+M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 7ee115eea0342d1e8ce2c34beed7ce1cfadc98d00ea431a1f0a28fc32aee7bdf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121258928"
---
# <a name="extract-local-function-refactoring"></a>Refactoring di estrazione di funzioni locali

Questo refactoring si applica a:

- C#

**Cosa:** Consente di trasformare un frammento di codice da un metodo esistente in una funzione locale.

**Quando:** In un metodo è presente un frammento di codice esistente che deve essere chiamato da una funzione locale.

**Perché:** è possibile copiare e incollare il codice, ma ciò potrebbe causare la duplicazione. Una soluzione migliore consiste nel eseguire il refactoring di tale frammento nella propria funzione locale.

## <a name="how-to"></a>Procedure

1. Evidenziare il codice da estrarre.

2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**. 

3. Selezionare **Estrai funzione locale**.

    ![Screenshot della finestra Visual Studio codice con una riga evidenziata. Il menu Azioni rapide e refactoring è aperto ed è selezionata l'opzione Estrai funzione locale.](media/extract-local-function.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
