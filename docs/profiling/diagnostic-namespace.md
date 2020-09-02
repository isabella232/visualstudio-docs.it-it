---
title: Spazio dei nomi diagnostic | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic
helpviewer_keywords:
- Concurrency, diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 680d304a8e4d21365d82f654265ae2f34582b636
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330258"
---
# <a name="diagnostic-namespace"></a>Spazio dei nomi diagnostic
Lo spazio dei nomi `diagnostics` offre funzionalità per l'emissione di marcatori del visualizzatore di concorrenza.

## <a name="syntax"></a>Sintassi

```cpp
namespace diagnostic;
```

## <a name="members"></a>Members

### <a name="classes"></a>Classi

|Name|Descrizione|
|----------|-----------------|
|[Classe marker_series](../profiling/marker-series-class.md)|Rappresenta un canale seriale di eventi generati da un singolo provider.|
|[Classe Span](../profiling/span-class.md)|Definisce una fase dell'applicazione.|

### <a name="enumerations"></a>Enumerazioni

|Name|Descrizione|
|----------|-----------------|
|[Enumerazione marker_importance](../profiling/marker-importance-enumeration.md)|Rappresenta il livello di importanza di un marcatore del visualizzatore di concorrenza.|

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkersobj.h*

 **Spazio dei nomi:** Concorrenza

## <a name="see-also"></a>Vedere anche
- [Spazio dei nomi Concurrency (Visualizzatore di concorrenza)](../profiling/concurrency-namespace-concurrency-visualizer.md)