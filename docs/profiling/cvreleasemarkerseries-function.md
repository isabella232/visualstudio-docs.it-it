---
title: Funzione CvReleaseMarkerSeries | Microsoft Docs
description: Vedere le informazioni di riferimento per la funzione Concurrency Visualizer SDK CvReleaseMarkerSeries (libreria C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 20619133d217dff7e8992387a9fdc94a19f419d9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084493"
---
# <a name="cvreleasemarkerseries-function"></a>Funzione CvReleaseMarkerSeries
Rilascia una serie di marcatori. Dopo il rilascio, non usare l'oggetto serie di marcatori o l'applicazione potrebbe arrestarsi in modo anomalo. Il mancato rilascio della serie di marcatori causa una perdita di memoria.

## <a name="syntax"></a>Sintassi

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>Parametri
 `pMarkerSeries` Indirizzo della variabile dell'oggetto provider. L'indirizzo non può essere NULL, la variabile può avere qualsiasi valore.

## <a name="return-value"></a>Valore restituito
 S_OK quando la serie di marcatori viene rilasciata correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkers.h*

## <a name="see-also"></a>Vedi anche
- [Informazioni di riferimento sulla libreria C++](../profiling/cpp-library-reference.md)