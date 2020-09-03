---
title: CV_call_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: afab1aef58616bfa925fd9f37aacf195eb569c96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462141"
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
CV_CALL_NEAR_C specifica una convenzione di chiamata di funzione utilizzando un push vicino da destra a sinistra. La funzione chiamante Cancella lo stack.

CV_CALL_NEAR_FAST specifica una convenzione di chiamata di funzione utilizzando un push vicino da sinistra a destra con registri. La funzione chiamata utilizza la somma dei byte del parametro per cancellare lo stack.

CV_CALL_NEAR_STD specifica una convenzione di chiamata di funzione utilizzando una chiamata near standard (push da destra a sinistra).

CV_CALL_NEAR_SYS specifica una convenzione di chiamata di funzione utilizzando una chiamata di sistema near.

CV_CALL_THISCALL specifica una convenzione di chiamata di funzione utilizzando `this` Call ( `this` puntatore passato nel registro).

CV_CALL_CLRCALL specifica una convenzione di chiamata di funzione utilizzata da Common Language Runtime (CLR), nota anche come convenzione di chiamata del codice gestito.

## <a name="remarks"></a>Osservazioni
I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
