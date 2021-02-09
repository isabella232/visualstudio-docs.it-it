---
title: Metrica del codice-intervallo di indici di gestibilità e significato
ms.date: 1/8/2021
description: Informazioni sulla metrica dell'intervallo di indici di manutenzione per la metrica del codice in Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa825b439b75606da136635d5816ac3e19ea8392
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860464"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>Metrica del codice-intervallo di indici di gestibilità e significato

Domanda: l'indice di gestibilità è stato reimpostato in modo da essere compreso tra 0 e 100. Come e perché questa operazione è stata eseguita?

La metrica è stata originariamente calcolata come segue: `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

L'uso di questa formula significava che è compreso tra 171 e un numero negativo non associato.  Poiché il codice tendeva a 0, era chiaramente difficile gestire il codice e la differenza tra il codice in 0 e un valore negativo non era utile.  In seguito all'utilità decrescente dei numeri negativi e al desiderio di tenere la metrica più chiara possibile, è stato deciso di considerare tutti i 0 o meno indici come 0 e quindi di riassegnare l'intervallo 171 o less a un valore compreso tra 0 e 100. Per questo motivo, la formula usata è:

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

Inoltre, abbiamo deciso di essere conservatore con le soglie.  Il desiderio era che se l'indice mostrasse il rosso, avremmo detto con un alto livello di confidenza che si è verificato un problema con il codice.  Questo ha fornito le soglie seguenti:

Per le soglie, si è deciso di suddividere questo intervallo 0-100 80-20 per ridurre il livello di disturbo e si è rilevato solo codice sospetto. Sono state usate le soglie seguenti:

- 0-9 = rosso
- 10-19 = giallo
- 20-100 = verde
