---
title: Opzioni di refactoring delle funzioni locali statiche
ms.date: 02/10/2020
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
ms.openlocfilehash: c297457c910c484c05c974c581e89c75e0ad44e5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77144841"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Refactoring di funzioni locali statiche e azioni rapideStatic local function refactorings and Quick Actions

In questo articolo vengono descritte due funzionalità di produttività relative alle funzioni locali statiche. Uno è un refactoring che rende statica una funzione locale e l'altro è un'azione rapida che genera codice per passare le variabili in una funzione locale statica.

## <a name="make-local-function-static"></a>Impostare una funzione locale come statica

Questo refactoring si applica a:

- C#

**Cosa:** Rende statica una funzione locale e passa le variabili definite all'esterno della funzione alla dichiarazione e alle chiamate della funzione.

**Quando:** Si desidera che la funzione locale sia statica e che tutte le variabili vengano definite nell'ambito della funzione.

**Perché:** Le funzioni locali statiche migliorano la leggibilità: sapere che il codice specifico è isolato rende più facile comprendere, rileggere e riutilizzare. Le funzioni locali statiche forniscono anche l'ambito per evitare di inquinare una classe con una funzione statica che viene chiamata solo in un singolo metodo.

### <a name="how-to"></a>Procedure

1. Posizionare il punto di inserimento sul nome della funzione locale.

2. Premere **CTRL**+**.** (periodo) per attivare il menu **Azioni rapide e refactoring.**

   ![Impostare una funzione locale come statica](media/make-local-function-static.png)

3. Selezionare **Rendi la funzione locale 'statica'.**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Passare la variabile in modo esplicito in una funzione locale staticaPass variable explicitly in a static local function

Questa azione rapida si applica a:

- C#

**Cosa:** Passa una variabile in modo esplicito in una funzione statica locale.

**Quando:** Si desidera che una funzione locale sia statica ma utilizzi comunque variabili inizializzate all'esterno di essa.

**Perché:** L'utilizzo di funzioni locali statiche fornisce chiarimenti ai lettori perché sanno che può essere dichiarato e chiamato solo in un contesto specifico del programma. Fornisce la flessibilità di definire le variabili al di fuori di questo contesto, ma comunque in grado di passarle come argomenti alla funzione locale statica.

### <a name="how-to"></a>Procedure

1. Posizionare il punto di inserimento nella variabile in cui viene utilizzato nella funzione locale statica.

2. Premere **CTRL**+**.** (periodo) per attivare il menu **Azioni rapide e refactoring.**

   ![Passare la variabile in modo esplicito nella funzione locale staticaPass variable explicitly in static local function](media/pass-variable-explicitly-static-local-function.png)

3. Selezionare **Pass variable explicitly in local static function**(Passa variabile in modo esplicito in una funzione statica locale).

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)