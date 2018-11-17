---
title: Visualizzazione Righe | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 829db9b1f8e4826ea9761a4433e6ee1adaab49e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749984"
---
# <a name="lines-view"></a>Visualizzazione Righe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La visualizzazione Righe è disponibile solo per i dati del profiler raccolti tramite il metodo di campionamento. La visualizzazione non è disponibile per i dati raccolti mediante la strumentazione.  
  
 Per i dati del profilo di campionamento, la visualizzazione Righe identifica l'istruzione in una funzione eseguita direttamente durante la raccolta del campione. Per i dati di memoria .NET, la visualizzazione Righe identifica le istruzioni per l'allocazione della memoria.  
  
 In un file di origine un'istruzione può occupare più di una riga e una singola riga può includere più di un'istruzione.  
  
 Un'istruzione viene identificata in base agli elementi seguenti:  
  
-   File di origine che contiene l'istruzione della funzione.  
  
-   Funzione che contiene l'istruzione.  
  
-   Riga di origine in cui inizia l'istruzione.  
  
-   Carattere nella riga di origine in cui inizia l'istruzione.  
  
-   Riga di origine in cui termina l'istruzione.  
  
-   Carattere nella riga di origine in cui termina l'istruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Righe](../profiling/lines-view-sampling-data.md)   
 [Visualizzazione Righe - Campionamento](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Righe](../profiling/lines-view-contention-data.md)



