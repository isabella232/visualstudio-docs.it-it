---
title: Legenda della visualizzazione Core | Microsoft Docs
description: Informazioni sulla legenda Visualizzazione core, che fornisce i dati del cambio di contesto tabulare e la selezione dei thread. Informazioni anche sui commutatori di contesto e sulle prestazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2b02000164ddea2d10cbe33a5f95f158f617ea383815a8691bd215b6a0424663
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333470"
---
# <a name="cores-view-legend"></a>Legenda della visualizzazione Core
La legenda della visualizzazione Core identifica ogni thread in base al colore e al nome. Include colonne che visualizzano il conteggio degli scambi di contesto tra core diversi, gli scambi di contesto totali e la percentuale di scambi di contesto tra core diversi. Le righe della legenda sono ordinate in base al numero di scambi di contesto tra core, in ordine decrescente.

 È possibile selezionare le righe della legenda per filtrare i thread che vengono visualizzati nella sequenza temporale. Solo i thread selezionati vengono visualizzati nella sequenza temporale. Se non è selezionata nessuna riga, nella sequenza temporale vengono visualizzate tutte le righe.

 Gli scambi di contesto tra core diversi hanno un costo più elevato in termini di sovraccarico e prestazioni rispetto agli scambi che rimangono sullo stesso core logico. Durante gli scambi di contesto, i registri del processore vengono salvati e ripristinati, viene eseguito il codice kernel del sistema operativo, le voci del buffer TLB (Translation Lookaside Buffer) vengono ricaricate e viene scaricata la pipeline del processore. Gli scambi di contesto tra core diversi possono essere anche più costosi rispetto ad altri scambi di contesto perché i dati della cache non sono validi per il thread in un altro core. Al contrario, se viene eseguito il cambio di contesto di un thread in un core in cui era già stato eseguito in precedenza, è probabile che i dati utili si trovino ancora nella cache. Quando gli scambi di contesto tra core diversi sono stati aumentati dai tentativi di gestire l'affinità di thread e le prestazioni risultano ridotte, valutare se risolvere il problema. Iniziare eliminando l'affinità di thread e quindi osservare il comportamento tra core risultante.

 La tabella seguente descrive gli elementi della legenda.

|Elemento|Definizione|
|-------------|----------------|
|Nome thread|Visualizza il colore del thread nella sequenza temporale del core precedente e il nome del thread.|
|Scambi di contesto tra core diversi|Numero di scambi di contesto per un thread che è anche passato da un core logico a un altro. Non fa distinzione tra scambi di contesto tra core diversi che avvengono tra un die del processore e un altro rispetto a quelli che rimangono nello stesso die.|
|Scambi di contesto totali|Numero totale di scambi di contesto per un determinato thread durante il periodo di campionamento. Viene conteggiato uno scambio di contesto ogni volta che un thread cambia contesto, ad esempio da esecuzione a sincronizzazione.|
|Percentuale di scambi di contesto tra core diversi|Calcolata come percentuale dividendo il numero di scambi di contesto tra core diversi per il numero di scambi di contesto totali. Maggiore sarà questa percentuale, maggiore sarà l'effetto complessivo del sovraccarico degli scambi di contesto tra core diversi sulle prestazioni di questo particolare thread.|

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Core](../profiling/cores-view.md)