---
title: Generare operatori IEquatable per gli struct
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5ee695169f52036858fc70598f81f375638ab03f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808116"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Genera operatori IEquatable durante la generazione di Equals per gli struct

Questa generazione di codice si applica a:

- C#

**Cosa:** Consente di generare gli operatori **Equals** e **IEquatable** per gli [struct](/dotnet/csharp/language-reference/builtin-types/struct).

**Quando:** Si dispone di uno struct che verrà automaticamente aggiunto anche a IEquatable e agli operatori Equals e not Equals.

**Perché**

- se si implementa un tipo valore, è consigliabile valutare la possibilità di eseguire l'override del metodo **Equals** per ottenere migliori prestazioni rispetto all'implementazione predefinita del metodo Equals su ValueType.

- Implementa interfaccia IEquatable implementa un metodo Equals () specifico del tipo.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore in un punto qualsiasi nella riga della dichiarazione dello struct.

2. Eseguire quindi una delle operazioni seguenti:

   - Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

   - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.

   - Fare clic sull'icona ![cacciavite](../media/screwdriver-icon.png) che viene visualizzato nel margine sinistro.

   ![Genera IEquatable e Equals per gli struct](media/generate-equals-structs.png)

3. Selezionare **genera Equals (oggetto)** dal menu a discesa.

## <a name="see-also"></a>Vedere anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)