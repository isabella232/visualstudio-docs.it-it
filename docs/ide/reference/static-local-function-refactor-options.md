---
title: Refactoring di funzioni locali statiche
ms.date: 09/28/2019
ms.topic: reference
author: governesss
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: adbf84b9ae7566cd5e58a7c757ce09a37252b754
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74782279"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Refactoring di funzioni locali statiche e azioni rapide

Questo articolo descrive due funzionalità di produttività correlate alle funzioni locali statiche. Uno è un refactoring che rende statica una funzione locale e l'altra è un'azione rapida che genera codice per passare le variabili in una funzione locale statica.

## <a name="make-local-function-static"></a>Rendi statica la funzione locale

Questo refactoring si applica a:

- C#

**Cosa:** Rende statica una funzione locale e passa le variabili definite all'esterno della funzione alla dichiarazione e alle chiamate della funzione.

**Quando:** Si vuole che la funzione locale sia statica e che tutte le variabili siano definite nell'ambito della funzione.

**Motivo:** Le funzioni locali statiche migliorano la leggibilità: sapere che il codice specifico è isolato rende più semplice comprendere, rileggere e riutilizzare. Le funzioni locali statiche forniscono anche l'ambito per impedire l'inquinamento di una classe con una funzione statica che viene chiamata solo in un singolo metodo.

### <a name="how-to"></a>Procedura

1. Posizionare il punto di inserimento sul nome della funzione locale.

2. Premere **CTRL**+ **.** (periodo) per attivare il menu **azioni rapide e refactoring** .

   ![Rendi statica la funzione locale](media/make-local-function-static.png)

3. Selezionare **make local Function "static".**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Passare la variabile in modo esplicito in una funzione locale statica

Questa azione rapida si applica a:

- C#

**Cosa:** Passa una variabile in modo esplicito in una funzione statica locale.

**Quando:** Si vuole che una funzione locale sia statica, ma usa comunque le variabili inizializzate al di fuori di essa.

**Motivo:** L'utilizzo di funzioni locali statiche fornisce chiarimenti ai lettori perché sa che possono essere dichiarati e chiamati solo in un contesto specifico del programma. Offre la flessibilità necessaria per definire le variabili all'esterno di questo contesto, ma è comunque possibile passarle come argomenti alla funzione locale statica.

### <a name="how-to"></a>Procedura

1. Posizionare il cursore sulla variabile in cui viene usato nella funzione locale statica.

2. Premere **CTRL**+ **.** (periodo) per attivare il menu **azioni rapide e refactoring** .

   ![Passare la variabile in modo esplicito nella funzione locale statica](media/pass-variable-explicitly-static-local-function.png)

3. Selezionare **Pass variable explicitly in local static function**(Passa variabile in modo esplicito in una funzione statica locale).

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)