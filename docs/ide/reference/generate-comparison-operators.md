---
title: Generare operatori di confronto per IComparable
ms.custom: SEO-VS-2020
description: Per migliorare le prestazioni, generare operatori di confronto per i tipi che implementano IComparable.
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: b0a2c2e532258594834d73c091314451f8b2cd3f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117358"
---
# <a name="generate-comparison-operators-for-types-that-implement-icomparable"></a>Generare operatori di confronto per tipi che implementano IComparable

Questa generazione di codice si applica a:

- C#

**Cosa:** Consente di generare operatori **di** confronto per i tipi che implementano IComparable.

**Quando:** Si dispone di un tipo che implementa IComparable e verranno aggiunti automaticamente gli operatori di confronto.

**Perché:** Se si implementa un tipo valore, è consigliabile eseguire l'override del metodo **Equals** per migliorare le prestazioni rispetto all'implementazione predefinita del metodo Equals in ValueType.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore all'interno della classe o sulla parola chiave IComparable.

2. Eseguire quindi una delle operazioni seguenti:

   - Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

   - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.

   - Fare clic sull'icona ![cacciavite](../media/screwdriver-icon.png) che viene visualizzato nel margine sinistro.

   ![Generare gli operatori di confronto](media/generate-comparison-operators.png)

3. Selezionare **Generate Equals(object) (Genera equals(oggetto)** dal menu a discesa.

## <a name="see-also"></a>Vedi anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
