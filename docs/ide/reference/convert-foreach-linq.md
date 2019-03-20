---
title: Convertire il ciclo foreach in LINQ
ms.date: 02/20/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: eadad8fdbec990607450b374a32758547194f734
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160274"
---
# <a name="convert-foreach-loop-to-linq"></a>Convertire il ciclo foreach in LINQ

Questo refactoring si applica a:

- C#

**Cosa:** consente di convertire facilmente i cicli foreach usando elementi IEnumerable in query LINQ o modulo di chiamata LINQ (anche noto come metodo LINQ).

**Quando:** in presenza di un ciclo foreach in cui viene usato un elemento IEnumerable che si preferisce leggere come query LINQ.

**Perché?:** in alcuni casi può essere preferibile per gli utenti usare la sintassi LINQ piuttosto che un ciclo foreach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) fa di una query un costrutto di linguaggio di prima classe in C#. LINQ può ridurre la quantità di codice in un file per una più facile lettura e consente l'uso di modelli di espressione di query simili in origini dati diverse.

> [!NOTE]
> La sintassi LINQ offre in genere prestazioni inferiori rispetto ai cicli foreach. È importante essere consapevoli dei compromessi in termini di prestazioni che può essere necessario accettare se si vuole migliorare la leggibilità del codice con LINQ.

## <a name="convert-foreach-loop-to-linq-refactoring"></a>Refactoring per convertire il ciclo foreach in LINQ

1. Posizionare il cursore nella parola chiave `foreach`.

    ![Foreach con IEnumerable](media/convert-foreach-to-LINQ.png)

2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

   ![Menu Convert to LINQ (Converti in LINQ)](media/convert-foreach-to-LINQ-codefix.png)

3. Selezionare **Convert to LINQ** (Converti in LINQ) o **Convert to Linq (call form)** (Converti in Linq (modulo di chiamata))

   ![Risultato della query LINQ](media/convert-foreach-to-LINQ-result.png)
   
   ![Risultato del modulo di chiamata LINQ](media/convert-foreach-to-LINQ-callform-result.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
- [Suggerimenti per gli sviluppatori di .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)