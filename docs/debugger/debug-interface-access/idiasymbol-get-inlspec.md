---
description: Questa funzione recupera un flag che indica se la funzione è stata contrassegnata come inline (usando uno degli attributi inline, _inline, __forceinline).
title: IDiaSymbol::get_InlSpec | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_InlSpec method
ms.assetid: 30af6a2f-be84-429e-a96a-d0f9ed9343fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f566ad0c13e64eda7ea8d6278d75261536b299423ae77ba65da996b9cdeeec65
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404826"
---
# <a name="idiasymbolget_inlspec"></a>IDiaSymbol::get_InlSpec
Questa funzione recupera un flag che indica se la funzione è stata contrassegnata come inline (usando uno degli attributi [inline, __inline, \_ _forceinline](/cpp/cpp/inline-functions-cpp) inline).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_inlSpec(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se la funzione è stata contrassegnata come inline; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o codice `S_FALSE` di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [inline, __inline, \_ _forceinline](/cpp/cpp/inline-functions-cpp)
