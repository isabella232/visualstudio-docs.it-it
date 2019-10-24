---
title: CV_call_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5deb59d4bbee06e505ba10bf1d4f08b1b06aa62d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745345"
---
# <a name="cv_call_e"></a>CV_call_e
Specifica la convenzione di chiamata per una funzione.

> [!NOTE]
> Solo i valori di enumerazione più comuni sono documentati qui. L'enumerazione complete è disponibile nel file di intestazione cvconst. h.

## <a name="syntax"></a>Sintassi

```C++
typedef enum CV_call_e {
    CV_CALL_NEAR_C    = 0x00,
    CV_CALL_NEAR_FAST = 0x04,
    CV_CALL_NEAR_STD  = 0x07,
    CV_CALL_NEAR_SYS  = 0x09,
    CV_CALL_THISCALL  = 0x0b,
    CV_CALL_CLRCALL   = 0x16
} CV_call_e;
```

## <a name="elements"></a>Elementi
CV_CALL_NEAR_C specifica una convenzione di chiamata di funzione che usa un push vicino da destra a sinistra. La funzione chiamante Cancella lo stack.

CV_CALL_NEAR_FAST specifica una convenzione di chiamata di funzione che usa un push vicino da sinistra a destra con registri. La funzione chiamata utilizza la somma dei byte del parametro per cancellare lo stack.

CV_CALL_NEAR_STD specifica una convenzione di chiamata di funzione che usa una chiamata near standard (push da destra a sinistra).

CV_CALL_NEAR_SYS specifica una convenzione di chiamata di funzione utilizzando una chiamata di sistema near.

CV_CALL_THISCALL specifica una convenzione di chiamata di funzione che usa `this` chiamata (`this` puntatore passato nel registro).

CV_CALL_CLRCALL specifica una convenzione di chiamata di funzione usata da Common Language Runtime (CLR), nota anche come convenzione di chiamata del codice gestito.

## <a name="remarks"></a>Note
I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
