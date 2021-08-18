---
title: Eseguire il refactoring per convertire un ciclo for in un'istruzione foreach
description: Informazioni su come usare il menu Azioni rapide e refactoring per eseguire la conversione tra un ciclo for e un'istruzione foreach.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b6648ffa903a0a8f3e808801f1c8627a164de251
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041308"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Effettuare il refactoring per convertire un ciclo for in un'istruzione foreach e viceversa

Questo articolo descrive i refactoring di Azioni rapide per eseguire la conversione tra due strutture di ciclo. Include alcuni motivi per cui si potrebbe voler passare da un ciclo [for](/dotnet/csharp/language-reference/keywords/for) a un'istruzione [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) nel codice.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Convertire un ciclo for in un'istruzione foreach

Se il codice contiene un ciclo [for](/dotnet/csharp/language-reference/keywords/for), è possibile usare questo refactoring per convertirlo in un'istruzione [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Questo refactoring si applica a:

- C#

- Visual Basic

> [!NOTE]
> Il refactoring di Azioni rapide **Converti in foreach** è disponibile solo per i cicli [for](/dotnet/csharp/language-reference/keywords/for) che contengono tutte le tre parti: un inizializzatore, una condizione e un iteratore.

### <a name="why-convert"></a>Perché eseguire la conversione

Di seguito sono riportati alcuni motivi per cui può essere opportuno convertire un ciclo [for](/dotnet/csharp/language-reference/keywords/for) in un'istruzione [foreach](/dotnet/csharp/language-reference/keywords/foreach-in):

- Non si usa la variabile di ciclo locale all'interno del ciclo se non come indice per accedere agli elementi.

- Si vuole semplificare il codice e ridurre la probabilità di errori logici nelle sezioni di inizializzatore, condizione e iteratore.

### <a name="how-to-use-it"></a>Modo d'uso

1. Posizionare il punto di inserimento nella parola chiave `for`.

1. Premere  + **CTRL.** oppure fare clic sull'icona a forma di cacciavite ![icona cacciavite](../media/screwdriver-icon.png) nel margine del file di codice.

   ![Menu Converti in foreach](media/convert-to-foreach.png)

1. Selezionare **Converti in foreach**. In alternativa, selezionare **Anteprima modifiche** per aprire la finestra di dialogo [Anteprima modifiche](../../ide/preview-changes.md) e quindi selezionare **Applica**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Convertire un'istruzione foreach in un ciclo for

Se il codice contiene un'istruzione [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) o [For Each...Next (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement), è possibile usare questo refactoring per convertirla in un ciclo [for](/dotnet/csharp/language-reference/keywords/for).

Questo refactoring si applica a:

- C#

- Visual Basic

### <a name="why-convert"></a>Perché eseguire la conversione

Di seguito sono riportati alcuni motivi per cui può essere opportuno convertire un'istruzione [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) in un ciclo [for](/dotnet/csharp/language-reference/keywords/for):

- Si vuole usare una variabile di ciclo locale all'interno del ciclo per altre azioni oltre all'accesso all'elemento.

- Si [scorre una matrice multidimensionale](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) e si vuole avere un maggiore controllo sugli elementi della matrice.

### <a name="how-to-use-it"></a>Modo d'uso

1. Posizionare il punto di inserimento nella parola chiave `foreach` o `For Each`.

1. Premere  + **CTRL.** oppure fare clic sull'icona a forma di cacciavite ![icona cacciavite](../media/screwdriver-icon.png) nel margine del file di codice.

   ![Menu Converti in for](media/convert-to-for.png)

1. Selezionare **Converti in for**. In alternativa, selezionare **Anteprima modifiche** per aprire la finestra di dialogo [Anteprima modifiche](../../ide/preview-changes.md) e quindi selezionare **Applica**.

1. Poiché il refactoring introduce una nuova variabile Numero di iterazioni, la casella **Rinomina** appare nell'angolo superiore destro dell'editor. Se si vuole scegliere un nome diverso per la variabile, digitarlo in e quindi premere **INVIO** oppure selezionare **Applica** nella casella **Rinomina**. Se non si vuole scegliere un nuovo nome, premere **ESC** oppure selezionare **Applica** per chiudere la casella **Rinomina**.

> [!NOTE]
> Per C#, il codice generato da questi refactoring usa un tipo esplicito o [var](/dotnet/csharp/language-reference/keywords/var) per il tipo degli elementi nella raccolta. Il tipo nel codice generato, esplicito o implicito, dipende dalle impostazioni di stile del codice che rientrano nell'ambito. Queste particolari impostazioni di stile del codice vengono configurate a livello di computer in Strumenti Opzioni Editor di testo  >    >    >  **C#** Code  >  **Style**  >  **General**  >  **\' var' preferences** [](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types) o a livello di soluzione in un file EditorConfig. Se si modifica un'impostazione di stile del codice in **Opzioni**, riaprire il file di codice per rendere effettive le modifiche.

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
