---
title: Eseguire la conversione tra valori letterali stringa regolari e verbatim
description: Informazioni su come usare il menu Azioni rapide e refactoring per eseguire la conversione tra valori letterali stringa regolari e verbatim.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ad19096bf01fa53463ec28939ef4ea7f5cdafb5d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151691"
---
# <a name="convert-between-regular-string-and-verbatim-string-literals-refactoring"></a>Eseguire la conversione tra valori letterali stringa regolari e valori letterali stringa verbatim refactoring

Questo refactoring si applica a:

- C#

**Cosa:** Consente di eseguire la conversione tra valori letterali stringa regolari e valori letterali stringa verbatim.

**Quando:** Si vuole risparmiare spazio o fornire maggiore chiarezza nel codice.

**Perché:** La conversione di un valore letterale stringa verbatim in un valore letterale stringa normale consente di risparmiare spazio. La conversione di un valore letterale stringa regolare in un valore letterale stringa verbatim può offrire maggiore chiarezza.

## <a name="how-to"></a>Procedure

1. Posizionare il punto di caret sulla stringa regolare o sul valore letterale stringa verbatim:

2. Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare una delle opzioni seguenti:

    Selezionare **Converti in stringa normale**.

    ![Eseguire la conversione in una stringa normale](media/convert-to-regular-string.png)

    Selezionare **Converti in stringa verbatim**.

    ![Convertire in una stringa verbatim](media/convert-to-verbatim-string.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)