---
title: Metodo marker_series::write_alert | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b41cd976ddd637faf00ee50a3ec208d2b3d513f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924941"
---
# <a name="markerserieswritealert-method"></a>Metodo marker_series::write_alert
Scrive un avviso nel file di traccia del visualizzatore di concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `_Format`  
 Stringa di formato composta che contiene testo combinato con zero o più elementi di formato, che corrispondono agli oggetti nell'elenco degli argomenti.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** *cvmarkersobj.h*  
  
 **Spazio dei nomi:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vedere anche  
 [Classe marker_series](../profiling/marker-series-class.md)