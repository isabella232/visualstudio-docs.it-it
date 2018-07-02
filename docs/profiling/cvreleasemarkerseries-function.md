---
title: Funzione CvReleaseMarkerSeries | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27c5bbc5d47972a4829c4e46f6aafdcf8ee76fad
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749359"
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
 `pMarkerSeries`  
 Indirizzo della variabile dell'oggetto provider. L'indirizzo non può essere NULL, la variabile può avere qualsiasi valore.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK quando la serie di marcatori viene rilasciata correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** *cvmarkers.h*  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)