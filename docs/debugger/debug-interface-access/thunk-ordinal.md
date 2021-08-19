---
description: Designa i tipi thunk.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 30a8f8d43056011bc28113bde1ce837da0205bc2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052172"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Designa i tipi thunk.

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
THUNK_ORDINAL_NOTYPE thunk Standard.

THUNK_ORDINAL_ADJUSTOR `this` thunk del regolatore.

THUNK_ORDINAL_VCALL thunk di chiamata virtuale.

THUNK_ORDINAL_PCODE thunk P-code.

THUNK_ORDINAL_LOAD thunk di caricamento ritardato.

THUNK_ORDINAL_TRAMP_INCREMENTAL thunk del trampolino incrementale (un thunk di trampolino viene usato per gonfiare le chiamate da uno spazio di memoria a un altro).

THUNK_ORDINAL_TRAMP_BRANCHISLAND thunk del trampolino del punto ramo.

## <a name="remarks"></a>Commenti
I valori in questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol::get_thunkOrdinal.](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
