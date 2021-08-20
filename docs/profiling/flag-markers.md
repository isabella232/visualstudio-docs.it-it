---
title: Marcatori flag | Microsoft Docs
description: Informazioni sui marcatori flag nel visualizzatore Visual Studio concorrenza. Un marcatore flag rappresenta un evento che si è verificato in un determinato istante di tempo all'interno di un'app.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bdc63b316f76ea048223af61a0822077d11c0b9e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150417"
---
# <a name="flag-markers"></a>Marcatori flag
Un marcatore flag rappresenta un evento che si è verificato in un determinato istante di tempo all'interno di un'app. Un flag può rappresentare molti tipi di eventi dell'applicazione. Ad esempio, un flag può indicare quando è stato pianificato un particolare elemento di lavoro o quando è stata generata un'eccezione. Anche i runtime come Task Parallel Library possono generare flag.

## <a name="flag-importance"></a>Importanza dei flag
 I flag vengono visualizzati con dimensioni diverse a seconda della loro importanza. Come per qualsiasi marcatore, l'importanza può essere bassa, normale, alta o critica.  La figura seguente mostra l'aspetto dei marcatori in base al livello di importanza:

 ![Marcatori di importanza bassa, normale, alta e critica](../profiling/media/cvmarkerimportance.png "CVMarkerImportance") Marcatori che mostrano l'importanza del flag

## <a name="flag-category"></a>Categoria dei flag
 Un flag viene visualizzato in uno dei cinque diversi colori seguenti, a seconda della categoria. I colori vengono riutilizzati se sono presenti più di cinque categorie. Non è possibile scegliere il colore. Come per qualsiasi marcatore, la categoria può essere un numero intero qualsiasi. La figura seguente mostra i colori per le prime cinque categorie.

 ![Cinque colori dei marcatori di categoria](../profiling/media/cvmarkercategory.png "CVMarkerCategory") Marcatori che mostrano le categorie

## <a name="alerts"></a>Avvisi
 Un avviso è un flag di colore rosso che rappresenta un evento dell'applicazione critico, come un'eccezione.  Ecco un esempio di avviso:

 ![Marcatore di avviso del visualizzatore di concorrenza](../profiling/media/cvmarkeralert.png "CVMarkerAlert") Marcatore di avviso

## <a name="aggregation-flags"></a>Flag di aggregazione
 Talvolta i flag si verificano a così poca distanza tra loro nel visualizzatore di concorrenza da non poter essere rappresentati singolarmente. Quando ciò accade, viene visualizzato un *flag di aggregazione* grigio che rappresenta i flag sottostanti. Quando si posiziona il puntatore del mouse su una di queste icone, compare una descrizione comando che mostra il numero di flag sottostanti rappresentati. Per visualizzare i flag, fare zoom avanti. Se viene fatto zoom avanti completamente e viene visualizzato ancora un flag di aggregazione, è possibile visualizzare i flag sottostanti nel [rapporto Marcatori](../profiling/markers-report.md).

 I flag di aggregazione sono rappresentati con diverse dimensioni. La dimensione dipende dal livello di importanza del flag più importante nell'aggregazione. La figura seguente mostra i flag di aggregazione in ordine di importanza crescente.

 ![Flag di aggregazione che mostrano quattro livelli di importanza](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate") Flag di aggregazione per livello di importanza

## <a name="see-also"></a>Vedi anche
- [Marcatori del visualizzatore di concorrenza](../profiling/concurrency-visualizer-markers.md)
- [SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md)