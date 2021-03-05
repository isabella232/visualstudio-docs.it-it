---
description: Rappresenta il livello di importanza di un marcatore del visualizzatore di concorrenza.
title: Enumerazione marker_importance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_importance
helpviewer_keywords:
- Concurrency, diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2c2e7560c91882afe1ee2608bb2ae2fc105738dc
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223940"
---
# <a name="marker_importance-enumeration"></a>Enumerazione marker_importance
Rappresenta il livello di importanza di un marcatore del visualizzatore di concorrenza.

## <a name="syntax"></a>Sintassi

```cpp
enum marker_importance;
```

## <a name="members"></a>Members

### <a name="values"></a>Valori

|Nome|Descrizione|
|----------|-----------------|
|`critical_importance`|Specifica che il marcatore è di importanza critica.|
|`high_importance`|Specifica che il marcatore è di elevata importanza.|
|`low_importance`|Specifica che il marcatore è di scarsa importanza.|
|`normal_importance`|Specifica che il marcatore è di normale importanza.|

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkersobj.h*

 **Spazio dei nomi:** Concurrency::diagnostic

## <a name="see-also"></a>Vedi anche
- [spazio dei nomi Diagnostic](../profiling/diagnostic-namespace.md)
