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
ms.openlocfilehash: 03671f314dca3c016f9524bcb246b74e0eb1f837
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600673"
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
- [Spazio dei nomi Concurrency (visualizzatore di concorrenza)](../profiling/concurrency-namespace-concurrency-visualizer.md)