---
description: Definisce i tipi thunk.
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
ms.openlocfilehash: c2ed7f7945c9ab4fb51d8ad434535d48e30b26ee12cbb880ed72500330d2c966
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240440"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Definisce i tipi thunk.

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

THUNK_ORDINAL_ADJUSTOR un `this` thunk del regolatore.

THUNK_ORDINAL_VCALL thunk di chiamata virtuale.

THUNK_ORDINAL_PCODE thunk del codice P.

THUNK_ORDINAL_LOAD thunk di caricamento ritardato.

THUNK_ORDINAL_TRAMP_INCREMENTAL thunk incrementale apolineo (un thunk apolineo viene usato per gonfiare le chiamate da uno spazio di memoria a un altro).

THUNK_ORDINAL_TRAMP_BRANCHISLAND thunk a virgola mobile del punto di diramazione.

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono restituiti da una chiamata al [metodo IDiaSymbol::get_thunkOrdinal.](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
