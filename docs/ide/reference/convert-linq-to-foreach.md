---
title: Effettuare il refactoring del codice per convertire una query LINQ in un'istruzione foreach
ms.date: 05/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e3e4e448931e028c53d62c534e2785e4f026a7ec
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refactoring per convertire LINQ in un'istruzione foreach

Usare questo refactoring per convertire la [sintassi di query LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) in un'istruzione [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Questo refactoring si applica a:

- C#

## <a name="how-to-use-it"></a>Come usare la funzionalità

1. Selezionare l'intera query LINQ a partire da `from`.

   > [!NOTE]
   > Questo refactoring può essere usato solo per convertire query LINQ espresse con la sintassi di query e non con la sintassi dei metodi.

1. Premere **CTRL**+**.** oppure fare clic sull'icona a forma di cacciavite ![icona cacciavite](../media/screwdriver-icon.png) nel margine del file di codice.

   ![Menu delle azioni rapide per convertire LINQ in foreach](media/convert-linq-to-foreach.png)

1. Selezionare **Converti in foreach**. In alternativa, selezionare **Anteprima modifiche** per aprire la finestra di dialogo [Anteprima modifiche](../../ide/preview-changes.md) e quindi selezionare **Applica**.

> [!NOTE]
> Per C#, il codice generato da questi refactoring usa un tipo esplicito o [var](/dotnet/csharp/language-reference/keywords/var) per la variabile di iterazione del ciclo `foreach`. Il tipo nel codice generato, esplicito o implicito, dipende dalle impostazioni di stile del codice che rientrano nell'ambito. Queste particolari impostazioni di stile del codice vengono configurate a livello di computer in **Strumenti** > **Opzioni** > **Editor di testo**  >  **C#** > **Stile del codice** > **Generale** > **Preferenze \'var'** oppure a livello di soluzione in un file [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types). Se si modifica un'impostazione di stile del codice in **Opzioni**, riaprire il file di codice per rendere effettive le modifiche.

## <a name="see-also"></a>Vedere anche

- [LINQ](/dotnet/standard/using-linq)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)