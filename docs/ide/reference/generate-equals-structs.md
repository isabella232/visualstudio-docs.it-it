---
title: Generare operatori IEquatable per gli struct
description: Informazioni su come usare il menu azioni rapide e refactoring per generare gli operatori Equals e IEquatable per gli struct.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 05792636e1094c53869f0235145aec73b26deea9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952980"
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

## <a name="see-also"></a>Vedi anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)