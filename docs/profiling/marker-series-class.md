---
description: Rappresenta un canale seriale di eventi generati da un singolo provider.
title: Classe marker_series | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series
helpviewer_keywords:
- Concurrency, diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f02c554c9df8a71fd6ae8b7a045d1ae4e3cc0917
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626927"
---
# <a name="marker_series-class"></a>Classe marker_series
Rappresenta un canale seriale di eventi generati da un singolo provider.

## <a name="syntax"></a>Sintassi

```cpp
class marker_series;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Costruttori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[marker_series::marker_series costruttore](../profiling/marker-series-marker-series-constructor.md)|Inizializza una nuova istanza della classe `marker_series`.|
|[marker_series::~marker_series distruttore](../profiling/marker-series-tilde-marker-series-destructor.md)|Elimina l'oggetto marker_series e rilascia tutte le risorse allocate.|

### <a name="public-methods"></a>Metodi pubblici

|Nome|Descrizione|
|----------|-----------------|
|[marker_series::is_enabled metodo](../profiling/marker-series-is-enabled-method.md)|Determina se il provider è stato abilitato da una sessione.|
|[marker_series::write_alert metodo](../profiling/marker-series-write-alert-method.md)|Scrive un avviso nel file di traccia del visualizzatore di concorrenza.|
|[marker_series::write_flag](../profiling/marker-series-write-flag-method.md)|Scrive un flag nel file di traccia del visualizzatore di concorrenza.|
|[marker_series::write_message metodo](../profiling/marker-series-write-message-method.md)|Scrive un messaggio nel file di traccia del visualizzatore di concorrenza.|

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà
 `marker_series`

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkersobj.h*

 **Spazio dei nomi:** Concurrency::diagnostic

## <a name="see-also"></a>Vedi anche
- [spazio dei nomi di diagnostica](../profiling/diagnostic-namespace.md)
