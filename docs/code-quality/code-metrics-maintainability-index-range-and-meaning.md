---
title: "Metriche del codice: intervallo e significato dell'indice di manutenibilità"
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105782"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>Metriche del codice: intervallo e significato dell'indice di manutenibilità

Domanda: l'indice di manutenibilità è stato reimpostato per essere compreso tra 0 e 100. Come e perché è stata eseguita questa operazione?

La metrica originariamente è stata calcolata come segue: `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

L'uso di questa formula significava che era compreso tra 171 e un numero negativo non associato.  Poiché il codice tendeva a 0, era chiaramente difficile mantenere il codice e la differenza tra il codice a 0 e un valore negativo non era utile.  Come risultato della diminuzione dell'utilità dei numeri negativi e del desiderio di mantenere la metrica il più chiara possibile, si è deciso di considerare tutti gli indici 0 o meno come 0 e quindi di riasstenere l'intervallo 171 o inferiore da 0 a 100. Per questo motivo, la formula che viene utilizzata è:

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

Inoltre, abbiamo deciso di essere conservativi con le soglie.  Il desiderio era che se l'indice fosse rosso, si sarebbe detto con un elevato grado di attendibilità che si è verificato un problema con il codice.  Ciò ha dato le soglie seguenti:

Per le soglie, è stato deciso di suddividere l'intervallo 0-100 80-20 per mantenere basso il livello di disturbo ed è stato contrassegnato solo il codice sospetto. Sono stati usati i valori soglia seguenti:

- 0-9 = Rosso
- 10-19 = Giallo
- 20-100 = Verde
