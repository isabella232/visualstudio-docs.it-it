---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1de2d6c9700dcb7b1106c3693d855bb1d8ae2cfa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738504"
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
Thunk standard THUNK_ORDINAL_NOTYPE.

THUNK_ORDINAL_ADJUSTOR un thunk di regolazione `this`.

Thunk di chiamata virtuale THUNK_ORDINAL_VCALL.

THUNK_ORDINAL_PCODE P-thunk di codice.

Thunk di caricamento ritardato THUNK_ORDINAL_LOAD.

Thunk THUNK_ORDINAL_TRAMP_INCREMENTAL incrementale per il trampolino (un thunk del trampolino viene usato per rimbalzare le chiamate da uno spazio di memoria a un altro).

Thunk del punto di THUNK_ORDINAL_TRAMP_BRANCHISLAND del ramo.

## <a name="remarks"></a>Note
I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
