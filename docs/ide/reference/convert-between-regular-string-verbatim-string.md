---
title: Eseguire la conversione tra valori letterali stringa normali e Verbatim
description: Informazioni su come usare il menu azioni rapide e refactoring per eseguire la conversione tra stringhe regolari e valori letterali stringa Verbatim.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1c335c90183e4c5c97b1a2737a2edd8a1b86fb77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918331"
---
# <a name="convert-between-regular-string-and-verbatim-string-literals-refactoring"></a>Refactoring tra stringhe regolari e valori letterali stringa Verbatim

Questo refactoring si applica a:

- C#

**Cosa:** Consente di eseguire la conversione tra stringhe regolari e valori letterali stringa Verbatim.

**Quando:** Si vuole risparmiare spazio o fornire maggiore chiarezza nel codice.

**Motivo:** La conversione di un valore letterale stringa verbatim in un valore letterale stringa normale può contribuire a risparmiare spazio. La conversione di un valore letterale stringa normale in un valore letterale stringa Verbatim può fornire maggiore chiarezza.

## <a name="how-to"></a>Procedure

1. Posizionare il punto di inserimento sulla stringa normale o sul valore letterale stringa Verbatim:

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare una delle opzioni seguenti:

    Selezionare **Converti in stringa normale**.

    ![Converti in stringa regolare](media/convert-to-regular-string.png)

    Selezionare **Converti in stringa verbatim**.

    ![Converti in stringa Verbatim](media/convert-to-verbatim-string.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)