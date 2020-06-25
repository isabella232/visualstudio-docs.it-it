---
title: Generare operatori IEquatable per gli struct
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ccc5be9debbdc2b4901d4aad15a0dc4d2bf1bb9f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290331"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Genera operatori IEquatable durante la generazione di Equals per gli struct

Questa generazione di codice si applica a:

- C#

**Cosa:** Consente di generare gli operatori **Equals** e **IEquatable** per gli [struct](https://docs.microsoft.com/dotnet/csharp/language-reference/builtin-types/struct).

**Quando:** Si dispone di uno struct che verrà automaticamente aggiunto anche a IEquatable e agli operatori Equals e not Equals.

**Perché**

- se si implementa un tipo valore, è consigliabile valutare la possibilità di eseguire l'override del metodo **Equals** per ottenere migliori prestazioni rispetto all'implementazione predefinita del metodo Equals su ValueType.

- Implementa interfaccia IEquatable implementa un metodo Equals () specifico del tipo.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore in un punto qualsiasi nella riga della dichiarazione dello struct.

2. Eseguire quindi una delle operazioni seguenti:

   - Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

   - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.

   - Fare clic su ![cacciavite](../media/screwdriver-icon.png) che viene visualizzato nel margine sinistro.

   ![Genera IEquatable e Equals per gli struct](media/generate-equals-structs.png)

3. Selezionare **genera Equals (oggetto)** dal menu a discesa.

## <a name="see-also"></a>Vedi anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
