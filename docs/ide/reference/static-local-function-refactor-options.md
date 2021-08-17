---
title: Opzioni di refactoring delle funzioni locali statiche
description: Informazioni su come usare il menu Azioni rapide e refactoring per rendere statica una funzione locale e passare le variabili definite all'esterno della funzione alla dichiarazione e alle chiamate della funzione.
ms.custom: SEO-VS-2020
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: aea122e61bec36a5e8c37ce443e4fdf0254bc6d6950cff704721e282b6dabb10
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400140"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Refactoring di funzioni locali statiche e azioni rapide

Questo articolo illustra due funzionalità di produttività correlate alle funzioni locali statiche. Uno è un refactoring che rende statica una funzione locale e l'altro è un'azione rapida che genera codice per passare variabili in una funzione locale statica.

## <a name="make-local-function-static"></a>Impostare una funzione locale come statica

Questo refactoring si applica a:

- C#

**Cosa:** Rende statica una funzione locale e passa le variabili definite all'esterno della funzione alla dichiarazione e alle chiamate della funzione.

**Quando:** Si vuole che la funzione locale sia statica e che tutte le variabili siano definite nell'ambito della funzione.

**Perché:** Le funzioni locali statiche migliorano la leggibilità: la consapevolezza che il codice specifico è isolato semplifica la comprensione, la rilettura e il riutilizzo. Le funzioni locali statiche forniscono anche l'ambito per impedire la rimozione di una classe con una funzione statica chiamata solo in un singolo metodo.

### <a name="how-to"></a>Procedure

1. Posizionare il punto di controllo sul nome della funzione locale.

2. Premere  + **CTRL.** (punto) per attivare il menu **Azioni rapide e refactoring.**

   ![Impostare una funzione locale come statica](media/make-local-function-static.png)

3. Selezionare **Make local function 'static' (Rendi statica la funzione locale).**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Passare la variabile in modo esplicito in una funzione locale statica

Questa azione rapida si applica a:

- C#

**Cosa:** Passa una variabile in modo esplicito in una funzione statica locale.

**Quando:** Si vuole che una funzione locale sia statica ma usi comunque variabili inizializzate all'esterno di essa.

**Perché:** L'uso di funzioni locali statiche fornisce chiarimenti ai lettori perché sa che può essere dichiarata e chiamata solo in un contesto specifico del programma. Offre la flessibilità necessaria per definire variabili esterne a questo contesto, ma è comunque possibile passarle come argomenti alla funzione locale statica.

### <a name="how-to"></a>Procedure

1. Posizionare il punto di riferimento sulla variabile in cui viene usato nella funzione locale statica.

2. Premere  + **CTRL.** (punto) per attivare il menu **Azioni rapide e refactoring.**

   ![Passare la variabile in modo esplicito in una funzione locale statica](media/pass-variable-explicitly-static-local-function.png)

3. Selezionare **Pass variable explicitly in local static function**(Passa variabile in modo esplicito in una funzione statica locale).

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)