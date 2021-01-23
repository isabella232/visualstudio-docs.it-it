---
title: Marcatori messaggio | Microsoft Docs
description: Informazioni su come esportare messaggi in un file di testo da usare con altri strumenti e posizionare il puntatore su un messaggio nel Visualizzatore di concorrenza per visualizzare la stringa del messaggio.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d8e4d493173cb50f62510a9b776701a0b199f47
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720566"
---
# <a name="message-markers"></a>Marcatori di messaggio
Un marcatore del messaggio rappresenta l'output del log. Un messaggio è una stringa che viene emessa da un thread specifico in un momento specifico. È possibile esportare i messaggi in un file di testo per usarli con altri strumenti. È possibile posizionare il puntatore del mouse su un messaggio nel visualizzatore di concorrenza per visualizzare la stringa del messaggio. È possibile visualizzare tutti i marcatori dei messaggi nel [Rapporto marcatori](../profiling/markers-report.md).  La figura seguente mostra un marcatore del messaggio.

## <a name="message-aggregation-markers"></a>Marcatori di aggregazione di messaggi
 Talvolta più messaggi si presentano a così poca distanza tra loro nel visualizzatore di concorrenza da non poter essere rappresentati singolarmente. In questo caso, viene visualizzato un *marcatore di aggregazione di messaggi* che rappresenta i messaggi sottostanti. Quando si posiziona il puntatore del mouse su una di queste icone, compare una descrizione comando che mostra il numero di messaggi sottostanti rappresentati. Per visualizzare i messaggi, fare zoom avanti.  Se viene fatto zoom avanti completamente e viene visualizzato ancora un marcatore di aggregazione, è possibile visualizzare i messaggi sottostanti nel [rapporto Marcatori](../profiling/markers-report.md).

## <a name="see-also"></a>Vedere anche
- [Marcatori del Visualizzatore di concorrenza](../profiling/concurrency-visualizer-markers.md)
- [SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md)