---
title: Utilizza nuovo()
description: Informazioni su come usare `new()` quando non è possibile usare `var` .
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 889be18ab342f515bf5add266088a7ee69c087c1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218074"
---
# <a name="use-new"></a>Utilizzare `new()`.

Si applica a:

- C#

**Cosa:** Usare `new()` .

**Quando:** È presente un campo che non può usare `var` o una preferenza di stile del codice da non usare `var` .

**Motivo:** Quindi, non è necessario scrivere codice ripetitivo ripetendo il tipo due volte.

## <a name="how-to"></a>Procedure

1. Posizionare il punto di inserimento nella dichiarazione di campo.

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare **USA ' nuovo (...)'**:

    ![USA ' nuovo (...)'](media/use-new.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
