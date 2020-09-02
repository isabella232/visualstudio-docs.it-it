---
title: Visualizzazione Righe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: ccdb211312a6f53e7f519b7fac0e3ac28aab2429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145633"
---
# <a name="lines-view"></a>Visualizzazione Righe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La visualizzazione Righe è disponibile solo per i dati del profiler raccolti tramite il metodo di campionamento. La visualizzazione non è disponibile per i dati raccolti mediante la strumentazione.  
  
 Per i dati del profilo di campionamento, la visualizzazione Righe identifica l'istruzione in una funzione eseguita direttamente durante la raccolta del campione. Per i dati di memoria .NET, la visualizzazione Righe identifica le istruzioni per l'allocazione della memoria.  
  
 In un file di origine un'istruzione può occupare più di una riga e una singola riga può includere più di un'istruzione.  
  
 Un'istruzione viene identificata in base agli elementi seguenti:  
  
- File di origine che contiene l'istruzione della funzione.  
  
- Funzione che contiene l'istruzione.  
  
- Riga di origine in cui inizia l'istruzione.  
  
- Carattere nella riga di origine in cui inizia l'istruzione.  
  
- Riga di origine in cui termina l'istruzione.  
  
- Carattere nella riga di origine in cui termina l'istruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione righe](../profiling/lines-view-sampling-data.md)   
 [Visualizzazione righe-campionamento](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Righe](../profiling/lines-view-contention-data.md)
