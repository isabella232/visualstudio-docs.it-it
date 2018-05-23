---
title: Effettuare il refactoring del codice per convertire un ciclo for in un'istruzione foreach
ms.date: 05/10/2018
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
ms.openlocfilehash: 34758473bcbee8ccad7d9dff9df2f1478ca1202c
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/11/2018
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Effettuare il refactoring per convertire un ciclo for in un'istruzione foreach e viceversa

Questi refactoring si applicano a:

- C#

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Convertire un ciclo for in un'istruzione foreach

Se il codice contiene un ciclo [for](/dotnet/csharp/language-reference/keywords/for), è possibile usare questo refactoring per convertirlo in un'istruzione [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

### <a name="why-convert"></a>Perché eseguire la conversione

Di seguito sono riportati alcuni motivi per cui può essere opportuno convertire un ciclo [for](/dotnet/csharp/language-reference/keywords/for) in un'istruzione [foreach](/dotnet/csharp/language-reference/keywords/foreach-in):

- Non si usa la variabile Numero di iterazioni all'interno del ciclo se non come indice per accedere all'elemento.

- Si vuole semplificare il codice e ridurre la probabilità di errori logici nell'inizializzatore, nella condizione e nelle istruzioni di iterazione.

### <a name="how-to-use-it"></a>Come usare la funzionalità

1. Posizionare il cursore sulla prima riga del ciclo `for`.

1. Premere **CTRL**+**.** oppure fare clic sull'icona a forma di cacciavite ![icona cacciavite](../media/screwdriver-icon.png) nel margine del file di codice.

   ![Menu Converti in foreach](media/convert-to-foreach.png)

1. Selezionare **Converti in foreach**. In alternativa, selezionare **Anteprima modifiche** per aprire la finestra di dialogo [Anteprima modifiche](../../ide/preview-changes.md) e quindi selezionare **Applica**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Convertire un'istruzione foreach in un ciclo for

Se il codice contiene un'istruzione [foreach](/dotnet/csharp/language-reference/keywords/foreach-in), è possibile usare questo refactoring per convertirla in un ciclo [for](/dotnet/csharp/language-reference/keywords/for).

### <a name="why-convert"></a>Perché eseguire la conversione

Di seguito sono riportati alcuni motivi per cui può essere opportuno convertire un'istruzione [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) in un ciclo [for](/dotnet/csharp/language-reference/keywords/for):

- Si vuole usare la variabile Numero di iterazioni all'interno del ciclo per altre azioni oltre all'accesso all'elemento.

- Si [scorre una matrice multidimensionale](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) e si vuole avere un maggiore controllo sugli elementi della matrice.

### <a name="how-to-use-it"></a>Come usare la funzionalità

1. Posizionare il cursore sulla prima riga dell'istruzione `foreach`.

1. Premere **CTRL**+**.** oppure fare clic sull'icona a forma di cacciavite ![icona cacciavite](../media/screwdriver-icon.png) nel margine del file di codice.

   ![Menu Converti in for](media/convert-to-for.png)

1. Selezionare **Converti in for**. In alternativa, selezionare **Anteprima modifiche** per aprire la finestra di dialogo [Anteprima modifiche](../../ide/preview-changes.md) e quindi selezionare **Applica**.

1. Poiché il refactoring introduce una nuova variabile Numero di iterazioni, la casella **Rinomina** appare nell'angolo superiore destro dell'editor. Se si vuole scegliere un nome diverso per la variabile, digitarlo in e quindi premere **INVIO** oppure selezionare **Applica** nella casella **Rinomina**. Se non si vuole scegliere un nuovo nome, premere **ESC** oppure selezionare **Applica** per chiudere la casella **Rinomina**.

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)