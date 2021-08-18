---
title: Visualizzazione Righe | Microsoft Docs
description: Informazioni su come la visualizzazione Righe è disponibile solo per i dati del profiler raccolti tramite il metodo di campionamento.
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
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 645bd910ec6213f9aef006f7e95e1f3fe7833250
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141805"
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
- [Visualizzazione Righe - Campionamento](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Visualizzazione Righe](../profiling/lines-view-contention-data.md)
