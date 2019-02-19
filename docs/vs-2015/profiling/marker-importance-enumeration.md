---
title: Enumerazione marker_importance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4451a7b222b66f0fe5bea2b0e5f2b8499c9033c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54779037"
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
  
|nome|Descrizione|  
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
