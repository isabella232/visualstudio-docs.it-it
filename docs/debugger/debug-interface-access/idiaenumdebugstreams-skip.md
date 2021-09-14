---
description: Ignora un numero specificato di flussi di debug in una sequenza di enumerazione.
title: IDiaEnumDebugStreams::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Skip method
ms.assetid: 6ec7753c-d7af-4879-b107-1b3442e0b025
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6c6c83d059455cc6046547af079de022bb7447d3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630354"
---
# <a name="idiaenumdebugstreamsskip"></a>IDiaEnumDebugStreams::Skip
Ignora un numero specificato di flussi di debug in una sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametri
 `celt`

[in] Numero di flussi di debug nella sequenza di enumerazione da ignorare.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce ; in caso contrario, restituisce se `S_OK` non sono presenti altri record da `S_FALSE` ignorare.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
