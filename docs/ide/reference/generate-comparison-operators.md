---
title: Generare operatori di confronto per IComparable
ms.custom: SEO-VS-2020
description: Per migliorare le prestazioni, generare operatori di confronto per i tipi che implementano IComparable.
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 289562b1aebe981b0829a1adac107a607163a859
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102597"
---
# <a name="generate-comparison-operators-for-types-that-implement-icomparable"></a>Genera operatori di confronto per i tipi che implementano IComparable

Questa generazione di codice si applica a:

- C#

**Cosa:** Consente di generare operatori di **confronto** per i tipi che implementano IComparable.

**Quando:** Si dispone di un tipo che implementa IComparable. gli operatori di confronto verranno aggiunti automaticamente.

**Motivo:** Se si implementa un tipo valore, è consigliabile eseguire l'override del metodo **Equals** per ottenere prestazioni più elevate rispetto all'implementazione predefinita del metodo Equals su ValueType.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore all'interno della classe o nella parola chiave IComparable.

2. Eseguire quindi una delle operazioni seguenti:

   - Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring** .

   - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring** .

   - Fare clic sull'icona ![cacciavite](../media/screwdriver-icon.png) che viene visualizzato nel margine sinistro.

   ![Generare gli operatori di confronto](media/generate-comparison-operators.png)

3. Selezionare **genera Equals (oggetto)** dal menu a discesa.

## <a name="see-also"></a>Vedere anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
