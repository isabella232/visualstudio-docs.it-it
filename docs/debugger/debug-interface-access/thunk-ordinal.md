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
ms.openlocfilehash: 776ee35e57b62463d47fc6f7fa26133f507f16f9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613271"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Definisce i tipi di thunk.

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
Thunk THUNK_ORDINAL_NOTYPE Standard.

Oggetto THUNK_ORDINAL_ADJUSTOR `this` thunk DS.

Thunk chiamata THUNK_ORDINAL_VCALL virtuale.

Thunk P-code THUNK_ORDINAL_PCODE.

Thunk carico THUNK_ORDINAL_LOAD ritardo.

Thunk trampoline THUNK_ORDINAL_TRAMP_INCREMENTAL incrementale (un thunk trampoline viene usato a oscillare in chiamate dallo spazio di memoria a un altro).

Thunk di trampoline punto THUNK_ORDINAL_TRAMP_BRANCHISLAND ramo.

## <a name="remarks"></a>Osservazioni
I valori di questa enumerazione vengono restituiti da una chiamata per il [Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
