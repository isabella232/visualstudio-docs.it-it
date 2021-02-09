---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c3984f106b3b29a25adac70745166878927a60b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862276"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Designa i tipi di thunk.

## <a name="syntax"></a>Sintassi

```C++
typedef enum THUNK_ORDINAL {
    THUNK_ORDINAL_NOTYPE,
    THUNK_ORDINAL_ADJUSTOR,
    THUNK_ORDINAL_VCALL,
    THUNK_ORDINAL_PCODE,
    THUNK_ORDINAL_LOAD

    // trampoline thunk ordinals - only for use in Trampoline thunk symbols
    THUNK_ORDINAL_TRAMP_INCREMENTAL,
    THUNK_ORDINAL_TRAMP_BRANCHISLAND,
} THUNK_ORDINAL;
```

## <a name="elements"></a>Elementi
THUNK_ORDINAL_NOTYPE thunk standard.

THUNK_ORDINAL_ADJUSTOR un `this` thunk di regolazione.

THUNK_ORDINAL_VCALL thunk di chiamata virtuale.

THUNK_ORDINAL_PCODE thunk del codice P.

THUNK_ORDINAL_LOAD thunk di caricamento ritardato.

THUNK_ORDINAL_TRAMP_INCREMENTAL thunk del trampolino incrementale (un thunk del trampolino viene usato per rimbalzare le chiamate da uno spazio di memoria a un altro).

Thunk del punto di THUNK_ORDINAL_TRAMP_BRANCHISLAND ramo.

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
