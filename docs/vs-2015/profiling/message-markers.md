---
title: Marcatori messaggio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 84c7a173bf0b7f5b3dc2187c0c8574819b2317a9
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54804027"
---
# <a name="message-markers"></a>Marcatori di messaggi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un marcatore del messaggio rappresenta l'output del log. Un messaggio è una stringa che viene emessa da un thread specifico in un momento specifico. È possibile esportare i messaggi in un file di testo per usarli con altri strumenti. È possibile posizionare il puntatore del mouse su un messaggio nel visualizzatore di concorrenza per visualizzare la stringa del messaggio. È anche possibile visualizzare tutti i marcatori del messaggio nel [rapporto Marcatori](../profiling/markers-report.md).  La figura seguente mostra un marcatore del messaggio.  
  
## <a name="message-aggregation-markers"></a>Marcatori di aggregazione di messaggi  
 Talvolta più messaggi si presentano a così poca distanza tra loro nel visualizzatore di concorrenza da non poter essere rappresentati singolarmente. In questo caso, viene visualizzato un *marcatore di aggregazione di messaggi* che rappresenta i messaggi sottostanti. Quando si posiziona il puntatore del mouse su una di queste icone, compare una descrizione comando che mostra il numero di messaggi sottostanti rappresentati. Per visualizzare i messaggi, fare zoom avanti.  Se viene fatto zoom avanti completamente e viene visualizzato ancora un marcatore di aggregazione, è possibile visualizzare i messaggi sottostanti nel [rapporto Marcatori](../profiling/markers-report.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Marcatori del visualizzatore di concorrenza](../profiling/concurrency-visualizer-markers.md)   
 [SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md)
