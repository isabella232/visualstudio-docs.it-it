---
title: BasicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7d9df59d5a3075bf63d619a03e8fe31da6991a1
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462281"
---
# <a name="basictype"></a>BasicType
Specifica il tipo di base del simbolo.

## <a name="syntax"></a>Sintassi

```C++
enum BasicType {
    btNoType   = 0,
    btVoid     = 1,
    btChar     = 2,
    btWChar    = 3,
    btInt      = 6,
    btUInt     = 7,
    btFloat    = 8,
    btBCD      = 9,
    btBool     = 10,
    btLong     = 13,
    btULong    = 14,
    btCurrency = 25,
    btDate     = 26,
    btVariant  = 27,
    btComplex  = 28,
    btBit      = 29,
    btBSTR     = 30,
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>Elementi
btNoType non è specificato alcun tipo di base.

il tipo di base di btVoid è `void` .

il tipo di base di btChar è un `char` (tipo C/C++).

il tipo di base di btWChar è un carattere wide (Unicode) ( `WCHAR` ).

il tipo di base di btInt è `signed int` (tipo C/C++).

il tipo di base di btUInt è `unsigned int` (tipo C/C++).

il tipo di base di btFloat è un numero a virgola mobile ( `FLOAT` ).

il tipo di base di btBCD è un valore decimale con codifica binaria ( `BCD` ).

il tipo di base di btBool è un valore booleano ( `BOOL` ).

il tipo di base di btLong è un `long int` (tipo C/C++).

il tipo di base di btULong è un `unsigned long int` tipo (C/C++).

il tipo di base di btCurrency è Currency.

il tipo di base di btDate è date/time ( `DATE` ).

il tipo di base di btVariant è una struttura di tipo variabile ( `VARIANT` ).

il tipo di base di btComplex è un numero complesso.

il tipo di base di btBit è bit.

il tipo di base di btBSTR è una stringa di base o binaria ( `BSTR` ).

il tipo di base di btHresult è `HRESULT` .

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono restituiti dal metodo [IDiaSymbol:: get_BaseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
