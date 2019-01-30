---
title: Spazio dei nomi diagnostic | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68f365210c2ed365a7e9ce75ab3c6fbcd309e01a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984054"
---
# <a name="diagnostic-namespace"></a>Spazio dei nomi diagnostic
Lo spazio dei nomi `diagnostics` offre funzionalità per l'emissione di marcatori del visualizzatore di concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
namespace diagnostic;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="classes"></a>Classi  
  
|nome|Description|  
|----------|-----------------|  
|[Classe marker_series](../profiling/marker-series-class.md)|Rappresenta un canale seriale di eventi generati da un singolo provider.|  
|[Classe span](../profiling/span-class.md)|Definisce una fase dell'applicazione.|  
  
### <a name="enumerations"></a>Enumerazioni  
  
|nome|Description|  
|----------|-----------------|  
|[Enumerazione marker_importance](../profiling/marker-importance-enumeration.md)|Rappresenta il livello di importanza di un marcatore del visualizzatore di concorrenza.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** *cvmarkersobj.h*  
  
 **Spazio dei nomi:** Concorrenza  
  
## <a name="see-also"></a>Vedere anche  
 [Spazio dei nomi Concurrency (visualizzatore di concorrenza)](../profiling/concurrency-namespace-concurrency-visualizer.md)