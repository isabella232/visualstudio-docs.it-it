---
title: Effettuare il refactoring del codice per convertire una query LINQ in un'istruzione foreach
description: Convertire qualsiasi query LINQ scritta nella sintassi di query in istruzione foreach.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6e1b24cb8406ff29659eb79d1d9fa856db628b89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094083"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refactoring per convertire LINQ in un'istruzione foreach

Usare questo refactoring per convertire la [sintassi di query LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) in un'istruzione [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Questo refactoring si applica a:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Come usarlo

1. Selezionare l'intera query LINQ a partire da `from`.

   > [!NOTE]
   > Questo refactoring può essere usato solo per convertire query LINQ espresse con la sintassi di query e non con la sintassi dei metodi.

1. Premere **CTRL**+**.** oppure fare clic sull'icona a forma di cacciavite ![icona cacciavite](../media/screwdriver-icon.png) nel margine del file di codice.

   ![Menu delle azioni rapide per convertire LINQ in foreach](media/convert-linq-to-foreach.png)

1. Selezionare **Converti in foreach**. In alternativa, selezionare **Anteprima modifiche** per aprire la finestra di dialogo [Anteprima modifiche](../../ide/preview-changes.md) e quindi selezionare **Applica**.

> [!NOTE]
> Per C#, il codice generato da questi refactoring usa un tipo esplicito o [var](/dotnet/csharp/language-reference/keywords/var) per la variabile di iterazione del ciclo `foreach`. Il tipo nel codice generato, esplicito o implicito, dipende dalle impostazioni di stile del codice che rientrano nell'ambito. Queste particolari impostazioni di stile del codice vengono configurate a livello di computer in **Strumenti** > **Opzioni** > Editor di testo Per**Code Style** > **General** > **l'editor** > **di codice** > generale**\'var**o a livello di soluzione in un file [EditorConfig.](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) Se si modifica un'impostazione di stile del codice in **Opzioni**, riaprire il file di codice per rendere effettive le modifiche.

## <a name="see-also"></a>Vedere anche

- [LINQ](/dotnet/standard/using-linq)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima delle modifiche](../../ide/preview-changes.md)
