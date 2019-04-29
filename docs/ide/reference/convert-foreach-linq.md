---
title: Convertire un ciclo foreach in LINQ
ms.date: 02/20/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f0b9685ce6d4cf8ee6d4253c79759508cf43915e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968482"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Convertire un ciclo foreach in LINQ

Questo refactoring si applica a:

- C#

**Cosa:** consente di convertire facilmente il ciclo *foreach* che usa un elemento IEnumerable in una query LINQ o un form di chiamata LINQ (anche noto come metodo LINQ).

**Quando:** si ha un ciclo foreach che usa un elemento IEnumerable e si vuole che tale ciclo venga letto come query LINQ.

**Perché?:** si preferisce usare la sintassi LINQ anziché un ciclo foreach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) fa di una query un costrutto di linguaggio di prima classe in C#. LINQ può ridurre la quantità di codice in un file, rende il codice più semplice da leggere e consente l'uso di modelli di espressione di query simili in origini dati diverse.

> [!NOTE]
> La sintassi LINQ è in genere meno efficiente rispetto a un ciclo foreach. Considerare il compromesso in termini di prestazioni in caso di uso di LINQ per migliorare la leggibilità del codice.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Refactoring per convertire un ciclo foreach in LINQ

1. Posizionare il cursore nella parola chiave `foreach`.

    ![Esempio di foreach con IEnumerable](media/convert-foreach-to-LINQ.png)

2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

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

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Finestra Anteprima modifiche](../../ide/preview-changes.md)
- [Suggerimenti per gli sviluppatori di .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
