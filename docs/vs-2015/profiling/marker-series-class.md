---
title: Classe marker_series | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb199d74ade593d0bc8318c27bc96ffbf70e4dcf
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54778870"
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
  
|nome|Descrizione|  
|----------|-----------------|  
|[Costruttore marker_series::marker_series](../profiling/marker-series-marker-series-constructor.md)|Inizializza una nuova istanza della classe `marker_series`.|  
|[Distruttore marker_series::~marker_series](../profiling/marker-series-tilde-marker-series-destructor.md)|Elimina l'oggetto marker_series e rilascia tutte le risorse allocate.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|nome|Descrizione|  
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
