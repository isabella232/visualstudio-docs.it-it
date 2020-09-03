---
title: Funzione CvCreateDefaultMarkerSeriesOfDefaultProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb0ab16dcd7e42a496317f4e7589bafdbdaf83dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161993"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>Funzione CvCreateDefaultMarkerSeriesOfDefaultProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Crea serie di marcatori predefinite di un provider predefinito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppProvider`  
 Indirizzo della variabile dell'oggetto provider. L'indirizzo non può essere NULL, la variabile può avere qualsiasi valore.  
  
 `ppMarkerSeries`  
 Indirizzo della variabile dell'oggetto serie marcatori. L'indirizzo non può essere NULL, la variabile può avere qualsiasi valore.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK quando sia il provider che la serie di marcatori vengono creati correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkers.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alla libreria C++](../profiling/cpp-library-reference.md)
