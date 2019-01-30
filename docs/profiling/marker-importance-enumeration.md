---
title: Enumerazione marker_importance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d4049a3792fcc529352baef3e4649c6157aa7f0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992152"
---
# <a name="markerimportance-enumeration"></a>Enumerazione marker_importance
Rappresenta il livello di importanza di un marcatore del visualizzatore di concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum marker_importance;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="values"></a>Valori  
  
|nome|Description|  
|----------|-----------------|  
|`critical_importance`|Specifica che il marcatore è di importanza critica.|  
|`high_importance`|Specifica che il marcatore è di elevata importanza.|  
|`low_importance`|Specifica che il marcatore è di scarsa importanza.|  
|`normal_importance`|Specifica che il marcatore è di normale importanza.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** *cvmarkersobj.h*  
  
 **Spazio dei nomi:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vedere anche  
 [Spazio dei nomi diagnostic](../profiling/diagnostic-namespace.md)