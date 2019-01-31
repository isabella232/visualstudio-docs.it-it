---
title: Metodo marker_series::write_alert | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d65bec449938a55ee9a415dd86db1ba07efbdb1b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792833"
---
# <a name="markerserieswritealert-method"></a>Metodo marker_series::write_alert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Scrive un avviso nel file di traccia del visualizzatore di concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `_Format`  
 Stringa di formato composta che contiene testo combinato con zero o più elementi di formato, che corrispondono agli oggetti nell'elenco degli argomenti.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vedere anche  
 [Classe marker_series](../profiling/marker-series-class.md)
