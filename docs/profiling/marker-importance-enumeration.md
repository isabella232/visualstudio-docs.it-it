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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1e499466eebb4ef856839d1e71880011c6490aba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076477"
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
- [spazio dei nomi diagnostic](../profiling/diagnostic-namespace.md)
