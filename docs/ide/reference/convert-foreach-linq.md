---
title: Convertire un ciclo foreach in LINQ
description: Converte qualsiasi ciclo foreach che utilizza IEnumerable in una query LINQ o un modulo di chiamata LINQ (noto anche come metodo LINQ).
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ff489e11cc5c61c5e840b4b12d05ba5da46ce41
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466290"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Convertire un ciclo foreach in LINQ

Questo refactoring si applica a:

- C#

**Cosa:** Consente di convertire facilmente il ciclo *foreach* che usa IEnumerable in una query LINQ o un modulo di chiamata LINQ (noto anche come metodo LINQ).

**Quando:** Si dispone di un ciclo foreach che utilizza IEnumerable e si desidera che il ciclo legga come query LINQ.

**Motivo:** Si preferisce utilizzare la sintassi LINQ anziché un ciclo foreach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) fa di una query un costrutto di linguaggio di prima classe in C#. LINQ può ridurre la quantità di codice in un file, rende il codice più semplice da leggere e consente l'uso di modelli di espressione di query simili in origini dati diverse.

> [!NOTE]
> La sintassi LINQ è in genere meno efficiente rispetto a un ciclo foreach. Considerare il compromesso in termini di prestazioni in caso di uso di LINQ per migliorare la leggibilità del codice.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Refactoring per convertire un ciclo foreach in LINQ

1. Posizionare il cursore nella parola chiave `foreach`.

    ![Esempio di foreach con IEnumerable](media/convert-foreach-to-LINQ.png)

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

   ![Esempio di menu Converti in LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Selezionare **Converti in LINQ** o **Converti in LINQ (form di chiamata)**.

   ![Esempio di risultato della query LINQ](media/convert-foreach-to-LINQ-result.png)

   ![Esempio di risultato del form di chiamata LINQ](media/convert-foreach-to-LINQ-callform-result.png)

### <a name="sample-code"></a>Codice di esempio

```csharp
using System.Collections.Generic;

public class Class1
{
    public void MyMethod()
    {
        var greetings = new List<string>()
            { "hi", "yo", "hello", "howdy" };

        IEnumerable<string> enumerable()
        {
            foreach (var greet in greetings)
            {
                if (greet.Length < 3)
                {
                    yield return greet;
                }
            }

            yield break;
        }
    }
}
```

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Finestra Anteprima modifiche](../../ide/preview-changes.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
