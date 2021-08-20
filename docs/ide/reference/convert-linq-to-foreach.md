---
title: Convertire una query LINQ in un'istruzione foreach
ms.custom: SEO-VS-2020
description: Eseguire il refactoring del codice per convertire qualsiasi query LINQ scritta nella sintassi di query in un'istruzione foreach.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6ef812f37ec4d13d2270ebf7e5471ec82d9efbe4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144067"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refactoring per convertire LINQ in un'istruzione foreach

Usare questo refactoring per convertire la [sintassi di query LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) in un'istruzione [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Questo refactoring si applica a:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Modo d'uso

1. Selezionare l'intera query LINQ a partire da `from`.

   > [!NOTE]
   > Questo refactoring può essere usato solo per convertire query LINQ espresse con la sintassi di query e non con la sintassi dei metodi.

1. Premere  + **CTRL.** oppure fare clic sull'icona a forma di cacciavite ![icona cacciavite](../media/screwdriver-icon.png) nel margine del file di codice.

   ![Menu delle azioni rapide per convertire LINQ in foreach](media/convert-linq-to-foreach.png)

1. Selezionare **Converti in foreach**. In alternativa, selezionare **Anteprima modifiche** per aprire la finestra di dialogo [Anteprima modifiche](../../ide/preview-changes.md) e quindi selezionare **Applica**.

> [!NOTE]
> Per C#, il codice generato da questi refactoring usa un tipo esplicito o [var](/dotnet/csharp/language-reference/keywords/var) per la variabile di iterazione del ciclo `foreach`. Il tipo nel codice generato, esplicito o implicito, dipende dalle impostazioni di stile del codice che rientrano nell'ambito. Queste particolari impostazioni di stile del codice vengono configurate a livello di computer in Strumenti Opzioni Editor di testo  >    >    >  **C#** Code  >  **Style**  >  **General**  >  **\' var' preferences** [](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types) o a livello di soluzione in un file EditorConfig. Se si modifica un'impostazione di stile del codice in **Opzioni**, riaprire il file di codice per rendere effettive le modifiche.

## <a name="see-also"></a>Vedi anche

- [LINQ](/dotnet/standard/using-linq)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
