---
title: BasicType | Microsoft Docs
description: Trovare informazioni di riferimento sull'enumerazione BasicType, che specifica il tipo di base di un simbolo nell'SDK Visual Studio di accesso all'interfaccia di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9c59e66b73767b5ee5c6787fe0155ad1a2345161
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630750"
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
btNoType Non è specificato alcun tipo di base.

btVoid Basic è un tipo `void` .

btChar Basic è un `char` tipo (tipo C/C++).

btWChar Basic è un carattere wide (Unicode) ( `WCHAR` ).

btInt Basic type è `signed int` (tipo C/C++).

btUInt Il tipo Basic è `unsigned int` (tipo C/C++).

btFloat Basic è un numero a virgola mobile ( `FLOAT` ).

btBCD Basic è un decimale in codice binario ( `BCD` ).

btBool Basic è un tipo booleano ( `BOOL` ).

btLong Basic è un `long int` tipo (tipo C/C++).

btULong Basic è un `unsigned long int` tipo (tipo C/C++).

btCurrency Basic type is currency.

btDate Il tipo Basic è data/ora ( `DATE` ).

btVariant Basic è una struttura di tipo variabile ( `VARIANT` ).

btComplex Basic è un numero complesso.

btBit Basic è un bit.

btBSTR Basic è una stringa di base o binaria ( `BSTR` ).

btHresult Il tipo Basic è `HRESULT` .

## <a name="remarks"></a>Commenti
I valori in questa enumerazione vengono restituiti dal [metodo IDiaSymbol::get_baseType.](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
