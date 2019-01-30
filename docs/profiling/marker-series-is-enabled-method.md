---
title: Metodo marker_series::is_enabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a74a1d35128eb61c08d44fc430305a9ba7756c0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936537"
---
# <a name="markerseriesisenabled-method"></a>Metodo marker_series::is_enabled
Determina se il provider è stato abilitato da una sessione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
bool is_enabled();  
bool is_enabled(  
   marker_importance _Importance,  
   int _Category  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `_Importance`  
 Livello di importanza.  
  
 `_Category`  
 Categoria.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** *cvmarkersobj.h*  
  
 **Spazio dei nomi:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vedere anche  
 [Classe marker_series](../profiling/marker-series-class.md)