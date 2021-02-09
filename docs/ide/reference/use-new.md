---
title: Utilizza nuovo()
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a129e94f6009eec51995b6a4e170f0a804e6407f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889811"
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
