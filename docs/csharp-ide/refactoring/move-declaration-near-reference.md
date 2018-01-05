---
title: Sposta la dichiarazione accanto riferimento - Refactoring (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: c274fd758fdae468bee884fcf1686abc16ec1d7e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="move-declaration-near-reference-in-c"></a>Spostare la dichiarazione accanto al riferimento del linguaggio c# #
**Novità:** consente di spostare le dichiarazioni di variabili più vicino al loro utilizzo.

**Quando:** si dispone di dichiarazioni di variabili che possono essere in un ambito più ristretto.

**Motivo:** potrebbe lasciare è, ma che potrebbe causare problemi di migliorare la leggibilità o nascondere le informazioni. Questa è la possibilità di eseguire il refactoring per migliorare la leggibilità.

**Procedura:**

1. Posizionare il cursore nella dichiarazione di variabile.

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **Sposta la dichiarazione accanto riferimento** nel popup di finestra di anteprima.
   * **Mouse**
     * Pulsante destro del mouse nel codice, selezionare il **azioni rapide e refactoring** dal menu **Sposta la dichiarazione accanto riferimento** nel popup di finestra di anteprima.

1. Quando si è soddisfatti della modifica, premere **invio** o scegliere la correzione nel menu e le modifiche verranno salvate.

Esempio:
```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>Vedere anche  
[Refactoring (C#)](../refactoring-csharp.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)