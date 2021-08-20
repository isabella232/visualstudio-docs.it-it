---
title: Generare operatori IEquatable per gli struct
description: Informazioni su come usare il menu Azioni rapide e refactoring per generare operatori Equals e IEquatable per gli struct.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 1a95d7c890d651dcddb90f1eafd431830e621cd9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151574"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Generare operatori IEquatable durante la generazione di equals per gli struct

Questa generazione di codice si applica a:

- C#

**Cosa:** Consente di generare **operatori Equals** **e IEquatable** per [gli struct](/dotnet/csharp/language-reference/builtin-types/struct).

**Quando:** Si dispone di uno struct che aggiungerà automaticamente gli operatori IEquatable e equals e not equals.

**Perché:**

- se si implementa un tipo valore, è consigliabile valutare la possibilità di eseguire l'override del metodo **Equals** per ottenere migliori prestazioni rispetto all'implementazione predefinita del metodo Equals su ValueType.

- Implementa l'interfaccia IEquatable implementa un metodo Equals() specifico del tipo.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore in un punto qualsiasi della riga della dichiarazione dello struct.

2. Eseguire quindi una delle operazioni seguenti:

   - Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring**.

   - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.

   - Fare clic sull'icona ![cacciavite](../media/screwdriver-icon.png) che viene visualizzato nel margine sinistro.

   ![Generare IEquatable e Equals per gli struct](media/generate-equals-structs.png)

3. Selezionare **Genera equals(oggetto)** dal menu a discesa.

## <a name="see-also"></a>Vedi anche

- [Generazione del codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)