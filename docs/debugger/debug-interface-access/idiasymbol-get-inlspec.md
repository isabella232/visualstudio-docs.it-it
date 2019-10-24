---
title: IDiaSymbol::get_InlSpec | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_InlSpec method
ms.assetid: 30af6a2f-be84-429e-a96a-d0f9ed9343fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5675239e35ab3bef809e3d54544d87d7a9e8bb75
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740387"
---
# <a name="idiasymbolget_inlspec"></a>IDiaSymbol::get_InlSpec
Questa funzione recupera un flag che indica se la funzione è stata contrassegnata come inline (usando uno degli attributi [inline, __inline, \__forceinline](/cpp/cpp/inline-functions-cpp) ).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_inlSpec(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se la funzione è stata contrassegnata come inline; in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisiti|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [inline, __inline, \__forceinline](/cpp/cpp/inline-functions-cpp)