---
title: Enumerazione marker_importance | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32e57a9463e6c6966c215066fd470b62596f5481
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756862"
---
# <a name="markerimportance-enumeration"></a>Enumerazione marker_importance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rappresenta il livello di importanza di un marcatore del visualizzatore di concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="values"></a>Valori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`critical_importance`|Specifica che il marcatore è di importanza critica.|  
|`high_importance`|Specifica che il marcatore è di elevata importanza.|  
|`low_importance`|Specifica che il marcatore è di scarsa importanza.|  
|`normal_importance`|Specifica che il marcatore è di normale importanza.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vedere anche  
 [Spazio dei nomi diagnostic](../profiling/diagnostic-namespace.md)



