---
title: Visualizzazione Righe | Microsoft Docs
description: Informazioni sul modo in cui la visualizzazione righe è disponibile solo per i dati del profiler raccolti tramite il metodo di campionamento.
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f99431faaa7bfc77bd7cd9a14be03f7cc2238127
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917832"
---
# <a name="lines-view"></a>Visualizzazione Righe
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

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Righe](../profiling/lines-view-sampling-data.md)
- [Visualizzazione righe-campionamento](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Visualizzazione Righe](../profiling/lines-view-contention-data.md)
