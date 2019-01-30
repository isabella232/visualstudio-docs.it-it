---
title: Visualizzazione Righe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5b81c724d5b0c8057abb706073c3faf94bfe1b7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965198"
---
# <a name="lines-view"></a>Visualizzazione Righe
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
 [Visualizzazione Righe: campionamento](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Righe](../profiling/lines-view-contention-data.md)