---
title: Classe marker_series | Microsoft Docs
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
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd82862800feacf92059a2d019e9f9988616d615
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754197"
---
# <a name="markerseries-class"></a>Classe marker_series
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rappresenta un canale seriale di eventi generati da un singolo provider.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class marker_series;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Costruttore marker_series::marker_series](../profiling/marker-series-marker-series-constructor.md)|Inizializza una nuova istanza della classe `marker_series`.|  
|[Distruttore marker_series::~marker_series](../profiling/marker-series-tilde-marker-series-destructor.md)|Elimina l'oggetto marker_series e rilascia tutte le risorse allocate.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo marker_series::is_enabled](../profiling/marker-series-is-enabled-method.md)|Determina se il provider è stato abilitato da una sessione.|  
|[Metodo marker_series::write_alert](../profiling/marker-series-write-alert-method.md)|Scrive un avviso nel file di traccia del visualizzatore di concorrenza.|  
|[Metodo marker_series::write_flag](../profiling/marker-series-write-flag-method.md)|Scrive un flag nel file di traccia del visualizzatore di concorrenza.|  
|[Metodo marker_series::write_message](../profiling/marker-series-write-message-method.md)|Scrive un messaggio nel file di traccia del visualizzatore di concorrenza.|  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 `marker_series`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkersobj.h  
  
 **Spazio dei nomi:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vedere anche  
 [Spazio dei nomi diagnostic](../profiling/diagnostic-namespace.md)



