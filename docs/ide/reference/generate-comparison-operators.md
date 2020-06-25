---
title: Genera operatori di confronto per i tipi che implementano IComparable
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 31e33b562a5a11ff77c1d610fbce9e90506b036d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290337"
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

   - Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

   - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.

   - Fare clic su ![cacciavite](../media/screwdriver-icon.png) che viene visualizzato nel margine sinistro.

   ![Generare gli operatori di confronto](media/generate-comparison-operators.png)

3. Selezionare **genera Equals (oggetto)** dal menu a discesa.

## <a name="see-also"></a>Vedi anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
