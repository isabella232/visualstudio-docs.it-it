---
title: Utilizza nuovo()
description: Informazioni su come usare `new()` quando non è possibile usare `var` .
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2c1455d92501ee50bca84e655b83ca98435e2d47
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061875"
---
# <a name="use-new"></a>Utilizzare `new()`.

Si applica a:

- C#

**Cosa:** Usare `new()` .

**Quando:** Si dispone di un campo che non può usare `var` o di una preferenza di stile del codice per non usare `var` .

**Perché:** Non è quindi necessario scrivere codice ripetitivo ripetendo il tipo due volte.

## <a name="how-to"></a>Procedure

1. Posizionare il punto di caret sulla dichiarazione di campo.

2. Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare **Usa 'new(...)'**:

    ![Usare 'new(...)'](media/use-new.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
