---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d67a1806034d55147379626b6eb4f868532e4d77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330744"
---
# <a name="marker_importance-enumeration"></a>Enumerazione marker_importance
Rappresenta il livello di importanza di un marcatore del visualizzatore di concorrenza.

## <a name="syntax"></a>Sintassi

```cpp
enum marker_importance;
```

## <a name="members"></a>Members

### <a name="values"></a>Valori

|Name|Descrizione|
|----------|-----------------|
|`critical_importance`|Specifica che il marcatore è di importanza critica.|
|`high_importance`|Specifica che il marcatore è di elevata importanza.|
|`low_importance`|Specifica che il marcatore è di scarsa importanza.|
|`normal_importance`|Specifica che il marcatore è di normale importanza.|

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkersobj.h*

 **Spazio dei nomi:** Concurrency::diagnostic

## <a name="see-also"></a>Vedere anche
- [spazio dei nomi Diagnostic](../profiling/diagnostic-namespace.md)