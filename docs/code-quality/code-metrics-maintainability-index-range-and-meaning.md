---
title: "Metriche del codice : intervallo e significato dell'indice di manutenibilità"
ms.date: 1/8/2021
description: Informazioni sulla metrica dell'intervallo di indici di manutenibilità per le metriche del codice in Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 8ab6115dd0c0a17bf6bb302d7c160e969d11773e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632063"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>Metriche del codice : intervallo e significato dell'indice di manutenibilità

Domanda: L'indice di manutenibilità è stato reimpostato in modo da essere compreso tra 0 e 100. Come e perché è stata eseguita questa operazione?

La metrica originariamente è stata calcolata come segue: `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

L'uso di questa formula indicava un intervallo compreso tra 171 e un numero negativo non associato.  Poiché il codice tendeva verso 0, era chiaramente difficile mantenere il codice e la differenza tra il codice a 0 e un valore negativo non era utile.  In seguito alla diminuzione dell'utilità dei numeri negativi e al voler mantenere la metrica il più chiara possibile, si è deciso di considerare tutti gli indici 0 o meno come 0 e quindi di riasstenere l'intervallo di 171 o inferiore in modo che sia compreso tra 0 e 100. Per questo motivo, la formula da usare è:

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

Inoltre, si è deciso di essere conservativi con le soglie.  Il volere era che se l'indice risultasse rosso, si sarebbe detto con un livello elevato di attendibilità che si è verificato un problema con il codice.  Questo ha dato le soglie seguenti:

Per le soglie, si è deciso di suddividere questo intervallo da 0 a 100 80-20 per mantenere basso il livello di disturbo ed è stato contrassegnato solo il codice sospetto. Sono stati usati i valori soglia seguenti:

- 0-9 = Rosso
- 10-19 = Giallo
- 20-100 = Verde
